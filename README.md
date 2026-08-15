# The Shopping Envoy — Website

A single-page marketing site for **The Shopping Envoy**, a live-video personal shopping and concierge service that shops in-store on a client's behalf and ships purchases worldwide.

The design is built around a "travel dispatch" concept — boarding passes, wax seals, and passport stamps — to visually reinforce the idea of an envoy traveling into stores on your behalf.

## Live Demo

Open `index.html` directly in any browser, or deploy to a static host (see **Deployment** below).

## Project Structure

```
.
├── index.html              # The entire site (HTML + CSS + JS in one file)
└── assets/
    ├── logo-seal.png        # Circular compass/seal mark — used in nav & footer
    ├── logo-lockup.png       # Full horizontal logo (icon + wordmark)
    ├── favicon-16.png         # Browser tab icon
    ├── favicon-32.png         # Browser tab icon
    └── favicon-180.png       # Apple touch icon
```

**Both `index.html` and the `assets/` folder must be uploaded/committed together** — the page references images via relative paths (`assets/...`), so the images will 404 if the folder is missing.

## Tech Stack

- Plain HTML, CSS, and vanilla JavaScript — no build step, no framework, no dependencies to install
- Fonts loaded from Google Fonts: **Fraunces** (display serif), **Manrope** (body sans-serif), **IBM Plex Mono** (labels/utility text)
- QR codes generated client-side via [qrcodejs](https://github.com/davidshimjs/qrcodejs) (loaded from a CDN)
- Scroll animations via `IntersectionObserver`; respects `prefers-reduced-motion`

## Design System

| Token | Value | Use |
|---|---|---|
| `--bg` | `#F8F6F1` | Page background (porcelain ivory) |
| `--bg-alt` | `#F1ECE1` | Alternate section background |
| `--card` | `#FCFBF8` | Card backgrounds |
| `--ink` | `#1E2A38` | Primary text |
| `--ink-soft` | `#5B6572` | Secondary text |
| `--emerald` | `#2F5D50` | Primary accent |
| `--emerald-deep` | `#1F433A` | Dark sections, featured pricing card |
| `--gold` | `#B8935A` | Accent details, labels |

## Sections (in page order)

1. **Hero** — headline + animated boarding-pass visual
2. **`#route`** — "How it works," a 5-step itinerary timeline
3. **`#services`** — four services as ticket-stub cards
4. **`#trust`** — policy badges (final sale, shipping, customs, etc.)
5. Testimonials — "postcards" from clients
6. **`#pricing`** — three pricing tiers (per store, full-day, percentage plan)
7. **`#follow`** — social links + generated QR codes (WhatsApp, Instagram, TikTok)
8. **`#book`** — final call-to-action
9. Footer — logo, nav links, social icons

## Editing Content

All content lives directly in `index.html` — there's no CMS or data file. Search for the relevant section by its `id` (e.g. `id="pricing"`) and edit the text or values directly.

Common edits:
- **Pricing** — under `<section id="pricing">`, each `.price-card` has an `.amt` div with the price
- **Social links** — under `<section id="follow">` and in the `<footer>`, update the `href` values and the `makeQR(...)` calls near the bottom of the file (inside `<script>`) if a handle changes
- **WhatsApp booking link** — appears in the nav, hero, and final CTA; search for `wa.me` to find every instance

## Deployment (Vercel)

1. Make sure `index.html` sits at the **root** of your repository, with `assets/` alongside it (not nested in a subfolder).
2. Push to GitHub.
3. In Vercel: **Import Project → From Git Repository**, select the repo.
4. Set **Framework Preset** to `Other` (no build command needed).
5. If your files are inside a subfolder, set **Root Directory** in Project Settings → General to that folder.
6. Every subsequent push to your production branch auto-deploys.

## Browser Support

Modern evergreen browsers (Chrome, Safari, Firefox, Edge). Uses CSS custom properties, `backdrop-filter`, and `IntersectionObserver` — all widely supported, but the site will degrade gracefully (no blur/animation) on very old browsers.

## License

All rights reserved — content and design are proprietary to The Shopping Envoy.
