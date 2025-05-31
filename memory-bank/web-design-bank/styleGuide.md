# TarotLyfe Digital Style Guide

## 1. Typography System

### Font Families

**Primary Display Font:** Cinzel (Serif, used for titles and branding)

**Secondary Display Font:** Marcellus (Serif, poetic accents and subheadings)

**Body Font:** Inter (Sans-serif, highly legible for UI and journaling)

### Font Scale

Heading 1 (H1): 2.25rem / 36px

Heading 2 (H2): 1.75rem / 28px

Heading 3 (H3): 1.5rem / 24px

Body Large: 1.125rem / 18px

Body Base: 1rem / 16px

Caption: 0.875rem / 14px

### Line Heights

Headings: 1.2–1.3

Body Text: 1.5

Journal Text: 1.6 (for improved readability during reflection)

## 2. Color Tokens

### Primary Palette

Primary Indigo: #1E1E2F (backgrounds, spiritual base)

Primary Lavender: #BFAAE3 (text accents, brand elements)

Primary Gold Ochre: #F5C77E (CTA, highlight color)

### Secondary Palette

Moonstone Gray: #2F2F3D (containers, panels)

Rose Quartz: #EAB7B7 (emotion/mood indicators)

Cloud White: #F8F8F8 (backgrounds for light mode)

### Contrast & Guidance

Text contrast must meet WCAG AA: 4.5:1 for body, 3:1 for large text

Avoid using accent colors (e.g., gold ochre or rose quartz) on light backgrounds without dark text overlays

## 3. Spacing System

### Base Unit

4px base unit using rem equivalents

### Scale (Rem)

XS: 0.25rem (4px)

SM: 0.5rem (8px)

MD: 1rem (16px)

LG: 1.5rem (24px)

XL: 2rem (32px)

2XL: 3rem (48px)

### CSS Variables (Example)

:root {
  --space-xs: 0.25rem;
  --space-sm: 0.5rem;
  --space-md: 1rem;
  --space-lg: 1.5rem;
  --space-xl: 2rem;
  --space-2xl: 3rem;
}

== 4. Accessibility Notes

=== WCAG Compliance

Target WCAG 2.1 AA compliance minimum

Maintain text contrast ratio of at least 4.5:1

Ensure focus outlines on interactive elements

Use semantic HTML for screen reader compatibility

=== Responsive Text

Use clamp() or calc() to scale headings for devices

h1 {
  font-size: clamp(1.75rem, 2.5vw, 2.25rem);
}

## Interaction Feedback

Provide visible hover/focus states for all inputs/buttons

Avoid color-only indicators — use icons, borders, or text changes for state changes

