# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Single-file static landing page for an investment strategy consultancy. Everything — HTML, CSS, and JavaScript — lives in `index.html`. There is no build step, bundler, package manager, or test suite.

## Running the site

Open directly in a browser:

```
start index.html          # Windows
open index.html           # macOS
xdg-open index.html       # Linux
```

No server is required. All assets are either inline or loaded from external CDNs (Google Fonts, Unsplash).

## Architecture

`index.html` is structured in this order:

1. `<head>` — meta/SEO tags, Google Fonts (`Inter` + `Playfair Display`), all CSS in a single `<style>` block
2. HTML sections (in DOM order): Nav → Hero → Why Choose Us → Investment Process → Testimonials → Lead Magnet → Enquiry Form → FAQ → Final CTA → Footer
3. A single `<script>` block at the bottom handling: sticky nav, hamburger menu, smooth scroll, IntersectionObserver scroll animations, FAQ accordion, and form validation

## CSS conventions

- All colours are CSS variables defined in `:root` — never hardcode hex values that duplicate a variable.
- Layout uses CSS Grid for multi-column sections and Flexbox for single-axis alignment.
- Responsive breakpoints: `768px` (tablet) and `480px` (mobile).
- Scroll-in animations use the `.animate` / `.animate.visible` pair — add the class to any new element that should fade in on scroll; the IntersectionObserver already targets `.animate`.

## Form

The enquiry form posts to `https://formsubmit.co/verwertung777@gmail.com`. Client-side validation (name, email regex, phone) runs before the native POST. To change the recipient, update the `action` attribute on `#enquiryForm`.

## External dependencies

| Resource | Purpose |
|---|---|
| `fonts.googleapis.com` | Inter + Playfair Display |
| `images.unsplash.com` | Hero background image |
| `formsubmit.co` | Form submission backend |

All other icons and visuals are inline SVG — no icon library is used.
