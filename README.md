# ⬡ SVG 2 STL Converter

A free, client-side web tool that turns **SVG vectors** or **typed text** into a **3D-printable STL** file. Drop in a logo, icon, or outlined shape — or just type some words — adjust the depth, and download a mesh ready for your slicer — all in your browser, nothing uploaded.

> Live demo: https://shanzy39.github.io/SVG-2-STL-Converter/

## Features

- **Two input modes** — convert an **SVG** vector, or extrude **typed text**
- **Drag & drop, browse, or paste** SVG markup
- **Text mode** with a choice of fonts (Helvetiker, Optimer, Gentilis — regular & bold)
- **Live 3D preview** you can rotate, pan, and zoom
- **Extrude** flat shapes to any depth
- **Scale** to a target size in millimeters
- **Optional bevel** for rounded edges
- **Optional base plate** — great for keychains, signs, and badges that need a flat backing
- **Binary STL export** (compact, slicer-friendly)
- **100% client-side** — no upload, no server, no tracking

## How it works

1. Shapes are collected from the input — **SVG mode** parses paths with Three.js `SVGLoader`, **Text mode** generates glyph shapes with `FontLoader`
2. Each shape is extruded into 3D with `ExtrudeGeometry`
3. The model is scaled, centered, and rested flat on the print bed
4. `STLExporter` writes a standard binary `.stl` file you can download

## What works best

| Works great | Won't extrude |
|---|---|
| Solid filled shapes (logos, icons) | Embedded raster images |
| Text converted to outlines/paths | Live `<text>` elements |
| Closed paths | Open strokes with no fill |
| Single or multi-part silhouettes | Gradients / filters |

Classic use cases: **keychains, cookie cutters, stencils, signs, name tags, logo badges.**

## Run locally

No build step. Open `index.html` in a browser, or serve the folder:

```bash
# Option 1: open directly
open index.html

# Option 2: serve (recommended for ESM imports)
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploy to GitHub Pages

1. Push this repo to GitHub
2. **Settings → Pages**
3. Source: **Deploy from a branch**, branch `main`, folder `/ (root)`
4. Save — your site goes live at `https://<your-username>.github.io/SVG-2-STL-Converter/`

## Built with

- [three.js](https://threejs.org) — `SVGLoader`, `FontLoader`, `ExtrudeGeometry`, `STLExporter`, `OrbitControls` (loaded via [esm.sh](https://esm.sh))
- No frameworks, no build tools, single HTML file

## Companion projects

- [Lightning-Decoder](https://github.com/shanzy39/Lightning-Decoder) — inspect LNURL, Lightning Address, and BOLT11 strings
- [USD-To-Sats-Chrome-Extension](https://github.com/shanzy39/USD-To-Sats-Chrome-Extension) — right-click any USD amount to convert to sats
- [BTCLN-QR-Generator](https://github.com/shanzy39/BTCLN-QR-Generator) — Flipper Zero app to generate Bitcoin and Lightning QR codes

## License

MIT
