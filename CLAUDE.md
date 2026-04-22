# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Always Do First

**Invoke the `frontend-design` skill** before writing any frontend code, every session, no exceptions.

## Project Overview

Neuromatic is a single-page marketing website (`index.html`) for an AI performance coaching product. The site is built as a self-contained HTML file with:
- **Tailwind CSS** via CDN for utility classes
- **Custom accent color** `#f5b614` (yellow-gold), extended as `accent` in the Tailwind config
- **Inter** font from Google Fonts
- All styles inline — no separate CSS files, no build step

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

Everything lives in `index.html`. Sections in order: Nav → Hero → Plans → Features → About → FAQ → Footer. The FAQ accordion and all interactivity are implemented with vanilla JS at the bottom of the file.

Key design conventions in the current site:
- Black navbar (`#000`), fixed, with underline-slide nav-link hover effect
- Primary CTA buttons use `btn-primary` class (yellow `#f5b614` background, hover darkens to `#e0a612`)
- Outline buttons use `btn-outline` class
- Plan cards use `plan-card` with image zoom on hover
- Focus states: 2px `#f5b614` outline
- Mobile breakpoint at 768px via `@media` + utility classes like `.hidden-mobile`, `.hero-grid`, `.plans-grid`

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
