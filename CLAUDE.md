# Multicultural Night 2026 — CLAUDE.md

## Project Purpose
A static educational website about Newfoundland & Labrador, built for **Central Public School's Multicultural Night 2026**. Created by Robert and his daughter. Audience is K-8 school kids and their families — keep language friendly, engaging, and age-appropriate.

## Site Structure (5 pages)
| File | Content |
|------|---------|
| `index.html` | Homepage — province overview, stats, puffin video |
| `wildlife.html` | Moose, icebergs, whales, MSC Baltic III shipwreck |
| `culture.html` | Jellybean Row, kitchen parties, flag, snowballs recipe, root cellars |
| `saintpierre.html` | Saint-Pierre & Miquelon — French territory connection |
| `funfacts.html` | Folklore — giant squid, Old Hag, fairy circles, mummers |

## Design System
- **Framework**: Tailwind CSS via runtime `assets/tailwind.js` (no build step — styles generated in-browser)
- **Tailwind config is embedded inline in each HTML file** — changes to the palette/tokens must be made in every page
- **Color palette**:
  - Primary: `#006094` (ocean blue)
  - Secondary: `#3f661d` (forest green)
  - Tertiary: `#b71029` (deep red)
  - Surface/Background: `#fdf6e3` (cream)
  - On-surface: `#322f22` (dark brown)
- **Fonts**: Plus Jakarta Sans (headlines), Be Vietnam Pro (body) — loaded from `assets/fonts/`, fully local
- **Icons**: Material Symbols — loaded from `assets/fonts/`
- **Aesthetic**: Warm scrapbook feel — rotated cards (-3° to +2°), rounded corners (1–3rem), SVG noise texture overlay at 3% opacity

## Architecture
- **Pure static HTML** — no framework, no build pipeline, no server-side rendering
- **JS is minimal** — only inline `onclick` handlers for modal open/close; no libraries beyond Tailwind runtime
- **All assets are local** — fonts, images, videos all in `assets/` — no CDN or external dependencies at runtime
- **Modal pattern**: `document.getElementById('modal-id').classList.remove('hidden')` / `.add('hidden')`

## Assets
- `assets/images/` — 50+ images (jpg, webp, png)
- `assets/videos/` — 5 videos, all MP4, compressed to 720p CRF 30 for web: `puffins-video.mp4`, `kitchen-party.mp4`, `moose-size.mp4`, `giant-squid.mp4`, `msc-baltic.mp4`
- `assets/fonts/` — Google Fonts (WOFF2) + Material Symbols, all local
- `assets/tailwind.js` — 409KB compiled Tailwind runtime
- If adding new videos, compress with: `ffmpeg -i input.mp4 -vf "scale=-2:720" -vcodec libx264 -crf 30 -preset medium -acodec aac -b:a 96k output.mp4`
- GitHub hard limit is 100MB per file; keep videos well under that

## Hosting
- Hosted on GitHub Pages: **https://smearobe.github.io/multicultural-day-2026/**
- Repo: **https://github.com/smearobe/multicultural-day-2026**
- Temporary — take down after the school event by disabling Pages in repo settings or deleting the repo

## Important Context
- Robert was born in Newfoundland & Labrador — content reflects genuine personal connection
- Melinda (Robert's mother/relative) appears on the site as a personal touch
- MSC Baltic III shipwreck content is current as of early 2025 — a real ongoing event
- Site is intended to be hosted **temporarily** for the school event, then taken down
- No external URLs are needed or desired — everything should work offline/self-contained

## Navigation
All 5 pages share a consistent sticky nav header linking to each other. Active page is indicated in the nav.
