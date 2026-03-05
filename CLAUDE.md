# MARR Laser & Skin Clinic — Unified Project Repo

## Overview
All deliverables for MARR Laser & Skin Clinic: website, landing page, design directions, and project docs.

**GitHub Pages**: https://ajeibbotson-cmyk.github.io/marr-laser/
**Design Hub**: https://ajeibbotson-cmyk.github.io/marr-laser/designs/
**Layout Variants**: https://ajeibbotson-cmyk.github.io/marr-laser/website/variants/

## Repo Structure
```
marr-laser/
├── CLAUDE.md
├── .gitignore
├── index.html                ← project hub (links to all deliverables)
├── website/                  ← full multi-page website (Design C)
│   ├── index.html            ← homepage
│   ├── laser-hair-removal.html
│   ├── why-alexandrite.html
│   ├── skin-treatments.html
│   ├── anti-ageing.html
│   ├── aesthetics.html
│   ├── about.html
│   ├── gallery.html
│   ├── blog.html
│   ├── contact.html
│   ├── style-guide.html      ← internal reference
│   ├── styles.css
│   ├── images/               ← local placeholder images (28 files, shared across site/designs/landing)
│   └── variants/             ← Layout A/B/C alternatives for client review
│       ├── index.html         ← client review hub (preference selectors + Formsubmit)
│       ├── thank-you.html     ← form submission confirmation
│       ├── home-b.html
│       ├── laser-b.html
│       ├── alexandrite-b.html
│       ├── skin-b.html
│       ├── anti-ageing-b.html
│       ├── aesthetics-b.html
│       ├── about-b.html
│       ├── gallery-b.html
│       ├── blog-b.html
│       ├── contact-b.html
│       ├── home-c.html
│       ├── laser-c.html
│       ├── alexandrite-c.html
│       ├── skin-c.html
│       ├── anti-ageing-c.html
│       ├── aesthetics-c.html
│       ├── about-c.html
│       ├── gallery-c.html
│       ├── blog-c.html
│       └── contact-c.html
├── landing/                  ← laser hair removal landing page (Webflow embed)
│   ├── index.html
│   ├── styles.css
│   ├── client-asset-brief.md
│   └── sections/             ← 01-header.html through 14-footer-cta.html
├── designs/                  ← design directions for client review
│   ├── index.html            ← branded hub page (links to style guide)
│   ├── styles.css
│   ├── style-guide.html      ← component animation review for Ashley (buttons, cards, CTA, nav)
│   ├── design-a/
│   ├── design-b/
│   └── design-c/             ← chosen direction (Warm Boutique)
└── docs/                     ← brand guidelines, briefs, audits
    ├── MARR_Brand Guidelines.pdf
    ├── Marr_Asset_Request.docx
    ├── Marr_Website_Development_Plan.docx
    ├── Marr_Local_SEO_Audit.xlsx
    └── reference/
```

## Brand Tokens (Shared)
| Token | Value | Name |
|-------|-------|------|
| Primary | `#3C3C3B` | charcoal |
| Accent | `#C6BCB3` | taupe |
| Accent hover | `#B4A89D` | darker taupe |
| Background | `#ECE5E0` | blush |
| Light | `#F9F9F8` | offwhite |
| Heading font | Cangste / Cormorant Garamond | serif |
| Body font | Noto Sans | sans-serif |

```css
--marr-primary: #3C3C3B;
--marr-accent: #C6BCB3;
--marr-accent-hover: #B4A89D;
--marr-light: #ffffff;
--marr-bg: #F9F9F8;
--marr-text: #3C3C3B;
--marr-font-heading: 'Cangste', 'Cormorant Garamond', serif;
--marr-font-body: 'Noto Sans', sans-serif;
```

### Font Loading
```html
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@300;400;500;600&family=Noto+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">
```
Cangste is a custom font — Cormorant Garamond is the web fallback until webfont files are provided.

## Subdirectory Details

### `website/`
Full multi-page site styled with Design C (Warm Boutique). 10 pages covering all clinic services, plus a `variants/` directory containing Layout B and Layout C alternatives for each page (30 total variants). The client review hub at `variants/index.html` presents all 3 layouts per page with radio-button preference selectors, notes fields, and a Formsubmit.co submission form (sends to andrew@foxhue.com, CC ashley@foxhue.com). Form submits via AJAX (Formsubmit.co) and displays inline confirmation without leaving the page. JavaScript handles localStorage auto-save, live summary panel, and copy-to-clipboard fallback. CSS in `styles.css` uses Design C tokens throughout. All images use local files from `website/images/` (28 curated placeholders) with `loading="lazy"` on below-fold images.

### `landing/`
Single-page landing for laser hair removal — built as self-contained HTML/CSS blocks for Webflow custom code embeds. Each section in `sections/` has its own `<style>` block and can be pasted into Webflow independently. BEM naming with `marr-` prefix. Responsive breakpoints: 1200px, 991px, 767px, 478px. Images reference `../website/images/` (shared local files).

### `designs/`
Three design directions deployed to GitHub Pages for client review. Hub page at `designs/index.html` links to all three. Design pages reference `../website/images/` for shared local image assets.

| Direction | Name | Mood |
|-----------|------|------|
| A | Serene Spa | Calm clinical authority |
| B | Editorial Bold | Fashion editorial, oversized type |
| C | Warm Boutique | Welcoming, soft corners, approachable |

### `docs/`
Brand guidelines PDF, client briefs, SEO audit, development plan, and competitor reference material.

## Deployment
- **Branch**: `main` (GitHub Pages source)
- **Pages**: Enabled, serves from root of `main`
- **Workflow**: Use `/sc:deploy-designs marr --repo ajeibbotson-cmyk/marr-laser` to redeploy designs

## Architecture Notes
- Each design is self-contained: `index.html` + `styles.css`
- No JavaScript except the client review hub (`variants/index.html`) which uses inline JS for form handling and localStorage
- Website breakpoints: 992px, 767px, 477px
- Landing breakpoints: 1200px, 991px, 767px, 478px
- Images served from `website/images/` (local files, shared by website, designs, and landing pages)
- Google Fonts loaded via `<link>` in each HTML file
