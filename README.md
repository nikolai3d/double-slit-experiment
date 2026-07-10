# Double-Slit Experiment — WebGL Particle Simulation

An interactive, single-file visualization of the quantum double-slit experiment.
Particles are fired one at a time at a barrier with two slits; each lands at a
single point on the detection screen, yet thousands of them build up an
interference pattern. Toggle the **which-path detector** to "observe" the slits
and watch the interference collapse into two single-slit diffraction humps.

## Features

- WebGL point-sprite particle simulation (up to 24,000 particles in flight)
- Dot-by-dot accumulation on a head-on "detector face" (framebuffer texture),
  reproducing the iconic build-up images from real electron experiments
- Landing positions sampled from the exact Fraunhofer intensity
  `I(θ) ∝ cos²(πd·sinθ/λ) · sinc²(πa·sinθ/λ)` via inverse-CDF tables
- **Theory mode**: an idealized which-path detector toggle that collapses the
  fringes into two single-slit humps
- **Real-experiment mode**: polarization tagging (quarter-wave plates on the
  slits, photons color-coded by slit) plus a quantum-eraser polarizer that
  absorbs half the photons, restores the fringes, and shifts them as it
  rotates (anti-fringes at 90°)
- Live histogram of hits with a dashed theoretical-curve overlay
- Adjustable wavelength, slit separation, slit width, and emission rate
- No dependencies, no build step — one `index.html`

## Run locally

Open `index.html` in any modern browser. That's it.

## Publish on GitHub Pages

1. Create a GitHub repository and push this directory:

   ```sh
   git init
   git add index.html README.md
   git commit -m "Double-slit experiment simulation"
   git remote add origin https://github.com/<you>/<repo>.git
   git push -u origin main
   ```

2. In the repository: **Settings → Pages → Build and deployment**, set
   *Source* to **Deploy from a branch**, choose `main` and `/ (root)`, save.

3. The app will be live at `https://<you>.github.io/<repo>/`.

## Physics notes

- In superposition mode, each particle's landing point is drawn from the full
  two-slit interference distribution — even though it is drawn traveling
  through one slit, its statistics come from both.
- With which-path measurement on, each particle's landing point is drawn from
  its own slit's single-slit diffraction envelope; the interference term
  vanishes, as in the real experiment.
- Units are dimensionless (screen distance L ≈ 1); sliders show values ×1000.
