# Triangulum — Generative Art

> A seed-based generative system for triangle-arc compositions.  
> A reproducible catalogue of computational constellation studies.

---

## What is this?

**Triangulum** is a generative design system that takes the triangle as its fundamental unit. Seventeen triangle-arcs radiate from the centre at graduated diameters — their size, colour, and stroke weight drifting with position. Behind them, a 5×5 grid carries two counter-layers: white frost particles scattered like stars, and a set of glowing triangle-planets, each with its own haloed glow.

Every artwork in this catalogue is defined by a single numeric seed. The same seed always produces the identical composition — making each piece **traceable, reproducible, and licensable** across textile, print, and apparel applications.

Named for the small northern constellation, **Triangulum** reframes radiating geometry as a textile.

---

## Live

🌐 **[View the catalogue →](https://reyrove.github.io/Triangulum/)**

---

## The System

The generator combines three layers:

| Layer | Description |
|-------|-------------|
| **Triangle-arcs** | 17 triangles drawn at graduated diameters around a common centre — each arc is a stack of 32 thin triangles. |
| **Frost grid** | A 5×5 lattice of white triangle particles, scattered across the canvas. |
| **Planets** | A 5×5 grid of triangle-planets, each with a radial gradient fill and a concentric triangle glow. |

All three layers are driven by the same seed, ensuring deterministic output.

### Parameters

- **Grid** — 5 columns × 5 rows
- **Arcs** — 17 triangle-arcs, graduated from `16%` of canvas to nearly full width
- **Arc layers** — 32 triangles per arc, colour-lerped along the arc's length
- **Triangle-orb size** — `canvasSize / 40` to `canvasSize / 13`
- **Planet size** — `canvasSize / 16` to `canvasSize / 6.4`
- **Frost particle size** — `canvasSize / 200` to `canvasSize / 130`
- **Arc palette** — 5 tones, each randomised RGB
- **Star palette** — 5 tones, each randomised RGB
- **Planet palette** — 5 tones, each randomised RGBA

---

## Structure

```
Triangulum/
├── index.html              ← Full catalogue (single-file)
├── images/
│   ├── fav.svg
│   ├── triangulum-tote.png
│   ├── triangulum-cushion.png
│   └── ...
├── Triangulum.jpg          ← Apparel mockup
└── README.md
```

The entire project is contained in a single `index.html` — no build step, no framework. The only external dependency is **p5.js** (loaded from CDN), which drives the exact sketch pipeline.

---

## Features

- **Seed-based generation** — every composition is deterministic and reproducible
- **Live animation** — the plate runs continuously; the cover and framed plate auto-stop after 30 seconds
- **Live catalogue** — cover, statement, plate, surfaces, process, archive, commission sections
- **Multiple surfaces** — print, scarf, textile, wallpaper — all rendered from the same seed
- **Archive of 8 seeds** — click any plate to load it into the main view
- **PNG export** — download the current frame of the plate directly from the browser
- **Keyboard shortcuts** — `R` for new seed, `S` to save
- **Legal modal** — licensing, terms, and credits built in
- **Responsive** — works on desktop, tablet, and mobile
- **Mobile-first navbar** — horizontally scrollable with fade hint

---

## Usage

### Generate a new composition

Click **New Seed** or press `R`.

### Download the current frame

Click **Download** or press `S`.

### Load a seed from the archive

Click any plate in the **Archive** section.

---

## Color System

Every composition is drawn from four seeded palettes, each built at setup time:

| Palette | Size | Range |
|---------|------|-------|
| **Arc colours** | 5 tones | Bounded RGB, biased toward warm / bright mid-tones |
| **Star colours** | 5 tones | Bounded RGB, biased toward high contrast |
| **Planet colours** | 5 tones | Bounded RGBA with seeded alpha |
| **Background** | Per-frame drift | RGB noise, near-black, low alpha |

Each arc draws its colour from a pair of arc-palette entries, lerped across the 32 layers. Each planet draws from the planet palette based on its grid position (`(row + col) % 5`). Same for the triangle-orb grid, drawn from the star palette.

Because the palettes are all seeded, no two compositions share the same rhythm of colour.

---

## Technical Notes

- **p5.js** drives the composition. The triangle primitive, triangle-arc layering, and radial gradient fills all use p5's native functions.
- **Seeded randomness** for structural parameters uses a Lehmer LCG.
- **Live plate** — 30fps, continuously animating.
- **Cover and framed plate** — 20fps, freeze after 30 seconds of animation.
- **Frozen stills** — the four surface swatches and eight archive thumbnails run for a small number of frames (6 and 5 respectively), then freeze. Because the background drift is per-frame, this captures a representative moment.
- **Off-screen pause** — an `IntersectionObserver` calls `noLoop()` on live instances that scroll out of view.
- **`prefers-reduced-motion` respected.**

---

## About

**Triangulum** is a project by [Reyhaneh Daneshdoost](https://reyrove.github.io/) — an Iranian-born artist working at the intersection of classical textile logic and generative systems.

The work begins with a simple observation: the woven surface — repetitive, mathematically structured, infinitely variable — has always been a form of computation, long before computers.

**Triangulum** is an attempt to render that logic visible.

> *A triangle is the simplest closed form — and yet nothing closes cleanly.*

---

## Licensing

All compositions are seed-documented and available for licensing across textile, surface, and apparel applications.

For commercial use, custom editions, or exclusive rights:

📧 **reyhanehdaneshdoost@gmail.com**

See the **Licensing** section in the live catalogue for details.

---

## Links

- 🌐 [Website](https://reyrove.github.io/)
- 📷 [Instagram](https://www.instagram.com/rey._.rove/)
- 💼 [LinkedIn](https://www.linkedin.com/in/reyhaneh-daneshdoost-730481160/)
- 🐦 [X](https://x.com/reyrove)

---

## Credits

**Design & Generative System**  
Reyhaneh Daneshdoost

**Typefaces**  
Cormorant Garamond · DM Mono

**Edition**  
Triangulum — Autumn 2026

---

<p align="center">
  <em>Generative Triangle-Arc</em><br />
  <sub>© Reyrove Studio · All compositions reproducible by seed</sub>
</p>