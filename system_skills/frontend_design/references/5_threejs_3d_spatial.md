# 3D Graphics & Spatial Applications Design Guidelines

This reference covers 3D viewports, Three.js / WebGL scenes, 3D games (car racing, first-person 3D snake), interactive 3D product visualizers, and spatial geometry models.

## 1. Viewport Composition & Semantic Layering
- Full Viewport Immersion: 3D canvas fills container (w-full h-full).
- Semantic DOM Overlay: Headings, labels, and controls reside as accessible DOM elements over the canvas (z-10 pointer-events-auto).
- HUD Frosted Backing: Floating HUD with backdrop blur (bg-black/40 backdrop-blur-sm).
- WebGL Context Safety: Handle webglcontextlost and webglcontextrestored with graceful 2D fallbacks.

## 2. Lighting, Materials & Atmosphere
- Three-Point Studio Lighting: Key light (warm directional), Fill light (soft ambient cool), Rim light (sharp outline).
- Atmospheric Depth: Exponential scene fog matching background color.
- PBR Materials: MeshStandardMaterial / MeshPhysicalMaterial with tuned roughness and metalness.
