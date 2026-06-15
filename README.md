# 🌍 Space Art Calculator

> An interactive physics simulator + artistic color mixer + accessibility validator, all in one elegant single-file web app.

**[🚀 Try it Live](https://universal-cyber.github.io/space-art-calculator/)** • **[View Code](#-how-to-run-locally)** • **[Give Feedback](#-feedback--contributions)**

---

## ✨ What Is This?

A responsive, mobile-friendly web app that combines three powerful tools:

1. **🎬 Physics Simulator** — Drop objects from Earth, Mars, Jupiter and more. See real-time velocity, acceleration, and impact calculations
2. **🎨 Color Mixer** — Blend colors using RGB vector math and get auto-labeled color names
3. **♿ Accessibility Checker** — Test color contrast ratios (WCAG 2.0) in real-time

Built entirely with **vanilla HTML5, CSS3, and JavaScript** — no dependencies, no build tools. Single file. Mobile-optimized.

---

## 🎯 Key Features

### Physics Telemetry Viewport
- **10 Celestial Bodies** — Simulate gravity on Mercury, Venus, Earth, Mars, Jupiter, Saturn, and more
- **Hydrodynamic Drag** — Terminal velocity, water buoyancy, trampoline bounces, concrete impacts
- **Real-Time Graph** — Watch velocity change in live vector graph visualization
- **Weather Effects** — Add crosswinds and headwinds to affect falling objects

### 🎨 Fluid Color Mixer
- **RGB Vector Blending** — Uses 3D Euclidean distance formula to find the closest named color
- **Instant Feedback** — See hex codes and human-readable color names as you mix
- **Smooth Transitions** — Real-time color preview

### ♿ WCAG 2.0 Contrast Checker
- **Instant Pass/Fail** — Determines if text/background combinations meet accessibility standards
- **Auto-Optimizer** — Suggests the nearest passing color combination
- **Real-time Calculation** — Uses official sRGB gamma expansion formula

---

## 🛠️ Technical Highlights

This project solves real-world web development challenges:

**Force-Dark Mode Canvas Shielding**
- Problem: Mobile browsers' "Force Dark Mode" distorts CSS colors
- Solution: Uses HTML5 Canvas as a bitmap container (immune to dark mode overrides)

**High-DPI Retina Rendering**
- Implements `window.devicePixelRatio` scaling for crisp graphics on all devices
- Prevents canvas text and vector lines from blurring

**Single-File Architecture**
- No dependencies, no build step, no npm install
- Just one HTML file with embedded CSS and JavaScript
- Download and run locally in seconds

---

## 🚀 Quick Start

### Try It Online
**[👉 Click here to use it now](https://universal-cyber.github.io/space-art-calculator/)**

### Run Locally

Since this is a single-file app, it's super simple:

```bash
# Clone the repo
git clone https://github.com/universal-cyber/space-art-calculator.git
cd space-art-calculator

# Option 1: Open in your browser directly
open index.html

# Option 2: Use Python's built-in server (for better compatibility)
python -m http.server 8000
# Then visit http://localhost:8000
```

That's it! No npm, no build tools, no dependencies.

---

## 💻 Tech Stack

| Component | Technology |
|-----------|-----------|
| **Language** | HTML5, CSS3 (Flexbox/Grid), JavaScript (ES6+) |
| **Graphics** | HTML5 Canvas API |
| **Styling** | Modern CSS with Dark Mode support |
| **Analytics** | Google Analytics (gtag.js) |
| **Hosting** | GitHub Pages |

---

## 📊 Use Cases

- **Physics Teachers** — Visualize gravity and drag in different environments
- **Web Developers** — Learn about Canvas, responsive design, accessibility
- **Designers** — Test color combinations for WCAG compliance
- **Students** — Interactive way to understand physics concepts

---

## 🎓 What You'll Learn

If you explore the code, you'll find examples of:
- **Canvas API** — Real-time graphics rendering and transformations
- **Physics Math** — Velocity, acceleration, drag calculations
- **Color Science** — RGB blending, Euclidean distance, contrast ratios
- **Responsive Design** — Mobile-first CSS, device pixel ratio handling
- **Accessibility** — WCAG 2.0 standards and real-time testing
- **Vanilla JavaScript** — No frameworks, pure ES6+

---

## 📝 Feedback & Contributions

**Have an idea or found a bug?**

- [💬 Start a Discussion](https://github.com/universal-cyber/space-art-calculator/discussions) — Ask questions, suggest features
- [🐛 Open an Issue](https://github.com/universal-cyber/space-art-calculator/issues) — Report bugs or request features
- [🚀 Submit a Pull Request](https://github.com/universal-cyber/space-art-calculator/pulls) — Contribute code

### Ideas for Enhancement
- More celestial bodies or custom gravity settings
- Export simulation data as CSV
- Dark mode toggle improvements
- Additional accessibility testing tools
- Simulation presets and saved scenarios

---

## 📄 License

MIT License — Feel free to use, modify, and distribute.

---

## 🙏 Show Your Support

If you find this useful:
- ⭐ **Star this repo** — It helps others discover it
- 🔄 **Share it** — Tell other developers about it
- 💬 **Give feedback** — Let me know how you're using it
- 🤝 **Contribute** — Submit improvements

---

**Made with ❤️ by [universal-cyber](https://github.com/universal-cyber)**

