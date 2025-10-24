---
description: Initialize CSS project with intelligent architecture detection and best practices setup
allowed-tools: Read, Write, Edit, Glob, Grep, Bash
---

# CSS Project Initialization

I'll help you set up a new CSS project with an appropriate architecture and best practices.

## Analyzing Project Context

First, let me analyze your project to understand what you're building:

1. Checking for existing files and frameworks
2. Detecting project type (React, Vue, vanilla, etc.)
3. Identifying build tools (Webpack, Vite, etc.)
4. Understanding project scale and requirements

## Architecture Options

Based on your project, I can set up:

### 1. **Vanilla CSS with BEM**
Best for: Static sites, small projects, traditional web apps

**Structure:**
```
css/
├── base/
│   ├── reset.css
│   ├── typography.css
│   └── variables.css
├── components/
│   ├── button.css
│   ├── card.css
│   └── form.css
├── layouts/
│   ├── header.css
│   ├── footer.css
│   └── grid.css
├── utilities/
│   └── helpers.css
└── main.css
```

### 2. **Sass/SCSS with ITCSS**
Best for: Medium to large projects, traditional architecture

**Structure:**
```
scss/
├── settings/
│   └── _variables.scss
├── tools/
│   └── _mixins.scss
├── generic/
│   └── _reset.scss
├── elements/
│   └── _typography.scss
├── objects/
│   └── _layouts.scss
├── components/
│   ├── _button.scss
│   └── _card.scss
├── utilities/
│   └── _helpers.scss
└── main.scss
```

### 3. **CSS Modules**
Best for: React, Vue, or component-based frameworks

**Structure:**
```
src/
├── components/
│   ├── Button/
│   │   ├── Button.tsx
│   │   └── Button.module.css
│   └── Card/
│       ├── Card.tsx
│       └── Card.module.css
├── styles/
│   ├── globals.css
│   └── variables.css
└── App.tsx
```

### 4. **Utility-First (Tailwind-like)**
Best for: Rapid development, design systems

**Setup:**
- Configure Tailwind CSS or create custom utility system
- Set up PostCSS with plugins
- Configure PurgeCSS for production

### 5. **CSS-in-JS**
Best for: React apps, dynamic styling needs

**Options:**
- Styled Components
- Emotion
- Vanilla Extract (zero-runtime)
- Linaria (zero-runtime)

## What I'll Set Up

Based on your selection, I'll create:

✓ **File structure** - All directories and base files
✓ **Configuration files** - PostCSS, Sass, or build tool config
✓ **Design tokens** - Colors, spacing, typography scales
✓ **Base styles** - Reset, typography, variables
✓ **Example components** - Button, card to demonstrate patterns
✓ **Documentation** - README with conventions and usage
✓ **Linting** - Stylelint configuration
✓ **Formatting** - Prettier configuration for CSS

## Arguments

```bash
/css-init [architecture-type]
```

**architecture-type** (optional):
- `bem` - Vanilla CSS with BEM methodology
- `sass` - Sass/SCSS with ITCSS
- `modules` - CSS Modules
- `tailwind` - Tailwind CSS setup
- `css-in-js` - Styled Components or similar
- (omit for interactive selection)

## Examples

```bash
# Interactive mode - I'll ask questions
/css-init

# Direct initialization with Sass
/css-init sass

# Set up CSS Modules for React
/css-init modules

# Configure Tailwind CSS
/css-init tailwind
```

## What Happens Next

1. I'll analyze your project structure
2. Ask clarifying questions if needed
3. Create the file structure
4. Set up configuration files
5. Create example components
6. Generate documentation
7. Install dependencies (if needed)
8. Provide usage instructions

Let's get started! What type of project are you building?

Arguments provided: `$ARGUMENTS`
