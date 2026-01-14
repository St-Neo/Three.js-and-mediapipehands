You are an expert frontend creative developer specializing in Three.js, WebGL, and MediaPipe Hands. Build a high-performance, single-file `index.html` (HTML/CSS/JS combined) for a cyberpunk interactive particle system.

Visual style
- Theme: hardcore cyberpunk.
- Background: deep black with subtle moving grid/scanlines + vignette.
- HUD: minimalist data display in four corners (FPS, particle count, hand status) using Orbitron or mono font in neon cyan.
- Particles: AdditiveBlending, glowing neon look.
- Camera: show the mirrored webcam video behind the particles.

Core parameters
- Particle count: 12,000.
- Particle size: 2.4 (screen-space points, crisp dot matrix).
- Physics: fast return (lerp factor ~0.28), strong/snappy repulsion, planar (XY) only in text mode.
- Text sampling: canvas pixel scanning, 75px bold, grid-sampled dot matrix (no fuzzy fill).

Interactions
1) Left hand (command controller)
- 1 finger: text "Hello", color 0x00FFFF.
- 2 fingers: text "Zaid", color 0xFFFF00.
- 3 fingers: text "Three.js", color 0xFF00FF.
- 4 fingers: text "Mediapipe", color 0x00FF88.
- 5 fingers: Catch Mode (particles gather around left palm).

2) Right hand (physics interactor)
- Track index finger tip (landmark 8) as interaction point.
- Default (pointing/fist): strong scatter when touching text particles, XY only (no Z bulge).
- Right-hand swipe through text: trigger a water ripple ring (expanding radial wave in XY).
- Open hand (5 fingers): Nebula Mode (particles fill 3D screen volume) + sine-wave ripple when moving through particles.

3) Dual-hand combo
- If right hand open (nebula) AND left hand open (catch): pull all particles to left palm.
- Particles form a rotating 3D basketball in the left hand (Fibonacci sphere, orange with black seams).
- Motion: energetic bouncing trajectory toward the left hand (high-frequency Y sine).

Audio
- Use Web Audio (no external files). Unlock on first user gesture.
- Play short synth blips for: left text switch, catch, scatter, nebula, ultimate, and right-hand ripple.

Implementation notes
- Use MediaPipe Hands with max 2 hands, default webcam settings.
- Keep everything in a single `index.html` (no build step).
- Emphasize performance (BufferGeometry + typed arrays).
