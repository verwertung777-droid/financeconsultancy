---
name: frontend-design
description: Design and enhance professional frontend experiences with modern styling, premium typography, and a sophisticated blue color scheme optimized for finance and investment services websites.
---

# Frontend Design Skill - Professional Finance Theme

This skill guides design improvements for professional finance and investment websites with a focus on trust, sophistication, and user engagement.

## Color Palette - Professional Blue Theme

### Primary Brand Colors
- **Primary Blue**: `#0052CC` - Main brand color, used for primary actions and key UI elements
- **Deep Blue**: `#00264D` - Dark backgrounds, text on light backgrounds
- **Light Blue**: `#E3F2FD` - Subtle backgrounds, hover states
- **Accent Gold**: `#D4AF37` - Premium accents, highlights for important information
- **Success Green**: `#10B981` - Positive actions, confirmations
- **Neutral Dark**: `#1F2937` - Primary text
- **Neutral Light**: `#F3F4F6` - Light backgrounds

### CSS Variables Setup
```css
:root {
  --primary-blue: #0052CC;
  --deep-blue: #00264D;
  --light-blue: #E3F2FD;
  --accent-gold: #D4AF37;
  --success-green: #10B981;
  --text-primary: #1F2937;
  --text-secondary: #6B7280;
  --bg-light: #F3F4F6;
  --bg-white: #FFFFFF;
  --border-color: #E5E7EB;
  --shadow-sm: 0 1px 2px rgba(0, 0, 0, 0.05);
  --shadow-md: 0 4px 6px rgba(0, 0, 0, 0.07);
  --shadow-lg: 0 10px 15px rgba(0, 0, 0, 0.1);
  --shadow-xl: 0 20px 25px rgba(0, 82, 204, 0.1);
}
```

## Premium Typography

### Font Stack
- **Display Font**: `"Playfair Display"` (serif) - Headlines, hero text for elegance
- **Body Font**: `"Inter"` (sans-serif) - All body text, UI elements for clarity
- **Fallback**: System fonts for reliability

### Typography Scale
- **Hero Headline (h1)**: `clamp(2.5rem, 4vw, 3.5rem)` - Main page title, powerful presence
- **Section Heading (h2)**: `clamp(1.8rem, 3vw, 2.6rem)` - Section titles
- **Subsection Heading (h3)**: `clamp(1.3rem, 2.5vw, 1.8rem)` - Card titles, subheadings
- **Body Large**: `1.075rem` - Key information, intro text
- **Body Regular**: `1rem` - Standard body text
- **Body Small**: `0.875rem` - Labels, helper text
- **Label/Uppercase**: `0.7rem`, letter-spacing: `0.1em`, text-transform: uppercase

### Line Heights
- Headlines: `1.2` - tight spacing for impact
- Body text: `1.6` to `1.75` - readable and professional
- Lists: `1.8` - comfortable scanning

## Design Principles for Finance Websites

### 1. Trust & Authority
- Use high contrast between text and background
- Clear visual hierarchy with generous whitespace
- Professional imagery and icons
- Consistent branding throughout

### 2. Information Architecture
- Lead with benefits before features
- Clear section structure: Hero → Why Us → Services → Process → Social Proof → CTA
- Mobile-first responsive design
- Progressive disclosure (hide complexity, show on demand)

### 3. Call-to-Action (CTA) Optimization
- Primary CTAs in primary blue (#0052CC)
- Secondary CTAs in outline style
- CTAs should stand out but feel trustworthy (not pushy)
- Different CTAs for different stages of customer journey

### 4. Engagement Elements
- Smooth scrolling and fade-in animations
- Hover states on interactive elements
- Icons (SVG preferred) to break up text
- Testimonials and social proof sections
- FAQ sections with smooth accordion behavior

### 5. Responsive Design Breakpoints
- **Desktop**: 1024px and above - multi-column layouts
- **Tablet**: 768px to 1023px - optimized grid layouts
- **Mobile**: Below 768px - single column, touch-friendly spacing

## Implementation Guidelines

### Buttons & Interactive Elements
```
Primary Button:
- Background: var(--primary-blue)
- Text: white
- Padding: 0.875rem 1.75rem
- Border radius: 0.5rem
- Font weight: 600
- Transition: box-shadow 0.2s, transform 0.1s
- Hover: Darker blue (#003BA3), elevated shadow

Secondary Button:
- Background: transparent
- Border: 2px solid var(--primary-blue)
- Color: var(--primary-blue)
- Hover: Light blue background (#E3F2FD)

Ghost Button:
- Background: transparent
- Color: var(--text-secondary)
- Border: 1px solid var(--border-color)
- Hover: Light blue background
```

### Cards & Containers
- Background: white with subtle shadow
- Border radius: 0.75rem to 1rem
- Padding: 2rem to 2.5rem
- Subtle border: 1px solid var(--border-color)
- Hover effect: Slight elevation, border color change

### Section Spacing
- Large sections: 4rem to 5rem padding (vertical)
- Card gaps: 2rem to 2.5rem
- Internal padding: 1.5rem to 2rem
- Mobile adjustments: Reduce by 30-40%

### Visual Hierarchy with Color
- Use gold accent (#D4AF37) sparingly for premium features
- Use green for positive actions and success states
- Use primary blue for primary navigation and CTAs
- Keep most UI neutral (grays) to reduce visual noise

## Examples - Common Finance Website Sections

### Hero Section
- Full-width background with gradient overlay (deep blue to dark)
- Large hero headline in Playfair Display
- Supporting text in Inter, body-large size
- Prominent CTA button (primary blue)
- Optional: Hero image or video background

### Features/Benefits Section
- Grid layout (3 columns on desktop, 1 on mobile)
- Cards with icons (SVG)
- Short headline + brief description
- Optional icon accent in gold or light blue

### Testimonials Section
- Quote marks as visual accent in light blue or gold
- Client photo (optional)
- Client name + title + company
- Star rating if applicable
- Light background (F3F4F6 or E3F2FD)

### Process/Steps Section
- Timeline or numbered cards
- Clear progression visual
- Icons for each step
- Short descriptions
- Vertical layout on mobile

### CTA Section (Final)
- Contrast against white background (light blue #E3F2FD)
- Centered layout
- Large headline
- Supporting text
- Primary button(s)

## Engagement & Animation

- Fade-in animations on scroll (0.6s duration)
- Smooth transitions on hover (0.2s)
- Icon slide animations
- Subtle bounce effects on buttons (no more than 4px)

## Accessibility Considerations

- All text has sufficient contrast (WCAG AA minimum 4.5:1 for body, 3:1 for large text)
- Color is never the only way to convey information
- Interactive elements have clear focus states
- Form labels are clearly associated with inputs
- Mobile touches are at least 44px × 44px
