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

`screenshot.mjs` points at a Windows Puppeteer install. In cloud sessions use Playwright with `/opt/pw-browsers/chromium-1194/chrome-linux/chrome` instead.

```bash
node screenshot.mjs http://localhost:3000
# Optional label: node screenshot.mjs http://localhost:3000 label
```

Screenshots auto-increment to `./temporary screenshots/screenshot-N.png` (or `screenshot-N-label.png`). After screenshotting, read the PNG with the Read tool to visually compare against reference. Do at least 2 comparison rounds before stopping.

Puppeteer is at `C:/Users/nateh/AppData/Local/Temp/puppeteer-test/`. Chrome cache at `C:/Users/nateh/.cache/puppeteer/`.

## Architecture

Everything page-specific lives in `index.html`. It is built with the **scroll-craft** skill (brief and fingerprint in `scrollcraft/`). The page is one example working day: each scene is a time of day, in order. Hero (6:12 AM) → Problem + missed-call calculator (9:47 AM) → Offer rail, Answer / Automate / Grow (12:30 PM) → silent beat (1:58 PM) → Peak, "The business runs itself" (2:30 PM) → How it works (4:00 PM) → Proof: demo line + founder note (5:15 PM) → Who it's for (6:30 PM) → Free audit + FAQ (7:45 PM) → Close + footer (9:40 PM).

- `assets/js/scrollcraft.js` + `assets/css/scrollcraft.css`: the scroll engine (copied from the skill, never edited per project). Sections opt in with `data-sc-*` attributes (`data-sc-act`, `data-sc-cue`, `data-sc-in`, `data-sc-reveal`, `data-sc-parallax`, `data-sc-pan`).
- `assets/js/lenis.min.js`: smooth wheel scrolling (off under reduced motion).
- The day log (signature move) is vanilla JS at the bottom of `index.html`: every scene carries `data-scene="HH:MM"`, the header clock runs between scenes with scroll, and `LOG` entries stamp in when their time passes. All entries are illustrative and labeled "Example day".
- Photo planes for hero, problem, peak and close are commented blocks pointing at `assets/scenes/*.webp`. Uncomment once the file exists.

Key conventions:
- Fixed black header in two rows: brand row (logo, nav, CTA) and the day bar (clock, latest log line, clickable time ticks). Nav links collapse into a menu at 1024px; the CTA stays visible
- Primary button `.btn` (lime pill, black text), one label everywhere: "Book a free audit". Every booking button carries `data-book`; `BOOKING_URL` in the script points them at the booking page
- Scenes are labeled only by their time stamp (`.stamp`); no section numbers
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
