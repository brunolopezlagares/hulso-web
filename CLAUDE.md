# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Minimalist landing page for **hulso.es** — a single `index.html` with 3D text "HULSO" rendered via Three.js, deployed on GitHub Pages.

## Architecture

- **Single file**: Everything lives in `index.html` (HTML + CSS + inline JS module)
- **Three.js** loaded from CDN via import map (`unpkg.com/three@0.170.0`)
- **No build tools**, no npm, no bundler — pure static site
- **CNAME** file maps to `hulso.es` custom domain

### Key features in `index.html`:
- 3D text geometry (`TextGeometry` + `FontLoader` from Three.js addons)
- `MeshStandardMaterial` with metallic finish, tuned differently for dark/light mode
- Chromatic aberration glitch effect (red/cyan ghost meshes that offset periodically)
- Mouse parallax + subtle idle rotation via lerped `textGroup.rotation`
- Entrance animation (scale from 0 + opacity fade, ease-out cubic)
- `prefers-color-scheme` detection for dark/light mode (CSS vars + JS)
- Responsive camera distance (`camera.position.z` adjusts for `aspect < 1`)
- WebGL fallback: CSS-only text if `getContext('webgl')` fails

## Development

```bash
# Serve locally (any static server works)
python3 -m http.server 8765

# Then open http://localhost:8765
```

## Deployment

Hosted on GitHub Pages from the `main` branch root.

```bash
# Push to deploy (GitHub Pages auto-builds from main)
git push origin main
```

DNS for `hulso.es` points to GitHub Pages IPs (A records) with `www` CNAME to `brunolopezlagares.github.io`.

## Language

Communicate in Spanish (castellano) with the user.
