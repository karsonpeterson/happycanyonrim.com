# Happy Canyon Rim Website — Design Spec

## Overview

A single-page static website for Happy Canyon Rim, a family-owned ranch/homestead/historical site. The site showcases the property through photography, tells its story, and invites donations for landscape preservation. It will be hosted on GitHub Pages.

## Goals

- Showcase the property and its history through photos and text
- Communicate the preservation mission
- Provide a way for visitors to donate via Venmo
- Deliver a western/high-desert aesthetic that feels authentic, not kitschy
- Mobile-friendly, fast-loading, zero dependencies

## Technical Approach

- **Single `index.html` file** with embedded CSS (`<style>`) and vanilla JS (`<script>`)
- No build tools, no frameworks, no package manager
- Images served from a local `images/` directory (photos copied from `happy_canyon_rim_photos/`)
- Hosted on **GitHub Pages** from the `main` branch
- Google Fonts loaded via `<link>` for typography

## Page Sections (top to bottom)

### 1. Hero

- Full-width background image (the cabin/house photo)
- "Happy Canyon Rim" as large display heading, centered
- Placeholder tagline beneath (e.g., "A piece of the American West, preserved.")
- Subtle dark overlay on the image so white text is legible
- CSS `background-attachment: fixed` for a parallax-like feel on desktop; falls back to scroll on mobile

### 2. About / History

- Heading: "Our Story" (or similar)
- Placeholder paragraph text about the property, the family's connection, and its significance
- Clean, readable layout — max-width container, generous line height
- Optional: one inline photo to break up text

### 3. Gallery

- Heading: "The Land"
- CSS Grid layout: 3 columns on desktop, 2 on tablet, 1 on mobile
- All 5 photos displayed as cards with subtle hover effect (slight scale + shadow)
- Click opens a **lightbox overlay** (vanilla JS):
  - Dark backdrop
  - Full-size image centered
  - Left/right arrow navigation
  - Close on click outside, Escape key, or X button
  - Touch-friendly tap targets
- Easy to extend: just add more `<img>` tags to the grid

### 4. Preservation / Donate

- Heading: "Help Preserve Happy Canyon Rim"
- Placeholder text about what the donations support
- Venmo section: placeholder for a QR code image and/or a direct Venmo link styled as a button
- Button styled in the site's accent color (terracotta red)

### 5. Footer

- Simple, understated
- Placeholder for contact email or other info
- Location placeholder (general area, not exact address)
- Copyright line

## Visual Design

### Color Palette

| Role        | Color     | Usage                                |
|-------------|-----------|--------------------------------------|
| Background  | `#FAF3E8` | Warm parchment/off-white             |
| Text        | `#2C1810` | Deep brown, almost black             |
| Accent      | `#C2452D` | Terracotta/desert red — buttons, highlights |
| Secondary   | `#8B6914` | Warm gold/ochre — subtle accents     |
| Muted       | `#A0927B` | Weathered wood gray-brown — borders, dividers |

### Typography

- **Headings:** Playfair Display (serif) — classic, western-compatible display font
- **Body:** Lato or Source Sans Pro (sans-serif) — clean and readable
- Both loaded from Google Fonts

### Section Dividers

- Subtle decorative horizontal rules between sections using CSS (a simple line with a small diamond or dot ornament in the center, done with pseudo-elements)

### Spacing

- Generous padding between sections (80-120px vertical)
- Content max-width of ~900px, centered
- Gallery grid with consistent gaps

## Responsive Behavior

| Breakpoint   | Behavior                                      |
|--------------|-----------------------------------------------|
| > 900px      | Full desktop layout, 3-column gallery         |
| 600-900px    | Tablet layout, 2-column gallery               |
| < 600px      | Mobile layout, single-column gallery, smaller hero text |

- All done with CSS media queries
- No horizontal scroll at any size
- Touch-friendly lightbox controls (large tap targets, swipe not required but arrows work)

## File Structure

```
happycanyonrim.com/
  index.html          # The entire site
  images/             # Optimized photos
    house.jpeg
    fence_gate.jpeg
    chicken_coop.jpeg
    wood_etch_fence.jpeg
    gate_latch.jpeg
    venmo-qr.png      # Placeholder for Venmo QR code (to be added later)
  docs/               # Design docs (not deployed)
```

## Deployment

- GitHub Pages, served from the root of the `main` branch
- No build step — push and it's live
- Custom domain `happycanyonrim.com` can be configured via GitHub Pages CNAME file when ready

## Out of Scope

- CMS or admin panel (owner will request changes through family)
- Analytics (can be added later with a single script tag if wanted)
- Blog or multi-page structure
- E-commerce or booking
- Server-side logic of any kind
