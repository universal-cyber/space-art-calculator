---
title: "Building a Physics Simulator + Color Mixer + Accessibility Checker in Vanilla JavaScript"
published: false
description: "A student's journey: building an interactive physics simulator with Canvas API, real physics math, and accessibility testing—all in one HTML file with zero dependencies."
tags: javascript, webdev, physics, canvas, accessibility, gamedev, learning
cover_image: https://raw.githubusercontent.com/universal-cyber/space-art-calculator/main/cover-image.jpg
canonical_url: https://github.com/universal-cyber/space-art-calculator
---

# Building a Physics Simulator + Color Mixer in Vanilla JavaScript

Ever wanted to build something that combines physics, art, and accessibility into one elegant web app? I did—and I'm sharing how I built it all in a **single HTML file with zero dependencies**.

## Meet Space Art Calculator 🌍

[**Try it live here →**](https://universal-cyber.github.io/space-art-calculator/)

It's a responsive web app that does three powerful things:

1. **🎬 Drop objects from different planets** and watch real-time physics calculations
2. **🎨 Mix colors using RGB vector math** and get auto-labeled color names
3. **♿ Test color accessibility** (WCAG 2.0 compliance) in real-time

No npm. No build tools. No dependencies. Just one HTML file, ~500 lines of JavaScript, and a lot of fun.

---

## Why I Built This

As a Computer Science student focused on game development, I wanted to deepen my understanding of three fundamental skills:

- **Physics simulation** — Games need realistic physics engines
- **Graphics rendering** — Canvas API is similar to game rendering pipelines
- **Performance optimization** — Critical for games to run smoothly

This project was my way of mastering these fundamentals while building something cool and useful.

---

## The Three Pillars

### 🎬 Physics Telemetry Viewport

The physics module simulates what happens when you drop an object from Earth, Mars, Jupiter, and 7 other celestial bodies.

**The Math:**
- **Gravity** — F = m × g (where g varies by planet)
- **Drag Force** — F = 0.5 × ρ × v² × A × Cd
- **Terminal Velocity** — v_t = √((2mg) / (ρACd))

The app calculates:
- Real-time velocity and acceleration
- Terminal velocity (when drag equals gravity)
- Impact force on different surfaces
- Effect of wind and weather

**Real Example:**
On Earth, a 1kg ball reaches terminal velocity of ~53 m/s (~120 mph).
On Jupiter? ~150 m/s because gravity is 2.5x stronger.
On the Moon? ~77 m/s, then it hits the surface at a gentler impact.

```javascript
// Terminal velocity calculation
function calculateTerminalVelocity(mass, gravity, density, area, dragCoeff) {
  const numerator = 2 * mass * gravity;
  const denominator = density * area * dragCoeff;
  return Math.sqrt(numerator / denominator);
}
```

**Live Visualization:** As the object falls, the app renders a real-time vector graph showing velocity curves. You can see exactly how the object accelerates until drag equals gravity.

**Game Dev Connection:** This is exactly how games calculate projectile motion, falling damage, and physics interactions. Understanding this formula is essential for game development.

---

### 🎨 Fluid Color Mixer

Ever wonder how color mixing *actually* works mathematically?

The color mixer uses **3D Euclidean distance** in RGB color space to find the closest named color to any mix you create.

**The Math:**
When you blend two colors, you're averaging their RGB values:
```
R_mixed = (R₁ + R₂) / 2
G_mixed = (G₁ + G₂) / 2
B_mixed = (B₁ + B₂) / 2
```

Then the app uses the **Euclidean distance formula** to find the closest named color:
```
distance = √[(ΔR)² + (ΔG)² + (ΔB)²]
```

**Real Example:**
- Mix red (255, 0, 0) + blue (0, 0, 255) = purple (128, 0, 128)
- The app instantly tells you: "This is closest to 'Purple' or 'Violet'"

```javascript
function findClosestColor(r, g, b) {
  let closestColor = null;
  let minDistance = Infinity;
  
  colorDictionary.forEach(color => {
    const distance = Math.sqrt(
      Math.pow(r - color.r, 2) +
      Math.pow(g - color.g, 2) +
      Math.pow(b - color.b, 2)
    );
    
    if (distance < minDistance) {
      minDistance = distance;
      closestColor = color;
    }
  });
  
  return closestColor;
}
```

**Why This Matters:** It's a fun way to learn about color science, vector math, and distance calculations in 3D space—all concepts used in game graphics programming.

---

### ♿ WCAG 2.0 Accessibility Checker

This is my favorite feature because it solves a real-world problem: **How do I know if my text is readable on my background?**

The app uses the official WCAG 2.0 formula:

**Step 1: Calculate Relative Luminance**
```
L = 0.2126 × R + 0.7152 × G + 0.0722 × B
(where R, G, B are gamma-expanded sRGB values)
```

**Step 2: Calculate Contrast Ratio**
```
Contrast Ratio = (L_light + 0.05) / (L_dark + 0.05)
```

**Step 3: Check WCAG Levels**
- **AA**: 4.5:1 for normal text, 3:1 for large text ✅
- **AAA**: 7:1 for normal text, 4.5:1 for large text ✅✅

**Real Example:**
- Black text on white = 21:1 contrast (perfect ✅)
- Dark gray on light gray = 2:1 contrast (fails ❌)
- The app suggests the nearest color that passes!

```javascript
function getRelativeLuminance(r, g, b) {
  // Convert to sRGB (normalize 0-1)
  const [rs, gs, bs] = [r/255, g/255, b/255];
  
  // Apply gamma expansion
  const [rLinear, gLinear, bLinear] = [rs, gs, bs].map(c =>
    c <= 0.03928 ? c / 12.92 : Math.pow((c + 0.055) / 1.055, 2.4)
  );
  
  // Official WCAG formula
  return 0.2126 * rLinear + 0.7152 * gLinear + 0.0722 * bLinear;
}

function getContrastRatio(lum1, lum2) {
  const lighter = Math.max(lum1, lum2);
  const darker = Math.min(lum1, lum2);
  return (lighter + 0.05) / (darker + 0.05);
}
```

---

## The Technical Challenges I Solved

### 🔧 Challenge #1: Mobile Dark Mode Ruins Everything

**The Problem:**
On iOS and Android, aggressive "Force Dark Mode" inverts CSS colors automatically. This completely breaks color accuracy for my color mixer and accessibility checker.

**The Solution:**
Instead of using CSS background colors for color previews, I use the **HTML5 Canvas API**. Mobile browsers treat canvas as a graphic/media asset, so they don't apply dark mode overrides.

```javascript
// Instead of: element.style.backgroundColor = '#FF0000';
// We use Canvas:

const canvas = document.getElementById('colorPreview');
const ctx = canvas.getContext('2d');
ctx.fillStyle = '#FF0000';
ctx.fillRect(0, 0, canvas.width, canvas.height);
```

Result? Perfect color rendering on every device, regardless of system settings.

### 🔧 Challenge #2: Crisp Graphics on High-DPI Screens

**The Problem:**
On "Retina" displays (iPhone, MacBook Pro, etc.), the canvas looks blurry because the device has 2-3x physical pixels per CSS pixel.

**The Solution:**
Use `window.devicePixelRatio` to scale the canvas:

```javascript
const ratio = window.devicePixelRatio || 1;
canvas.width = cssWidth * ratio;
canvas.height = cssHeight * ratio;
ctx.scale(ratio, ratio); // Scale everything accordingly

// Fonts and lines now render crisply!
```

**Game Dev Connection:** Game engines do this exact same thing. Understanding pixel-perfect rendering is crucial for game graphics.

### 🔧 Challenge #3: Single-File Architecture

**The Goal:**
Ship the entire app as one HTML file. No build step, no dependencies, no package.json.

**The Solution:**
- Embed CSS in `<style>` tags
- Embed JavaScript in `<script>` tags
- Use modern JavaScript (ES6+) without transpiling
- Use Google Analytics for optional tracking

Result? Users can literally just download the file and open it. No npm install, no build process, no server needed.

---

## What You'll Learn From This Code

If you explore the repository, you'll find practical examples of:

✅ **Canvas API** — Real-time rendering, transformations, text rendering on high-DPI screens
✅ **Physics Math** — Gravity, drag, terminal velocity, vector calculations
✅ **Color Science** — RGB blending, Euclidean distance, WCAG accessibility formulas
✅ **Responsive Design** — Mobile-first CSS, Flexbox/Grid, device pixel ratio handling
✅ **Accessibility** — Not just testing WCAG compliance, but understanding the math behind it
✅ **Vanilla JavaScript** — No frameworks, no dependencies, just modern ES6+

---

## How to Use It

### Try It Live
👉 **[Space Art Calculator Live Demo](https://universal-cyber.github.io/space-art-calculator/)**

### Run It Locally
```bash
git clone https://github.com/universal-cyber/space-art-calculator.git
cd space-art-calculator

# Option 1: Open directly
open index.html

# Option 2: Use a local server
python -m http.server 8000
# Visit http://localhost:8000
```

---

## Want to Contribute?

The project is open source! Ideas for contributions:

- 🌍 Add more celestial bodies
- 📊 Export simulation data as CSV
- ⌨️ Keyboard shortcuts
- 🎨 More animation effects
- 📱 Better touch controls
- 📚 Interactive tutorials

Check out the [Contributing Guide](https://github.com/universal-cyber/space-art-calculator/blob/main/CONTRIBUTING.md) to get started.

---

## About Me

I'm a Computer Science student learning C++, JavaScript, and HTML/CSS with a goal of becoming a game developer. This project was a way to deepen my understanding of physics simulation, graphics rendering, and performance optimization—skills that directly apply to game development.

Building projects like this helps me master fundamentals while creating something useful for others. If you're a fellow student or aspiring game dev, I'd love to connect and hear about your journey!

Feel free to:
- ⭐ **Star the repo** — it helps others discover it
- 💬 **Open a discussion** — ask questions, share ideas
- 🤝 **Contribute** — I'd love collaborators!

---

## Key Takeaways

1. **You don't need frameworks for creative projects** — Vanilla JavaScript + Canvas can do amazing things
2. **Physics and math are beautiful when you can visualize them** — Interactive demos make concepts click
3. **Accessibility isn't just a checkbox** — Understanding WCAG means understanding color science
4. **Single-file architecture can be elegant** — If you're disciplined about organization
5. **Game dev fundamentals matter** — Physics, graphics, and performance optimization apply everywhere

---

## What's Next?

I'm working on:
- [ ] Animation presets (save/load common scenarios)
- [ ] Mobile touch controls for better UX
- [ ] Dark mode toggle with Canvas preservation
- [ ] Educational mode with guided tutorials
- [ ] More game dev examples (projectiles, collision detection)
- [ ] Performance optimizations for older devices

---

## Give It a Star! ⭐

If you found this interesting, [star the repo on GitHub](https://github.com/universal-cyber/space-art-calculator)! It helps others discover it.

**Questions or feedback?** Open a discussion on GitHub—I'd love to hear your thoughts!

---

**Happy coding! 🚀**

*P.S. — If you're learning game development, I'd recommend building physics simulations in vanilla JS first. It forces you to understand the fundamentals before jumping into game engines. This project proved that to me.*
