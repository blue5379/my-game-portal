# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A static game portal website (in Japanese) built with vanilla HTML/CSS/JavaScript — no build system or package manager. The portal showcases games created on Scratch, with a landing page (`index.html`) and a game detail page (`detail.html`).

## Running Locally

```bash
python -m http.server 8000
# or
npx serve
```

No build, lint, or test commands exist — the project is served directly as static files.

## Architecture

**Two-page static site:**
- `index.html` — Landing page with hero, featured pickup game, and filterable game grid
- `detail.html` — Game detail page for a specific game; includes screenshot carousel, feature highlights, a "Kiki" customization carousel, and a creature encyclopedia section

**All CSS is inline** inside `<style>` tags in each HTML file — there are no external stylesheets. All interactivity is vanilla JS at the bottom of each file.

**Design source:** `pencil-my-game-portal.pen` is the Pencil design tool file and the source of truth for visual design. Use the `pencil` MCP tools to read or modify it — never read it directly with file tools.

## Key Conventions

- Color accent: orange `#FF5C00`
- Fonts: Google Fonts — Instrument Serif, Inter, DM Mono
- CSS class naming mirrors component roles: `game-card`, `btn-primary`, `pickup-card`, `feature-card`, etc.
- Active/selected states use an `.active` class toggled via JS
- External game link: `https://scratch.mit.edu/projects/1191411435/`
- Game images live in `images/game/` (img01.png–img18.png)
