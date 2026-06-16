# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A single-page personal landing site (plain HTML + CSS, no JavaScript, no build step). Deployed via GitHub Pages — pushes to `main` go live at https://chimichurriprod.github.io/churri-practice/.

## Running locally

No build, no server required. Open `index.html` directly in a browser, or run `python3 -m http.server` from the repo root and visit `http://localhost:8000`.

## Architecture

- `index.html` — semantic markup only. Four `<section>` blocks (Hero, About, Selected Work, Contact) each prefixed with a numbered `.label`. No inline styles.
- `style.css` — all visual styling. Organized top-to-bottom: design tokens → reset → base → layout → sections → responsive.

Two conventions to preserve when editing styles:

1. **Tokens in `:root`.** Colors, spacing, type scale, and font stacks are CSS custom properties. To re-skin the site, change the tokens — don't hardcode values in component rules.
2. **Fluid scaling via `clamp()`, not breakpoints.** Type sizes and paddings use `clamp(min, fluid, max)` so they scale smoothly with viewport width. The single `@media (min-width: 768px)` query exists only for the project grid's 1→3 column shift, which `clamp()` can't express. Prefer adding a new clamp before adding a new media query.
