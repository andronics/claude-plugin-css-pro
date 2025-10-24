---
description: Interactive layout generator for Flexbox and Grid with live preview code
allowed-tools: Read, Write
---

# Interactive Layout Generator

I'll help you create responsive layouts using Flexbox or CSS Grid through an interactive process.

## Arguments

```bash
/css-layout [layout-type]
```

**layout-type** (optional):
- `flexbox` - Create Flexbox layout
- `grid` - Create CSS Grid layout
- `holy-grail` - Classic 3-column layout
- `sidebar` - Sidebar + content layout
- `cards` - Responsive card grid
- `navbar` - Navigation bar layout
- `dashboard` - Dashboard grid layout
- (omit for interactive selection)

## Layout Types I Can Create

### 1. **Flexbox Layouts**

#### Navigation Bar
- Horizontal navigation
- Logo, menu items, action buttons
- Responsive mobile menu

#### Card Row
- Flexible card container
- Auto-wrapping cards
- Equal heights

#### Centered Content
- Vertical and horizontal centering
- Full viewport height
- Responsive sizing

#### Holy Grail
- Header, footer, sidebar, main content
- Flexible height distribution
- Responsive stacking

### 2. **CSS Grid Layouts**

#### Responsive Grid
- Auto-fitting columns
- No media queries needed
- Minimum card size

#### Dashboard Layout
- Named grid areas
- Complex arrangements
- Responsive breakpoints

#### Magazine Layout
- Asymmetric grid
- Spanning cells
- Feature areas

#### Masonry-style
- Pinterest-like layout
- Variable heights
- Dense packing

## Interactive Process

I'll ask you these questions:

1. **What are you building?**
   - Navigation, content grid, page layout, etc.

2. **How many items/sections?**
   - Number of columns, rows, or components

3. **Responsive behavior?**
   - Mobile-first, breakpoints, stacking order

4. **Spacing requirements?**
   - Gap between items, padding, margins

5. **Sizing constraints?**
   - Fixed widths, min/max sizes, flexible areas

## Example: Card Grid

**Me:** What kind of layout do you need?

**You:** I need a responsive card grid that shows 1 column on mobile, 2 on tablet, 3 on desktop.

**Me:** Here's your layout:

```html
<div class="card-grid">
  <div class="card">Card 1</div>
  <div class="card">Card 2</div>
  <div class="card">Card 3</div>
  <!-- More cards -->
</div>
```

```css
/* Responsive card grid using Grid */
.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 1.5rem;
  padding: 1rem;
}

.card {
  background: white;
  padding: 1.5rem;
  border-radius: 0.5rem;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

/* Explicit breakpoints (alternative approach) */
@media (max-width: 640px) {
  .card-grid {
    grid-template-columns: 1fr;
  }
}

@media (min-width: 641px) and (max-width: 1024px) {
  .card-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1025px) {
  .card-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}
```

## Example: Navbar

**You:** `/css-layout navbar`

**Me:** Let me create a responsive navbar for you. What items should it include?

**You:** Logo on left, menu items in center, login button on right.

**Me:** Here's your navbar:

```html
<nav class="navbar">
  <div class="navbar__logo">Logo</div>

  <ul class="navbar__menu">
    <li><a href="#home">Home</a></li>
    <li><a href="#about">About</a></li>
    <li><a href="#services">Services</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>

  <button class="navbar__button">Login</button>
</nav>
```

```css
/* Desktop navbar */
.navbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1rem 2rem;
  background: white;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.navbar__logo {
  font-size: 1.5rem;
  font-weight: bold;
  color: #333;
}

.navbar__menu {
  display: flex;
  gap: 2rem;
  list-style: none;
  margin: 0;
  padding: 0;
}

.navbar__menu a {
  text-decoration: none;
  color: #666;
  font-weight: 500;
  transition: color 0.2s;
}

.navbar__menu a:hover {
  color: #333;
}

.navbar__button {
  padding: 0.5rem 1.5rem;
  background: #007bff;
  color: white;
  border: none;
  border-radius: 0.25rem;
  cursor: pointer;
  font-weight: 500;
}

/* Mobile responsive */
@media (max-width: 768px) {
  .navbar {
    flex-direction: column;
    align-items: flex-start;
    gap: 1rem;
  }

  .navbar__menu {
    flex-direction: column;
    gap: 0.5rem;
    width: 100%;
  }

  .navbar__button {
    width: 100%;
  }
}
```

## Example: Holy Grail Layout

**You:** `/css-layout holy-grail`

**Me:** Creating a classic holy grail layout with header, footer, sidebar, and main content:

```html
<div class="layout">
  <header class="header">Header</header>
  <nav class="sidebar">Sidebar</nav>
  <main class="main">Main Content</main>
  <aside class="aside">Aside</aside>
  <footer class="footer">Footer</footer>
</div>
```

```css
/* Grid-based holy grail */
.layout {
  display: grid;
  grid-template-areas:
    "header header header"
    "sidebar main aside"
    "footer footer footer";
  grid-template-columns: 200px 1fr 200px;
  grid-template-rows: auto 1fr auto;
  min-height: 100vh;
  gap: 1rem;
}

.header {
  grid-area: header;
  background: #333;
  color: white;
  padding: 1rem;
}

.sidebar {
  grid-area: sidebar;
  background: #f0f0f0;
  padding: 1rem;
}

.main {
  grid-area: main;
  background: white;
  padding: 2rem;
}

.aside {
  grid-area: aside;
  background: #f0f0f0;
  padding: 1rem;
}

.footer {
  grid-area: footer;
  background: #333;
  color: white;
  padding: 1rem;
  text-align: center;
}

/* Responsive - Stack on mobile */
@media (max-width: 768px) {
  .layout {
    grid-template-areas:
      "header"
      "sidebar"
      "main"
      "aside"
      "footer";
    grid-template-columns: 1fr;
  }
}
```

## Common Layout Patterns

### Center Anything
```css
.center {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}
```

### Sidebar Layout
```css
.layout {
  display: flex;
  min-height: 100vh;
}

.sidebar {
  flex: 0 0 250px;
}

.main {
  flex: 1;
}
```

### Responsive Grid (No Media Queries)
```css
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1rem;
}
```

### Sticky Footer
```css
body {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

main {
  flex: 1;
}

footer {
  /* Sticks to bottom */
}
```

## Customization Options

For each layout, I can adjust:

- **Spacing**: Gap, padding, margins
- **Sizing**: Fixed, percentage, flexible
- **Breakpoints**: Custom responsive behavior
- **Colors**: Theme integration
- **Components**: Additional elements

## Best Practices I Follow

✓ **Mobile-first** - Start with mobile, enhance for desktop
✓ **Semantic HTML** - Proper element usage
✓ **Accessibility** - Logical tab order, ARIA when needed
✓ **Modern CSS** - Flexbox/Grid, no floats
✓ **Flexible** - Works with varying content
✓ **Responsive** - Adapts to all screen sizes

## Examples

```bash
# Interactive mode
/css-layout

# Specific layout type
/css-layout flexbox

# Pre-defined pattern
/css-layout navbar

# Grid layout
/css-layout grid

# Holy grail layout
/css-layout holy-grail

# Card grid
/css-layout cards

# Dashboard
/css-layout dashboard
```

## What You'll Get

For each layout:

✓ **HTML structure** - Semantic markup
✓ **CSS code** - Complete, production-ready
✓ **Responsive behavior** - Mobile to desktop
✓ **Comments** - Explaining key parts
✓ **Variations** - Alternative approaches
✓ **Customization guide** - How to modify

---

Let's create your layout!

Layout type: `$ARGUMENTS`

Tell me what you're building, and I'll generate the perfect layout for you.
