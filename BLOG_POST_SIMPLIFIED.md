---
title: "I Built a Physics Simulator + Color Mixer in One HTML File"
published: true
description: "A student's journey: physics simulation, color math, and accessibility—all in vanilla JavaScript with zero dependencies."
tags: javascript, physics, gamedev, canvas, learning
cover_image: https://raw.githubusercontent.com/universal-cyber/space-art-calculator/main/cover-image.jpg
canonical_url: https://github.com/universal-cyber/space-art-calculator
---

# I Built a Physics Simulator + Color Mixer in One HTML File

**[Try it live →](https://universal-cyber.github.io/space-art-calculator/)**

I wanted to understand three things game developers need to know: physics simulation, graphics rendering, and performance. So I built a single-file web app that does all three.

No npm. No build tools. No dependencies. Just ~500 lines of JavaScript in one HTML file.

---

## What It Does

**Drop objects from different planets** — Watch gravity, drag, and terminal velocity in real-time as objects fall from Earth, Mars, Jupiter, and more.

**Mix colors mathematically** — Blend RGB values and instantly see the closest named color using distance calculations.

**Test color accessibility** — Check if your text color meets WCAG standards (4.5:1 contrast ratio) so everyone can read it.

---

## The Physics Part

When you drop a 1kg ball from Earth, it accelerates until drag force equals gravity. That's called *terminal velocity*.

The math:
```
v_terminal = √((2 × mass × gravity) / (density × area × drag_coefficient))
```

**Real numbers:**
- Earth: ~53 m/s (120 mph)
- Jupiter: ~150 m/s (gravity is 2.5× stronger)
- Moon: ~77 m/s (but way less air)

```javascript
function terminalVelocity(mass, gravity, density, area, drag) {
  return Math.sqrt((2 * mass * gravity) / (density * area * drag));
}
```

**Why this matters:** Every game that has falling or flying objects uses this exact formula. Understanding it helps you build realistic movement.

---

## The Color Part

When you mix two colors, you're just averaging their RGB values:

```
Red_mixed = (R₁ + R₂) / 2
Green_mixed = (G₁ + G₂) / 2
Blue_mixed = (B₁ + B₂) / 2
```

Then I use **Euclidean distance** to find the closest named color:

```javascript
const distance = Math.sqrt(
  (r - colorR)² + (g - colorG)² + (b - colorB)²
);
```

Mix red + blue = purple. The app instantly finds the closest color name. That's it.

---

## The Accessibility Part

WCAG (Web Content Accessibility Guidelines) says your text needs enough contrast to be readable. The formula:

**Step 1:** Convert RGB to luminance (how bright it is)
```javascript
luminance = 0.2126×R + 0.7152×G + 0.0722×B
(with gamma correction applied)
```

**Step 2:** Calculate contrast ratio
```javascript
ratio = (brighter + 0.05) / (darker + 0.05)
```

**Step 3:** Check if it passes
- **AA level:** 4.5:1 or higher ✅
- **AAA level:** 7:1 or higher ✅✅

Black text on white = 21:1 (perfect). Dark gray on light gray = 2:1 (fails).

The app tests your colors in real-time and suggests fixes.

---

## Two Technical Wins

### Problem #1: Mobile Dark Mode Breaks Colors

On iOS/Android, the OS inverts colors automatically. This ruins a color mixer because colors get wrong.

**Solution:** Use Canvas instead of CSS backgrounds. Browsers treat Canvas as a graphic, so they don't apply dark mode.

```javascript
// Instead of: element.style.backgroundColor = '#FF0000';
// Use Canvas:
ctx.fillStyle = '#FF0000';
ctx.fillRect(0, 0, width, height);
```

Result: Perfect colors on every device.

### Problem #2: Blurry Graphics on High-DPI Screens

Retina displays have 2-3× physical pixels per CSS pixel, so Canvas looks blurry.

**Solution:**
```javascript
const ratio = window.devicePixelRatio;
canvas.width = cssWidth * ratio;
canvas.height = cssHeight * ratio;
ctx.scale(ratio, ratio);
```

Now everything renders crisply.

---

## How to Run It

**Live:** [space-art-calculator.github.io](https://universal-cyber.github.io/space-art-calculator/)

**Locally:**
```bash
git clone https://github.com/universal-cyber/space-art-calculator.git
cd space-art-calculator
open index.html
```

---

## What You Learn

From reading the code, you'll see:
- Canvas rendering (used in every game engine)
- Physics math (gravity, drag, velocity)
- Color science (RGB, luminance, contrast)
- Responsive design (mobile-first, device pixel ratio)
- Vanilla JavaScript (ES6+, no frameworks)

---

## Why I Built This

I'm a CS student learning game development. I realized I needed to understand physics simulation, graphics rendering, and performance before jumping into a game engine.

This project forced me to:
1. Learn the *real* physics equations, not approximate them
2. Render graphics efficiently (Canvas isn't magic)
3. Optimize for mobile (batteries matter)

Building something small and real teaches more than tutorials.

---

## Next Steps

Want to contribute? Ideas:
- Add more planets
- Export simulation data
- Keyboard shortcuts
- Better touch controls
- Interactive tutorials

[Open an issue](https://github.com/universal-cyber/space-art-calculator/issues) or [start a discussion](https://github.com/universal-cyber/space-art-calculator/discussions).

⭐ **Star the repo if you found this interesting!**

---

## Key Takeaway

You don't need frameworks to build cool things. Vanilla JavaScript + Canvas can handle physics, graphics, and complex math. And shipping one HTML file (no build step, no npm install) is actually elegant.

If you're learning game development, start here. Understand the fundamentals before frameworks.

---

**[Try the demo →](https://universal-cyber.github.io/space-art-calculator/)**

Happy coding! 🚀
