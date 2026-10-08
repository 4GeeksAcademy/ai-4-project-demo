# Zine Portfolio — Plan & Decision Log

## Overview

A single-page static HTML+CSS site for fictional artist **Marlowe Reeves**.
Designed as a DIY photocopied zine with intentional imperfections and
translucent neon highlighter accents.

**No JavaScript.** Semantic HTML5 with a separate CSS stylesheet.

---

## File Structure

```
/workspaces/ai-4-project-demo/
├── index.html      ← Semantic HTML5 (all content)
├── styles.css      ← All styling (no JS)
├── PLAN.md         ← This file
├── server.py       ← Flask dev server (provided by template)
└── ...
```

---

## Page Sections

| #   | Section            | HTML Element            | Content                                                            |
| --- | ------------------ | ----------------------- | ------------------------------------------------------------------ |
| 1   | **Masthead**       | `<header>`              | Zine title "MARLOWE REEVES", issue #, tagline, decorative staples  |
| 2   | **About Me**       | `<section id="about">`  | Bio card, photocopied photo placeholder, handwritten quote         |
| 3   | **Career / Works** | `<section id="career">` | 4 timeline cards (exhibitions, residencies, commissions)           |
| 4   | **Upcoming Shows** | `<section id="shows">`  | 4 future event entries with checkbox decorations, torn-note footer |
| 5   | **Footer**         | `<footer>`              | Social links, colophon, decorative staples                         |

---

## Design System

### Color Palette

| Role        | Color        | Value                     | Usage                |
| ----------- | ------------ | ------------------------- | -------------------- |
| Paper       | Off-white    | `#F5F0E8`                 | Page background      |
| Ink         | Almost-black | `#1A1A1A`                 | Body text, borders   |
| Highlighter | Neon Yellow  | `rgba(255, 255, 0, 0.35)` | Primary highlights   |
| Highlighter | Neon Pink    | `rgba(255, 0, 128, 0.25)` | Accent highlights    |
| Highlighter | Neon Green   | `rgba(0, 255, 128, 0.22)` | Secondary highlights |
| Highlighter | Neon Blue    | `rgba(0, 128, 255, 0.22)` | Links, tertiary      |

### Typography

| Role            | Font                           | Fallback               |
| --------------- | ------------------------------ | ---------------------- |
| Body / all text | **Cutive Mono** (Google Fonts) | Courier New, monospace |

No separate handwritten font — unified monospace throughout.

### Key CSS Techniques

- **Photocopied paper grain** — layered `radial-gradient` speckles on body background
- **Misregistration shadow** — `body::before` with inset box-shadows
- **Highlighter effect** — `linear-gradient` spans at oblique angles (`.hl-yellow`, `.hl-pink`, etc.)
- **Selection color** — global `::selection` in neon yellow
- **Intentional tilt** — `.tilt-left` / `.tilt-right` classes using `transform: rotate(±0.8–1.7deg)`
- **Wavy underlines** — `text-decoration: underline wavy` on key words
- **Collage cards** — offset `box-shadow`, mixed `border-style` (dashed, double, dotted)
- **Staple decorations** — `::before` pseudo-elements on rotated `<span>` elements
- **Torn paper edge** — `::before`/`::after` pseudo-elements with dashed repeating gradients
- **Responsive** — mobile breakpoint at 600px

---

## Decision Log

| Date       | Decision                                         | Rationale                                                              |
| ---------- | ------------------------------------------------ | ---------------------------------------------------------------------- |
| 2026-10-08 | Chose **b&w photocopy** aesthetic                | Aligns with zine/concept                                               |
| 2026-10-08 | Added **neon highlighter** accents               | Requested by user — translucent yellow, pink, green, blue              |
| 2026-10-08 | Chose **Cutive Mono** + **Just Another Hand**    | Typewriter body + handwriting accent                                   |
| 2026-10-08 | Removed **Just Another Hand** font               | User disliked handwritten look; unified to Cutive Mono throughout      |
| 2026-10-08 | `.handwritten` class repurposed                  | Now renders as uppercase monospace with subtle tilt (no separate font) |
| 2026-10-08 | Replaced CSS `@import` with HTML `<link>`        | Better performance, fewer render-blocking requests                     |
| 2026-10-08 | Added `::-moz-selection` / `::-webkit-selection` | Cross-browser selection highlight support                              |

---

## Development

```bash
# Start dev server
python3 server.py
# → http://localhost:3000
```

The Flask server serves static files from the project root.
Changes to `index.html` or `styles.css` are reflected on refresh
(no restart needed in debug mode).
