# Contributing to Space Art Calculator

Thank you for your interest in contributing! 🎉 Whether you're fixing bugs, adding features, or improving documentation, your help is welcome.

---

## 🚀 How to Contribute

### 1. **Report a Bug**
Found an issue? [Open a Bug Report](https://github.com/universal-cyber/space-art-calculator/issues/new?template=bug_report.md)

### 2. **Suggest a Feature**
Have an idea? [Open a Feature Request](https://github.com/universal-cyber/space-art-calculator/issues/new?template=feature_request.md)

### 3. **Improve Documentation**
Spotted a typo or unclear section? Improvements to README, docs, or code comments are always welcome!

### 4. **Submit Code Changes**
Want to contribute code? Follow these steps:

#### Step 1: Fork & Clone
```bash
git clone https://github.com/YOUR-USERNAME/space-art-calculator.git
cd space-art-calculator
```

#### Step 2: Create a Branch
```bash
git checkout -b feature/your-feature-name
# or
git checkout -b fix/bug-fix-name
```

#### Step 3: Make Your Changes
- Edit `index.html` (the single file contains all HTML, CSS, and JavaScript)
- Test thoroughly in multiple browsers and devices
- Keep the file clean and well-commented

#### Step 4: Commit & Push
```bash
git add index.html
git commit -m "feat: Add your feature" 
# or
git commit -m "fix: Fix the bug description"
git push origin feature/your-feature-name
```

#### Step 5: Open a Pull Request
- Go to the original repository
- Click "New Pull Request"
- Describe what you changed and why
- Provide screenshots/videos if applicable

---

## 📋 Code Style Guidelines

Since this is a single-file project, keep things organized:

- **Comment your code** — especially complex logic
- **Use meaningful variable names** — not `x` or `temp`
- **Keep functions focused** — one thing per function
- **Test on mobile** — ensure responsive design works
- **Check accessibility** — make sure your changes work for all users

### Example:
```javascript
// Calculate terminal velocity using drag force formula
// v_terminal = sqrt((2 * mass * gravity) / (density * area * drag_coefficient))
function calculateTerminalVelocity(mass, gravity, density, area, dragCoeff) {
  return Math.sqrt((2 * mass * gravity) / (density * area * dragCoeff));
}
```

---

## ✅ Before You Submit

- [ ] Code works in Chrome, Firefox, Safari, and Edge
- [ ] Tested on mobile (iPhone, Android)
- [ ] No console errors or warnings
- [ ] Code is well-commented
- [ ] Changes are focused (not multiple unrelated features)
- [ ] Commit message is clear and descriptive

---

## 🎯 Contribution Ideas

Not sure what to work on? Here are some ideas:

- **New celestial bodies** — Add more planets or custom gravity
- **Data export** — Save simulation results as CSV/JSON
- **Keyboard shortcuts** — Add quick key bindings for common actions
- **Animation improvements** — Smoother transitions or effects
- **Accessibility enhancements** — Better screen reader support
- **Presets** — Save and load common scenarios
- **Mobile optimizations** — Better touch controls
- **Documentation** — More examples or tutorials

---

## 📞 Questions?

- 💬 [Start a Discussion](https://github.com/universal-cyber/space-art-calculator/discussions)
- 🐛 [Open an Issue](https://github.com/universal-cyber/space-art-calculator/issues)

---

## 📄 License

By contributing, you agree that your contributions will be licensed under the MIT License.

---

**Thank you for helping make Space Art Calculator better! 🙏**
