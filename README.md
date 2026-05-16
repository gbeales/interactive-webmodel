# interactive-webmodel

A standalone WebGL demo page with an integrated 3D viewport that renders a flexible rectangular sheet. You can orbit around the mesh, upload different front/back images, and tweak lighting in real time.

## Quick start

1. Serve the folder from a local web server (module imports require HTTP):
   ```bash
   cd <project-directory>
   python3 -m http.server 8080
   ```
2. Open `http://localhost:8080`.
3. Use the file pickers to set front/back sheet textures.
4. Use the top-right controls to adjust directional light position and ambient intensity.

## What has been built

- `index.html`:
  - 3D scene with perspective camera and orbit controls
  - Flexible subdivided rectangular sheet with continuous deformation
  - Independent front/back sheet texturing
  - Front/back image upload inputs
  - Directional + ambient lighting with interactive GUI controls
- `PROJECT_PLAN.md`: planning and future-work recommendations
- `.gitignore`: baseline ignore rules for frontend/web workflow

## Controls and interaction

- Left-click + drag: orbit camera
- Scroll: zoom
- Right-click + drag: pan
- Front face image / Back face image: upload independent textures
- GUI panel: adjust light position, ambient intensity, and flex animation parameters
