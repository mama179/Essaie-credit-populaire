# Quick Start Guide - Development

## 🚀 Getting Started

### Local Development Setup

#### Using Python HTTP Server (Easiest)
```powershell
# Navigate to project directory
cd "C:\Users\lenovo\Documents\CREDITS POPULAIRE"

# Start server (Python must be installed)
python -m http.server 8000

# Open in browser
Start-Process "http://localhost:8000"
```

#### Using Node.js HTTP Server
```powershell
# Install globally (one-time)
npm install -g http-server

# Navigate to project directory
cd "C:\Users\lenovo\Documents\CREDITS POPULAIRE"

# Start server
http-server

# Open in browser (usually http://localhost:8080)
```

#### Using PHP Built-in Server
```powershell
# Navigate to project directory
cd "C:\Users\lenovo\Documents\CREDITS POPULAIRE"

# Start server
php -S localhost:8000

# Open in browser
Start-Process "http://localhost:8000"
```

## 📁 File Structure

```
CREDITS POPULAIRE/
│
├── index.html                      # Main homepage
├── index.php                       # PHP version (if needed)
│
├── css/
│   ├── responsive.css             # Main styles (EDIT THIS)
│   ├── animations.css             # Animations (EDIT THIS)
│   ├── general.css                # Legacy styles
│   ├── style.css                  # Legacy styles
│   └── [other css files]
│
├── images/
│   ├── logo_ecpc.png              # Logo
│   ├── banniere.gif               # Hero banner
│   └── [other images]
│
├── services/
│   ├── compte_epargne.php
│   ├── digital_bank.php
│   └── [service pages]
│
├── agences/
│   ├── accueil.php
│   ├── centre.php
│   └── [branch pages]
│
├── statut/
│   └── [customer type pages]
│
├── carrieres/
│   ├── formations.php
│   ├── metiers.php
│   └── postuler.php
│
├── contacts/
│   └── contacts_tous.php
│
├── media/
│   ├── actualites.php
│   └── nos_images.php
│
├── slidenews/
│   └── images/
│
├── RESPONSIVE_DESIGN_GUIDE.md      # Design documentation
├── IMPLEMENTATION_SUMMARY.md       # What was changed
├── TESTING_GUIDE.md               # How to test
└── README.md                       # This file
```

## 🎨 Editing Styles

### Main Stylesheet Location
**File**: `css/responsive.css`

### CSS Variables (Color Theme)
Located at the top of `responsive.css`:
```css
:root {
  --primary: #0f3a8a;         /* Main blue */
  --secondary: #ff8c00;       /* Orange accent */
  --accent: #f6f9ff;          /* Light blue bg */
  --text: #1f2933;            /* Dark text */
  --muted: #6b7280;           /* Gray text */
  --radius: 12px;             /* Border radius */
  --shadow: 0 10px 30px rgba(0, 0, 0, 0.06);
  --transition: all 0.3s ease;
}
```

### Common Edits

**Change primary color (blue)**:
```css
--primary: #0f3a8a;  /* Change this to your color */
```

**Change secondary color (orange)**:
```css
--secondary: #ff8c00;  /* Change this to your color */
```

**Adjust spacing**:
```css
/* In .section { } */
padding: 56px 5vw;  /* Change 56px for vertical, 5vw for horizontal */
```

**Modify button size**:
```css
/* In .btn { } */
padding: 14px 24px;  /* top/bottom, left/right */
```

## 📱 Responsive Breakpoints

The design adapts at these key breakpoints:

| Width | Device | File Location |
|-------|--------|---------------|
| < 480px | Small Mobile | Line ~780 in responsive.css |
| 481-640px | Mobile | Line ~640 in responsive.css |
| 641-900px | Tablet | Line ~550 in responsive.css |
| > 900px | Desktop | Default styles |

To adjust breakpoint widths, find the `@media` queries in `responsive.css`:

```css
/* Change max-width value to adjust when breakpoint activates */
@media (max-width: 900px) { ... }
@media (max-width: 640px) { ... }
@media (max-width: 480px) { ... }
```

## 🎬 Adding Animations

Animations are in: `css/animations.css`

### Add a simple fade-in to an element:
```css
.my-element {
  animation: fadeIn 0.6s ease-out;
}
```

### Add a delayed entrance for multiple items:
```css
.my-element:nth-child(1) { animation-delay: 0.1s; }
.my-element:nth-child(2) { animation-delay: 0.2s; }
.my-element:nth-child(3) { animation-delay: 0.3s; }
```

### Available animations:
- `fadeIn` - Fade in with slight upward movement
- `slideInLeft` - Slide in from left side
- `slideInRight` - Slide in from right side
- `scaleUp` - Scale from smaller to normal size
- `pulse` - Gentle opacity pulse

## 🔧 Common Tasks

### Change a section's background color
**File**: `css/responsive.css`

Find the section class and modify `background`:
```css
.section--accent {
  background: linear-gradient(135deg, #0f3a8a 0%, #1f5ad1 100%);
  color: #fff;
}
```

### Adjust card grid columns
**File**: `css/responsive.css`

Find `.grid` class:
```css
.grid {
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: 24px;
}
```

Change `260px` to make columns wider/narrower.

### Hide element on mobile
**File**: `css/responsive.css`

In the mobile `@media` query:
```css
.element-to-hide {
  display: none !important;
}
```

### Make text larger on mobile
**File**: `css/responsive.css`

In mobile `@media` query:
```css
h1, h2 {
  font-size: 1.5rem;  /* Increase from default */
}
```

## 🧪 Testing Changes

After making changes:

1. **Save the CSS file** (Ctrl+S)
2. **Refresh the browser** (F5 or Ctrl+R)
3. **Hard refresh** to clear cache (Ctrl+Shift+R)
4. **Check mobile view** (F12 → Device Toggle)

## 📐 Typography System

### Font Sizes (Responsive)
Headings use `clamp()` for automatic scaling:

```css
h1 { font-size: clamp(1.8rem, 4vw, 3.2rem); }
h2 { font-size: clamp(1.5rem, 3.5vw, 2.2rem); }
h3 { font-size: clamp(1.1rem, 1.3vw, 1.3rem); }
body { font-size: 0.95rem; }
```

This means:
- Minimum size: First value (never smaller)
- Preferred size: Second value (scales with viewport)
- Maximum size: Third value (never larger)

## 🎯 Spacing System

### Horizontal Padding
Most sections use `5vw` (5% of viewport width):
```css
.section { padding: 56px 5vw; }
```

On mobile, this changes to `4vw`:
```css
@media (max-width: 640px) {
  .section { padding: 36px 4vw; }
}
```

### Vertical Spacing
Main sections use these gap values:
- Desktop: 32-40px
- Tablet: 28px
- Mobile: 16-20px

## 🚀 Performance Tips

1. **Minimize CSS**: Remove unused styles
2. **Optimize Images**: Use appropriate sizes
3. **Lazy Load**: Use `loading="lazy"` on images
4. **Cache**: Browser caching for repeat visits
5. **Minify**: Minify CSS for production

## 🔒 Security Notes

1. **Always validate** PHP form inputs
2. **Use HTTPS** in production
3. **Keep dependencies** updated
4. **Escape output** in PHP templates
5. **Regular backups** of important files

## 📝 Editing HTML Content

### Main page: `index.html`

**Add a new section**:
```html
<section class="section" id="my-section">
  <div class="section__header">
    <h2>Section Title</h2>
    <p>Description</p>
  </div>
  <div class="grid">
    <!-- Add cards here -->
  </div>
</section>
```

**Add a new card**:
```html
<article class="card">
  <img src="images/example.jpg" alt="Description">
  <div class="card__body">
    <h3>Card Title</h3>
    <p>Card description text.</p>
    <a class="link" href="/path">Learn more</a>
  </div>
</article>
```

## 🆘 Troubleshooting

### Styles not updating
- [ ] Hard refresh browser (Ctrl+Shift+R)
- [ ] Check file path in HTML is correct
- [ ] Verify CSS syntax (missing semicolons, brackets)
- [ ] Check browser console for errors (F12)

### Mobile menu not working
- [ ] Verify HTML has `.nav__toggle` button
- [ ] Check JavaScript event listener exists
- [ ] Ensure `.nav__links--open` class exists in CSS
- [ ] Look for console errors

### Layout broken at certain widths
- [ ] Check all `@media` queries
- [ ] Verify `minmax()` grid values
- [ ] Test exact breakpoint width
- [ ] Check for conflicting CSS rules

### Images not showing
- [ ] Verify image file exists in `images/` folder
- [ ] Check image path is correct in HTML
- [ ] Ensure image format supported (jpg, png, gif)
- [ ] Check file name case sensitivity

## 📚 Resources

- **CSS Reference**: https://developer.mozilla.org/en-US/docs/Web/CSS
- **Responsive Design**: https://web.dev/responsive-web-design-basics/
- **Accessibility**: https://www.w3.org/WAI/WCAG21/quickref/
- **Browser DevTools**: https://developer.chrome.com/docs/devtools/

## 💬 Support

For questions about:
- **CSS/HTML**: Check MDN Web Docs
- **Responsive Design**: Read RESPONSIVE_DESIGN_GUIDE.md
- **Testing**: Read TESTING_GUIDE.md
- **What Changed**: Read IMPLEMENTATION_SUMMARY.md

---

**Last Updated**: December 2025
**Version**: 2.0
**Status**: Ready for Development ✅
