You are running the /updategit command. Follow every step below in order. If any step fails, stop immediately and report exactly what failed and why — do not skip ahead.

---

## Step 1 — Security scan (local files)

Before touching git, scan all project files for secrets and credentials. Use the Grep tool for each pattern below, searching the entire working directory but excluding `.git/`:

| What to find | Pattern |
|---|---|
| Hardcoded passwords | `(?i)(password\|passwd\|pwd)\s*[=:]\s*['"][^'"]{3,}['"]` |
| API keys / tokens | `(?i)(api[_-]?key\|api[_-]?token\|auth[_-]?token\|access[_-]?token\|secret[_-]?key)\s*[=:]\s*['"][^'"]{8,}['"]` |
| Private keys | `-----BEGIN (RSA \|EC \|DSA \|OPENSSH )?PRIVATE KEY` |
| AWS access keys | `AKIA[0-9A-Z]{16}` |
| Generic secrets | `(?i)secret\s*[=:]\s*['"][^'"]{6,}['"]` |
| Connection strings with creds | `(?i)(jdbc\|mongodb\|postgres\|mysql\|redis):\/\/[^:]+:[^@]+@` |

Also run this bash command to detect any `.env` files currently tracked by git:

```bash
git ls-files | grep -iE '\.env(\.|$)'
```

**If any pattern matches or any .env file is tracked: STOP. Report the finding (file name, line number, matched text). Do not proceed to Step 2.**

If the scan is clean, report "Security scan: PASSED" and continue.

---

## Step 2 — Verify .gitignore

Read `.gitignore`. If it does not exist or is missing any of these entries, create or update it:

```
.env
.env.*
.env.local
.env.production
*.pem
*.key
*.p12
*.pfx
*_rsa
*_dsa
*_ecdsa
*_ed25519
credentials.*
secrets.*
*.secret
.DS_Store
Thumbs.db
```

---

## Step 3 — Update README

Read `index.html` (first 80 lines is enough to check the title and section headings). Compare against `README.md`. If the page title, sections, or external dependencies have changed, update `README.md` to reflect the current state. Keep the existing structure — do not rewrite sections that are still accurate.

---

## Step 4 — Pre-commit file audit

Run `git status` and review every file that is new or modified. For each file ask: could this contain credentials, personal data, or private configuration? If yes — remove it from staging with `git rm --cached <file>` and note it for the user. Never blindly stage everything.

Files that are always safe to include in this project:
- `index.html`
- `README.md`
- `CLAUDE.md`
- `.gitignore`
- `.github/workflows/deploy.yml`
- `.claude/commands/*.md`

---

## Step 5 — Commit

Stage only the safe files identified in Step 4 by name (never `git add -A` or `git add .`). Write a clear, specific commit message that describes what actually changed. Format:

```
<short summary under 72 chars>

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>
```

---

## Step 6 — Push to GitHub

Run `git push origin main`.

The existing workflow at `.github/workflows/deploy.yml` runs a gitleaks secret scan **before** deploying — so the push triggers both the security gate and the Pages deployment automatically.

---

## Step 7 — Update repo about

Derive the repo's owner and name:

```bash
gh repo view --json nameWithOwner -q .nameWithOwner
```

Then run these two commands (substituting the real owner/repo):

```bash
# Set description and homepage
gh api repos/{owner}/{repo} -X PATCH \
  -f description="Professional investment strategy consultancy — static landing page deployed via GitHub Pages" \
  -f homepage="https://{owner}.github.io/{repo}/"

# Set topics
gh api repos/{owner}/{repo}/topics -X PUT \
  -f "names[]=investment" \
  -f "names[]=finance" \
  -f "names[]=landing-page" \
  -f "names[]=github-pages" \
  -f "names[]=static-site"
```

---

## Step 8 — Final report

Print a concise summary:

```
/updategit complete
─────────────────────────────────────
Security scan  : PASSED
Files committed: <list>
Push           : SUCCESS — commit <sha>
GitHub Pages   : https://<owner>.github.io/<repo>/
Repo about     : updated (description + homepage + topics)
─────────────────────────────────────
```

If GitHub Pages takes a minute to propagate, note that to the user.
