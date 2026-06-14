# 🌍 Ultimate Planetary & Art Sandbox Simulator

An interactive, high-performance web dashboard sandbox combining real-time planetary physics modeling, hydrodynamic fluid drag simulations, a digital paint-mixing engine, and WCAG 2.0 color accessibility diagnostics. 

Built entirely as a responsive, lightweight, single-file native application.

## 🚀 Live Features

### 🎬 Real-Time Physics Telemetry Viewport
* **Dynamic Environment Modeling:** Run calculations for atmospheric drag profiles on Earth or escape velocities across 10 different celestial bodies (Mercury, Venus, Mars, Jupiter, etc.).
* **Hydrodynamic Fluid Drag:** Simulates terminal velocity changes, deep water buoyancy, elastic trampoline bounces, and concrete impact surface matrices.
* **Vector Graph Matrix:** A real-time rendering engine that logs velocity telemetry onto a dynamically scaling canvas path.
* **Weather Vectors:** Simulates structural interference from crosswinds and severe headwinds on falling masses.

### 🎨 Fluid Paint Mixer (Custom Logic Engine)
* Uses multi-channel RGB vector averaging to simulate physical medium blending.
* Implements a 3D Euclidean distance formula ($\sqrt{\Delta R^2 + \Delta G^2 + \Delta B^2}$) to map mixed hex values against a color dictionary, auto-labeling the closest human-readable shade name.

### 🔍 UI Accessibility Contrast Diagnostics
* Formulates relative luminance tracking following official sRGB non-linear gamma expansions ($0.2126R + 0.7152G + 0.0722B$).
* Computes real-time WCAG 2.0 contrast ratios to output definitive reading PASS/FAIL diagnostics.
* Includes an smart contrast auto-optimizer fallback function.

---

## 🛠️ Advanced Technical Challenges Solved

### 📱 Force-Dark Mode Canvas Shielding
* **The Problem:** Aggressive system-level mobile browser "Force Dark Mode" overrides and accessibility filters aggressively invert or distort raw CSS background colors, ruining the accuracy of paint mixing and contrast diagnostic previews.
* **The Solution:** Converted static preview wrappers into low-level HTML5 `<canvas>` bitmap environments. Because mobile rendering engines recognize the canvas as a media/graphic asset container rather than a UI element, the pixels glide past background inversion filters entirely, guaranteeing 100% color-pure rendering on any mobile device.

### 📐 High-DPI "Retina" Layout Normalization
* Implemented hardware pixel ratio scaling (`window.devicePixelRatio`) combined with context matrix resets (`setTransform`) to prevent responsive canvas fonts and vector graph lines from blurring or shrinking during layout window resize events.

---

## 💻 Tech Stack
* **Language:** HTML5, CSS3 (Modern Flexbox/Grid layouts), JavaScript (Vanilla ES6+)
* **Graphics Core:** Low-level HTML5 Canvas API
* **Analytics:** Google Analytics (gtag.js) integration

---

## 🏎️ How to Run Locally

Because this utility is completely self-contained in a single file, you don't need to install any heavy packages or node dependencies.

1. Clone this repository:
   ```bash
   git clone [https://github.com/universal-cyber/space-art-calculator/commits?author=universal-cyber]

