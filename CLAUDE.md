# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal portfolio website for Jose Lazo-Flores, Ph.D. — AI Solutions Consultant & Data Scientist, based in Zurich. Deployed to GitHub Pages at `www.joselazoflores.com`. Built on the Tessellate template (HTML5 UP) with jQuery, Font Awesome, and Google Fonts.

## Local Development

```bash
python3 -m http.server 8001
# Visit http://localhost:8001
```

Port 8001 — **not** 8000. Jose's Swing Trader platform runs on 8000.

No build pipeline or package manager. SASS files in `assets/sass/` are pre-compiled to `assets/css/main.css`. Deployment is automatic on push to `main`.

## Architecture

**Two pages, hybrid model:**
- `index.html` (~1773 lines) — single-page home with anchor sections: `#header`, `#about`, `#experience`, `#platforms`, `#projects`, `#methodology`, `#insights`, `#contact`. Smooth scrolling via jQuery + scrolly plugin.
- `consulting.html` (~822 lines) — dedicated consulting page with sections: `#page-hero`, `#consulting-services`, `#consulting-audit`, `#consulting-methodology`, `#consulting-why`, `#consulting-presence`, `#consulting-cta`.

**Two styling layers:**
- Inline `<style>` block in each HTML file (`index.html` lines ~14–935; `consulting.html` lines ~14–630) — custom nav, hero, brand-coloured sections, card patterns, responsive overrides. This is where most custom styling lives.
- `assets/css/main.css` — Tessellate template styles (compiled from `assets/sass/`). **Do not edit `main.css` directly** — it's compiled output. Template-imposed rules to be aware of:
  - `p { text-align: justify }` at line 214 (overridden site-wide in each inline block)
  - `.main > .content { padding: 6em 0 }` at line 2240 (overridden per-section)
  - Gradients on `.content.style1/.style2/.style3` (overridden to white for content sections)

**Brand palette (CSS variables in each inline `<style>`):**
- `--accent-primary: #0F766E` (teal) — headings, buttons, accent borders, links
- `--accent-primary-hover: #0b5e58`
- `--accent-secondary: #1E40AF` (indigo) — secondary accents (e.g. "Worth Exploring" quadrant)
- Navy `#0f172a` — showcase sections (Platforms, Contact, hero overlays)
- Heading on light `#1f2937`; body on light `#4b5563`; body on dark `#d1d5db`

**Visual rhythm:** dark hero → white content → navy showcase (Platforms) → white content → navy CTA (Contact) → light-gray footer. Same logic on consulting page.

**Card pattern (site-wide convention):** any card-shaped element uses
```
background: #fff; border: 1px solid #e5e7eb; border-radius: 10px;
padding: 1.6em–1.8em 1.4em–1.5em;
box-shadow: 0 4px 12px rgba(0,0,0,0.08);
transition: box-shadow .2s, transform .2s;
:hover { box-shadow: 0 8px 24px rgba(0,0,0,0.08); transform: translateY(-2px); }
```
Used by `.service-card`, `.platform-card`, `.quadrant` (Opportunity Map), and friends. Color-coded top borders (`border-top: 4px solid <color>`) where priority signalling matters. Stay with this pattern when adding new cards.

**External integrations:**
- AI Twin chat widget via `augself.ai/widget.js` (floating, loaded at bottom of each page)
- HuggingFace Spaces iframes for project demos
- Calendly inline widget on `consulting.html#consulting-cta`; Calendly link buttons elsewhere
- Clicky analytics (`data-id="101496361"`)

**Hardcoded URLs:**
- Calendly: `https://calendly.com/jose-lazo-flores-1/ai-consulting-discovery-call`
- Upwork: long URL ending `...?ref=project_share` (see "Also available on" section of consulting.html)
- Malt: `https://en.malt.ch/profile/joselazoflores`

## Content Updates

- **Text content source:** `WebsiteIntroInfo.txt` has raw copy notes; rendered content lives in `index.html` / `consulting.html`.
- **CV/Resume:** Replace PDFs in `documents/`
- **Images:** Replace files in `images/`
- **Section line numbers in `index.html` (current — verify after major edits):**
  - Inline `<style>`: 14–935
  - Hero: 957–978
  - About: 979–1066
  - Experience: 1067–1151
  - Platforms: 1152–1263 (Augself, EnableMate, Swing Trader, Workshop)
  - Projects: 1264–1436 (6 project cards)
  - Methodology: 1437–1683 (5 P's, AI Sweet Spot, AI Opportunity Map)
  - Insights: 1684–1717 (three "Coming Soon" cards)
  - Contact: 1718–1741
  - Footer: 1742+
- **Pricing locale: CHF (Swiss francs)** — not EUR. All pricing strings on `consulting.html`. If you see `€` or `&euro;` anywhere, that's a regression.
- **Custom domain:** Configured in `CNAME`

## Responsive Breakpoints

Defined in `assets/sass/libs/_vars.scss`: wide (1681px), normal (1281px), narrow (1001px/737px), mobile (736px). Project images resize to 250px on mobile.

## Custom Slash Commands

Available in `.claude/commands/`:
- `/add-project` — add a new card to the AI Agent Projects section
- `/add-platform` — add a new card to the AI Platforms & Ventures section (optionally adds an Experience entry)
- `/update-content` — general content updates with branch-review-merge workflow
- `/preview` — start the local dev server (port 8001) for browser review
- `/screenshot` — capture fullpage screenshots (home and/or consulting) into `~/Documents/website-review/`
- `/deploy` — commit, merge to main, and push to GitHub Pages

## Workflow

All changes follow the branch-review-merge pattern: create a `feature/<description>` branch, make changes, preview locally with `python3 -m http.server 8001` (and a fullpage screenshot if visual), get Jose's approval, then merge to `main` and push.
