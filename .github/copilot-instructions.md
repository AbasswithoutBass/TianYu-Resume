# Project Guidelines

## Overview

Personal portfolio/resume site deployed to GitHub Pages at `tianyu-resume.art`. Single `index.html` file containing all HTML, CSS (~5000 lines), and JavaScript (~1500 lines). No build tools, no package manager.

## Deployment

- Push to `main` → GitHub Actions automatically deploys to GitHub Pages
- Local preview: open `index.html` directly in a browser (no server needed)

## Architecture

**Single-file design** — all code lives in `index.html`:
- HTML structure defines animation modules (editor, terminal, preview, stage, mixing, music)
- CSS: 100+ `@keyframes`, responsive breakpoints (6 media queries), `will-change` / `contain` for perf
- JS: scroll-driven animation loop via `requestAnimationFrame` + `ease(t)` where `t ∈ [0,1]`

**Animation system**:
- `renderAll(t)` is the central dispatcher — all animated states derive from a single progress value
- Phases gate rendering: `Editor → Terminal → Preview`
- `Intersection Observer` triggers entrance animations for the vocal-stage section

## Conventions

- **No frameworks** — vanilla HTML/CSS/JS only; do not introduce npm, bundlers, or libraries
- **No file splits** — keep everything in `index.html` unless explicitly asked to extract files
- **Responsive**: maintain all 6 media query breakpoints when editing layout
- **Performance**: preserve `will-change`, `contain`, and `pointer-events` optimizations on animated elements
- **Assets**: `assets/` holds static images only
