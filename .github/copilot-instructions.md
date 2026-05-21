# Copilot instructions for this repository

## Build, test, and lint

This repository currently has **no configured build, lint, or automated test commands**. There is no `package.json`, test runner, or lint configuration in the repo.

To run the app locally, serve the repository root over HTTP and open the page in a browser:

```bash
python -m http.server 8080
```

Then open `http://localhost:8080`.

## High-level architecture

- The app is a **single-file static prototype** implemented entirely in `index.html`. HTML structure, CSS, and all JavaScript live together in that file.
- Rendering is handled in-browser with **Three.js loaded from CDNs** via an `importmap`; `OrbitControls` comes from `three/addons`, and the control panel uses `lil-gui` from jsDelivr.
- The viewport layout is a two-panel page: a left sidebar for front/back image uploads and a main `#viewport` container for the WebGL canvas.
- The sheet is rendered as **two meshes sharing one `PlaneGeometry`**: one mesh uses a front-side material, the other a back-side material. This is how the demo supports different textures on each face.
- The flex effect is procedural, not physics-based. The animation loop rewrites the geometry's Z positions every frame using the original vertex positions stored in `basePositions`, then recomputes normals for lighting.
- Lighting is interactive: ambient and directional light settings are mirrored into an `options` object and exposed through `lil-gui`. Resize handling keeps the camera aspect ratio and renderer size in sync with `#viewport`.

## Key conventions

- Keep changes aligned with the current **no-build static demo** approach unless the task explicitly asks for a larger restructure or tooling setup.
- Prefer the existing **CDN ESM import** pattern over adding local dependency management. If you change library versions, update the `importmap` and any direct CDN imports together.
- Preserve the **shared geometry + separate front/back materials** pattern for per-face texturing. Do not collapse this to a single material if the front/back image distinction must remain.
- File uploads currently replace `frontMaterial.map` and `backMaterial.map` independently using `FileReader` + `Image` + `THREE.Texture`. Follow that flow when extending texture upload behavior.
- The README is meant to describe the current implementation, while `PROJECT_PLAN.md` holds recommendations and future-work ideas.
