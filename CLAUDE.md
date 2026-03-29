# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This repo contains standalone single-file HTML apps — no build system, no package manager, no dependencies. Each file is self-contained with inline CSS and JavaScript.

**Apps:**
- `tictactoe.html` — Two-player Tic Tac Toe with score tracking. Pure vanilla JS, no libraries.
- `distance-calculator.html` — Interactive canvas-based distance calculator. Accepts image upload (drag-and-drop or file browse), renders it on a `<canvas>`, and lets users place/measure points on the image.

## Running the Apps

Open any `.html` file directly in a browser — no server required. For features that need a local server (e.g., if file-protocol restrictions arise), use:

```bash
npx serve .
# or
python -m http.server 8080
```

## Git Workflow

After every meaningful change, commit and push to GitHub so work is never lost:

```bash
git add <files>
git commit -m "short, descriptive message"
git push origin master
```

Keep commit messages clear and specific (e.g. `"add win highlight animation to tictactoe"` not `"update files"`). Commit logical units of work — don't batch unrelated changes into one commit.

## Versioning Rule

Every significant edit to an existing app must be saved as a **new versioned file** (e.g. `distance-calculator-v2.html` → `distance-calculator-v3.html`) and committed + pushed to GitHub. Never overwrite the previous version with big changes. Small fixes (typos, model name swap, single-line patches) may be applied in place, but any feature addition, redesign, or multi-area change warrants a new version.

## Architecture Notes

Both apps follow the same pattern:
- All styles in a `<style>` block in `<head>`
- All logic in a `<script>` block at the end of `<body>`
- No external dependencies or CDN imports

`distance-calculator.html` is significantly larger and uses:
- A `<canvas>` element for rendering the background image and overlaid measurement points/lines
- CSS custom properties (`--bg`, `--accent`, etc.) for theming
- Floating draggable panels for the UI (results, scale calibration)
- Mouse/touch event handling on the canvas for point placement
