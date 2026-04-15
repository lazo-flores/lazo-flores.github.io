# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal portfolio website for Jose Lazo-Flores, Ph.D. — deployed to GitHub Pages at `www.joselazoflores.com`. Built on the Tessellate template (HTML5 UP) with jQuery, Font Awesome, and Google Fonts.

## Local Development

```bash
python3 -m http.server 8000
# Visit http://localhost:8000
```

No build pipeline or package manager. SASS files in `assets/sass/` are pre-compiled to `assets/css/main.css`. Deployment is automatic on push to `main`.

## Architecture

**Single-page site** — everything lives in `index.html` (~908 lines). Sections are navigated via anchor links (`#header`, `#about`, `#experience`, `#projects`, `#contact`) with smooth scrolling (jQuery + scrolly plugin).

**Two styling layers:**
- Inline `<style>` block in `index.html` (lines ~14–326) — custom nav bar, header background, project cards, badges, AI Twin widget, responsive overrides. This is substantial (~300 lines) and where most custom styling lives.
- `assets/css/main.css` — base Tessellate template styles (generated from `assets/sass/`). Do not edit `main.css` directly; it's compiled output.

**Key accent color:** `#f5a623` (gold/orange), used throughout nav, badges, and buttons.

**External integrations:**
- AI Twin chat widget via `augself.ai/widget.js` (floating widget, loaded at bottom of `index.html`)
- HuggingFace Spaces iframes for project demos
- Clicky analytics (`data-id="101496361"`)

## Content Updates

- **Text content source:** `WebsiteIntroInfo.txt` has the raw copy; actual rendered content is in `index.html`
- **CV/Resume:** Replace PDFs in `documents/`
- **Images:** Replace files in `images/`
- **Projects section:** Lines ~520–691 in `index.html` (6 projects with badges, demo/code buttons)
- **Custom domain:** Configured in `CNAME`

## Responsive Breakpoints

Defined in `assets/sass/libs/_vars.scss`: wide (1681px), normal (1281px), narrow (1001px/737px), mobile (736px). Project images resize to 250px on mobile.
