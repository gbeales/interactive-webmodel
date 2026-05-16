# Project Plan: Interactive Flexible 3D Sheet Web Demo

## 1) Goal
Build a standalone browser page that renders a flexible rectangular mesh in a 3D viewport, allows user interaction, and applies user-provided front/back images as sheet faces.

## 2) Recommended Framework
- **Primary recommendation: Three.js**
  - Large ecosystem and examples for mesh deformation, controls, and lights.
  - Quick setup using CDN for a standalone prototype.
  - Works directly with WebGL and has mature helper utilities.

## 3) MVP Scope
- Single `index.html` that runs with no build step.
- 3D scene with:
  - Perspective camera
  - Orbit mouse controls
  - Flexible subdivided plane geometry
  - Directional + ambient lighting
- UI widgets for:
  - Directional light position (`x/y/z`)
  - Ambient light intensity
  - Flex/wave amount and speed
- File inputs:
  - Upload front image
  - Upload back image
- Double-sided rendering:
  - Front and back each use separate texture maps

## 4) Delivery Steps
1. Scaffold standalone HTML/CSS/JS files.
2. Add Three.js scene, camera, renderer, controls.
3. Add subdivided plane and vertex animation for flexible behavior.
4. Add front/back texture support with image upload.
5. Add runtime controls (GUI sliders).
6. Add responsive resizing and basic error handling.
7. Document usage and extension ideas in README.

## 5) Suggested Next Enhancements
- Add drag interaction to pin/deform corners directly.
- Upgrade from procedural wave to cloth simulation (Verlet/constraints).
- Add HDRI environment maps and shadow tuning presets.
- Add export/import of lighting and camera presets.
- Add mobile touch gestures and performance quality presets.
