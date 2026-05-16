# Alternative Implementation Plan: Spring-Chain Edge Flex

## Goal
Replace the current vertex-direct deformation with a physically inspired spring-chain profile so the sheet edges and interior settle naturally during and after rotation.

## Core Idea
Use a 1D spring chain across the sheet width (x-axis) to generate a bend profile, then apply that profile to each row of the plane geometry.

## Model
- Chain nodes: one per x-segment (or a reduced count for performance).
- State per node:
  - position (bend offset in z)
  - velocity
- Springs:
  - Structural springs between neighboring nodes.
  - Optional damping per node.
- Drive force:
  - Derived from sheet angular velocity around y-axis.
  - Signed force applied strongest at edges, weaker toward center.

## Update Loop
1. Compute delta time and angular velocity from sheet rotation.
2. Build edge-weighted drive force per node.
3. Integrate spring system (semi-implicit Euler):
   - velocity += acceleration * dt
   - position += velocity * dt
4. Clamp node displacement to max bend.
5. Sample chain profile to all vertices by x index.
6. Recompute normals and render.

## Suggested Parameters
- maxBend: 0.03 to 0.16
- springStiffness: 20 to 120
- damping: 4 to 20
- edgeDriveGain: 0.02 to 0.18
- edgeExponent: 1.0 to 2.5

## Why This Is Useful
- Produces secondary motion that feels more like fabric/paper inertia.
- Naturally creates catch-up and settle behavior without procedural wave functions.
- Easy to compare directly against angular-velocity edge-lag by swapping deformation modules.

## Implementation Notes
- Keep all lighting and texture upload logic unchanged.
- Share one deformation profile for both front/back meshes by keeping shared geometry.
- Start with node count equal to plane width segments + 1 for direct index mapping.
- Add a feature toggle so A/B testing against angular-lag is easy.

## Test Checklist
- Rotate slowly and quickly in both directions.
- Confirm deformation settles to flat at near-zero angular velocity.
- Check for jitter at very small dt and on window focus changes.
- Verify no visible texture tearing across front/back faces.
- Confirm performance remains stable on lower-end devices.
