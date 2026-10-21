# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Always Do First

**Invoke the `frontend-design` skill** before writing any frontend code, every session, no exceptions.

## Project Overview

Neuromatic is a single-page sales site (`index.html`) for an agency that builds AI systems (AI receptionist, admin automation, lead generation) for service businesses and industrial companies across the US and abroad. The page has one job: get an owner to book a free automation audit. Copy follows the "Neuromatic One Page Sales Copy Blueprint"; look and feel follows the "Neuromatic Brand" design system.

- Plain CSS with brand tokens on `:root` (no Tailwind, no build step)
- **Sora** for everything, self-hosted from `assets/fonts/` (the brand allows no second typeface)
- Colors: `black #0a0a0a` ground, white type, `lime #c8f560` only for the "Book a free audit" buttons and one key word or callout per section
- Logo: always the file `assets/logo/wordmark-on-dark.svg`, never typed; favicon `assets/logo/n-favicon.svg`
- No gradients, glows or em dashes; no hype words; never publish a number that can't be backed up (unknown facts stay as `[placeholders]` styled with `.fill`)

## Dev Server

Start the local server before taking any screenshots or previewing in browser:

```bash
node serve.mjs
# Serves project root at http://localhost:3000
```

Always serve from localhost — never screenshot a `file:///` URL. Do not start a second instance if already running.

## Screenshot Workflow

```bash
node screenshot.mjs http://localhost:3000
# Optional label: node screenshot.mjs http://localhost:3000 label
```

Screenshots auto-increment to `./temporary screenshots/screenshot-N.png` (or `screenshot-N-label.png`). After screenshotting, read the PNG with the Read tool to visually compare against reference. Do at least 2 comparison rounds before stopping.

Puppeteer is at `C:/Users/nateh/AppData/Local/Temp/puppeteer-test/`. Chrome cache at `C:/Users/nateh/.cache/puppeteer/`.

## Architecture

Everything lives in `index.html`. Sections in order: Header → Hero (with animated example call) → Problem (missed-call calculator) → Offer (Answer / Automate / Grow) → How it works → Proof (demo call + founder note) → Who it's for → Free audit → FAQ → Final CTA → Footer. All interactivity is vanilla JS at the bottom of the file.

Key conventions:
- Sticky black header with hairline bottom border; nav links collapse into a menu on phones while the CTA stays visible
- Primary button `.btn` (lime pill, black text); every booking button carries `data-book`. Set `BOOKING_URL` in the script to point them at the booking page; while empty they scroll to `#audit`
- Focus states: lime outline
- Breakpoints: 1024px (tablet) and 768px (mobile)

## Available Skills

- **`frontend-design`** (`FrontendDesign/FESKILL.md`) — Guides creation of distinctive, production-grade frontend interfaces. Invoked automatically for any frontend work.
- **`video-to-website`** (`VideoToWebsite/VideoToWebsite.md`) — Converts a video into a scroll-driven animated website using GSAP, Lenis smooth scroll, and canvas frame rendering.

## Frontend Rules (from FrontendCLAUDE.md)

- If a reference image is provided: match layout/spacing/typography/color exactly — do not improve or add to the design.
- Images: use `https://loremflickr.com/{w}/{h}/{keyword}?lock={n}` for content-specific photos (unique lock number per slot); `https://picsum.photos/seed/{word}/{w}/{h}` for atmospheric/hero backgrounds. Use `placehold.co` only when pixel-matching a reference.
- Check `brand_assets/` folder before designing — use any logos or color palettes found there.
- **Never** use `transition-all`
- **Never** use default Tailwind blue/indigo as primary color
- **Never** use the same font for headings and body
- Animate only `transform` and `opacity`
- Every clickable element needs hover, focus-visible, and active states
