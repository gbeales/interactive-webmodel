# interactive-webmodel

A standalone WebGL demo page with an integrated 3D viewport that renders a flexible rectangular sheet. You can rotate the paper directly with pointer drag, upload different front/back images, and tweak lighting in real time.

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
  - 3D scene with perspective camera and direct pointer-driven sheet rotation
  - Flexible subdivided rectangular sheet with a 2D spring-mesh soft-paper model
  - Independent front/back sheet texturing
  - Front/back image upload inputs
  - Directional + ambient lighting with interactive GUI controls and material presets
- `PROJECT_PLAN.md`: planning and future-work recommendations
- `.gitignore`: baseline ignore rules for frontend/web workflow

## Controls and interaction

- Left-click + drag on viewport: rotate paper on x/y axes
- Front face image / Back face image: upload independent textures
- GUI panel: adjust light position, ambient intensity, and spring-paper tuning parameters
- GUI panel presets: Soft Paper, Soft Fabric, and Stiff Card
