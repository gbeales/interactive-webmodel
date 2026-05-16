# interactive-webmodel

A standalone WebGL demo page with an integrated 3D viewport that renders a flexible rectangular sheet. You can orbit around the mesh, upload different front/back images, and tweak lighting in real time.

## Framework recommendation

**Use Three.js** for this project. It provides the fastest path to a browser-based prototype with mesh deformation, texture mapping, camera controls, and lighting widgets.

Alternatives worth considering as the project grows:
- **Babylon.js** (strong editor + PBR workflow)
- **PlayCanvas** (great cloud tooling + collaboration)
- **Raw WebGL + regl/twgl** (maximum control, highest implementation cost)

## Quick start

1. Serve the folder from a local web server (module imports require HTTP):
   ```bash
   cd <project-directory>
   python3 -m http.server 8080
   ```
2. Open `http://localhost:8080`.
3. Use the file pickers to set front/back sheet textures.
4. Use the top-right controls to adjust directional light position and ambient intensity.

## What is included

- `index.html`: complete standalone demo (scene, camera, controls, flexible mesh, lighting UI, image uploads)
- `PROJECT_PLAN.md`: implementation plan and phased expansion ideas
- `.gitignore`: baseline ignore rules for frontend/web workflow

## Further ideas

- Replace sinusoidal deformation with cloth simulation (constraints + pinned corners).
- Add direct manipulation handles to pull individual vertices/corners.
- Add HDRI environment lighting presets and shadow quality controls.
- Add texture transform controls (tiling/rotation/offset) for front/back images.
- Save/load scene state (camera, lighting, flex settings) as JSON.
