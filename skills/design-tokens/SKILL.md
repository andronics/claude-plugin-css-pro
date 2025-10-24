---
name: design-tokens
description: Design token management for creating, organizing, and applying design tokens across projects. Supports multiple formats (CSS custom properties, Sass, JS, JSON). Use when setting up design systems or managing design tokens.
allowed-tools: Read, Write, Edit
---

# Design Tokens Skill

This skill helps you create, organize, and manage design tokens for scalable design systems. I'll guide you through token architecture, naming conventions, and implementation across different formats.

## What Are Design Tokens?

Design tokens are named entities that store visual design attributes. They create a single source of truth for design decisions and enable consistent styling across platforms and tools.

### Token Hierarchy
```
Global Tokens (Foundation)
    ↓
Semantic Tokens (Purpose/Context)
    ↓
Component Tokens (Specific Usage)
```

## Token Categories

### Color Tokens
- Brand colors
- Semantic colors (success, error, warning)
- Text colors
- Background colors
- Border colors
- State colors (hover, active, disabled)

### Spacing Tokens
- Margin and padding scales
- Gap values
- Layout spacing
- Component spacing

### Typography Tokens
- Font families
- Font sizes
- Font weights
- Line heights
- Letter spacing

### Size Tokens
- Width and height values
- Min/max constraints
- Breakpoints
- Container sizes

### Border Tokens
- Border widths
- Border radius values
- Border styles

### Shadow Tokens
- Box shadows
- Elevation levels
- Text shadows

### Animation Tokens
- Durations
- Timing functions
- Delays

## Token Naming Convention

### Pattern: `[category]-[property]-[variant]-[state]`

```css
/* Color tokens */
--color-primary          /* Brand primary */
--color-primary-hover    /* Hover state */
--color-primary-light    /* Variant */

--color-text-primary     /* Primary text */
--color-text-secondary   /* Secondary text */

--color-bg-primary       /* Primary background */
--color-bg-secondary     /* Secondary background */

/* Spacing tokens */
--spacing-1              /* Smallest */
--spacing-4              /* Base */
--spacing-8              /* Large */

/* Typography tokens */
--font-size-sm           /* Small */
--font-size-base         /* Base */
--font-size-lg           /* Large */

--font-weight-normal     /* 400 */
--font-weight-bold       /* 700 */

/* Component tokens */
--button-padding-x
--button-padding-y
--button-bg-primary
--button-text-primary

--card-padding
--card-radius
--card-shadow
```

## Global Tokens (Foundation)

```css
:root {
  /* Color primitives */
  --color-blue-50: #eff6ff;
  --color-blue-100: #dbeafe;
  --color-blue-200: #bfdbfe;
  --color-blue-300: #93c5fd;
  --color-blue-400: #60a5fa;
  --color-blue-500: #3b82f6;
  --color-blue-600: #2563eb;
  --color-blue-700: #1d4ed8;
  --color-blue-800: #1e40af;
  --color-blue-900: #1e3a8a;

  --color-gray-50: #f9fafb;
  --color-gray-100: #f3f4f6;
  --color-gray-200: #e5e7eb;
  --color-gray-300: #d1d5db;
  --color-gray-400: #9ca3af;
  --color-gray-500: #6b7280;
  --color-gray-600: #4b5563;
  --color-gray-700: #374151;
  --color-gray-800: #1f2937;
  --color-gray-900: #111827;

  /* Spacing scale (4px base) */
  --spacing-0: 0;
  --spacing-1: 0.25rem;   /* 4px */
  --spacing-2: 0.5rem;    /* 8px */
  --spacing-3: 0.75rem;   /* 12px */
  --spacing-4: 1rem;      /* 16px */
  --spacing-5: 1.25rem;   /* 20px */
  --spacing-6: 1.5rem;    /* 24px */
  --spacing-8: 2rem;      /* 32px */
  --spacing-10: 2.5rem;   /* 40px */
  --spacing-12: 3rem;     /* 48px */
  --spacing-16: 4rem;     /* 64px */

  /* Font sizes (modular scale 1.25) */
  --font-size-xs: 0.75rem;    /* 12px */
  --font-size-sm: 0.875rem;   /* 14px */
  --font-size-base: 1rem;     /* 16px */
  --font-size-lg: 1.125rem;   /* 18px */
  --font-size-xl: 1.25rem;    /* 20px */
  --font-size-2xl: 1.5rem;    /* 24px */
  --font-size-3xl: 1.875rem;  /* 30px */
  --font-size-4xl: 2.25rem;   /* 36px */
  --font-size-5xl: 3rem;      /* 48px */

  /* Font weights */
  --font-weight-thin: 100;
  --font-weight-light: 300;
  --font-weight-normal: 400;
  --font-weight-medium: 500;
  --font-weight-semibold: 600;
  --font-weight-bold: 700;
  --font-weight-black: 900;

  /* Line heights */
  --line-height-none: 1;
  --line-height-tight: 1.25;
  --line-height-snug: 1.375;
  --line-height-normal: 1.5;
  --line-height-relaxed: 1.625;
  --line-height-loose: 2;

  /* Border radius */
  --radius-none: 0;
  --radius-sm: 0.125rem;
  --radius-base: 0.25rem;
  --radius-md: 0.375rem;
  --radius-lg: 0.5rem;
  --radius-xl: 0.75rem;
  --radius-2xl: 1rem;
  --radius-full: 9999px;

  /* Shadows */
  --shadow-xs: 0 1px 2px 0 rgba(0, 0, 0, 0.05);
  --shadow-sm: 0 1px 3px 0 rgba(0, 0, 0, 0.1);
  --shadow-base: 0 1px 3px 0 rgba(0, 0, 0, 0.1), 0 1px 2px 0 rgba(0, 0, 0, 0.06);
  --shadow-md: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
  --shadow-lg: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
  --shadow-xl: 0 20px 25px -5px rgba(0, 0, 0, 0.1);
  --shadow-2xl: 0 25px 50px -12px rgba(0, 0, 0, 0.25);

  /* Animation */
  --duration-fast: 150ms;
  --duration-base: 250ms;
  --duration-slow: 350ms;
  --duration-slower: 500ms;

  --ease-in: cubic-bezier(0.4, 0, 1, 1);
  --ease-out: cubic-bezier(0, 0, 0.2, 1);
  --ease-in-out: cubic-bezier(0.4, 0, 0.2, 1);
}
```

## Semantic Tokens (Purpose)

```css
:root {
  /* Color semantics */
  --color-primary: var(--color-blue-600);
  --color-primary-hover: var(--color-blue-700);
  --color-primary-active: var(--color-blue-800);
  --color-primary-light: var(--color-blue-50);

  --color-secondary: var(--color-gray-600);
  --color-success: var(--color-green-600);
  --color-warning: var(--color-yellow-600);
  --color-error: var(--color-red-600);
  --color-info: var(--color-blue-500);

  /* Text colors */
  --color-text-primary: var(--color-gray-900);
  --color-text-secondary: var(--color-gray-600);
  --color-text-tertiary: var(--color-gray-500);
  --color-text-disabled: var(--color-gray-400);
  --color-text-inverse: var(--color-white);

  /* Surface colors */
  --color-surface-primary: var(--color-white);
  --color-surface-secondary: var(--color-gray-50);
  --color-surface-tertiary: var(--color-gray-100);
  --color-surface-overlay: rgba(0, 0, 0, 0.5);

  /* Border colors */
  --color-border: var(--color-gray-300);
  --color-border-hover: var(--color-gray-400);
  --color-border-focus: var(--color-primary);

  /* Spacing semantics */
  --spacing-xs: var(--spacing-2);
  --spacing-sm: var(--spacing-3);
  --spacing-md: var(--spacing-4);
  --spacing-lg: var(--spacing-6);
  --spacing-xl: var(--spacing-8);

  /* Typography semantics */
  --text-xs: var(--font-size-xs);
  --text-sm: var(--font-size-sm);
  --text-base: var(--font-size-base);
  --text-lg: var(--font-size-lg);
  --text-xl: var(--font-size-xl);
}
```

## Component Tokens (Specific)

```css
:root {
  /* Button */
  --button-padding-x: var(--spacing-4);
  --button-padding-y: var(--spacing-2);
  --button-font-size: var(--font-size-base);
  --button-font-weight: var(--font-weight-semibold);
  --button-radius: var(--radius-md);
  --button-transition: var(--duration-base) var(--ease-in-out);

  --button-primary-bg: var(--color-primary);
  --button-primary-bg-hover: var(--color-primary-hover);
  --button-primary-text: var(--color-text-inverse);

  --button-secondary-bg: transparent;
  --button-secondary-border: var(--color-border);
  --button-secondary-text: var(--color-text-primary);

  /* Input */
  --input-padding-x: var(--spacing-3);
  --input-padding-y: var(--spacing-2);
  --input-font-size: var(--font-size-base);
  --input-border: 1px solid var(--color-border);
  --input-border-focus: 2px solid var(--color-border-focus);
  --input-radius: var(--radius-md);
  --input-bg: var(--color-surface-primary);

  /* Card */
  --card-padding: var(--spacing-6);
  --card-bg: var(--color-surface-primary);
  --card-border: 1px solid var(--color-border);
  --card-radius: var(--radius-lg);
  --card-shadow: var(--shadow-md);

  /* Modal */
  --modal-width: 32rem;
  --modal-padding: var(--spacing-6);
  --modal-bg: var(--color-surface-primary);
  --modal-radius: var(--radius-lg);
  --modal-shadow: var(--shadow-2xl);
  --modal-overlay-bg: var(--color-surface-overlay);
}
```

## Multi-Format Token Output

### CSS Custom Properties
```css
/* tokens.css */
:root {
  --color-primary: #2563eb;
  --spacing-4: 1rem;
  --font-size-base: 1rem;
}
```

### Sass Variables
```scss
// tokens.scss
$color-primary: #2563eb;
$spacing-4: 1rem;
$font-size-base: 1rem;

// Map format
$colors: (
  'primary': #2563eb,
  'secondary': #6b7280,
);

$spacing: (
  '4': 1rem,
  '6': 1.5rem,
);
```

### JavaScript/TypeScript
```javascript
// tokens.js
export const tokens = {
  color: {
    primary: '#2563eb',
    secondary: '#6b7280',
  },
  spacing: {
    4: '1rem',
    6: '1.5rem',
  },
  fontSize: {
    base: '1rem',
    lg: '1.125rem',
  },
};

// TypeScript
export interface Tokens {
  color: {
    primary: string;
    secondary: string;
  };
  spacing: {
    4: string;
    6: string;
  };
}
```

### JSON
```json
{
  "color": {
    "primary": {
      "value": "#2563eb",
      "type": "color"
    },
    "secondary": {
      "value": "#6b7280",
      "type": "color"
    }
  },
  "spacing": {
    "4": {
      "value": "1rem",
      "type": "dimension"
    }
  }
}
```

## Theme Variations

### Light & Dark Themes
```css
:root {
  /* Light theme (default) */
  --color-bg: #ffffff;
  --color-text: #111827;
  --color-primary: #2563eb;
  --color-surface: #f9fafb;
  --color-border: #e5e7eb;
}

[data-theme="dark"] {
  /* Dark theme overrides */
  --color-bg: #111827;
  --color-text: #f9fafb;
  --color-primary: #60a5fa;
  --color-surface: #1f2937;
  --color-border: #374151;
}

[data-theme="high-contrast"] {
  /* High contrast theme */
  --color-bg: #000000;
  --color-text: #ffffff;
  --color-primary: #ffff00;
  --color-surface: #1a1a1a;
  --color-border: #ffffff;
}
```

### Brand Themes
```css
[data-brand="acme"] {
  --color-primary: #ff6b35;
  --font-family-display: "Montserrat", sans-serif;
  --radius-base: 0.5rem;
}

[data-brand="widgets-inc"] {
  --color-primary: #4caf50;
  --font-family-display: "Roboto", sans-serif;
  --radius-base: 0;
}
```

## Token Documentation Template

```markdown
## Color Tokens

### Primary
- **Token**: `--color-primary`
- **Value**: `#2563eb` (Blue 600)
- **Usage**: Primary actions, links, brand elements
- **Contrast**: 7.02:1 on white (AAA)
- **Related**:
  - `--color-primary-hover`: #1d4ed8
  - `--color-primary-light`: #eff6ff

### Text
- **Token**: `--color-text-primary`
- **Value**: `#111827` (Gray 900)
- **Usage**: Main body text, headings
- **Contrast**: 16.04:1 on white (AAA)

## Spacing Tokens

### Base Unit
- **Token**: `--spacing-4`
- **Value**: `1rem` (16px)
- **Usage**: Base spacing unit, component padding

## Component Tokens

### Button
- **Padding**: `--button-padding-x` (1rem), `--button-padding-y` (0.5rem)
- **Font**: `--button-font-size` (1rem), `--button-font-weight` (600)
- **Radius**: `--button-radius` (0.375rem)
- **Colors**:
  - Primary: `--button-primary-bg`, `--button-primary-text`
  - Secondary: `--button-secondary-border`, `--button-secondary-text`
```

## Token Best Practices

### ✓ Do
- Use hierarchical token structure
- Name tokens by purpose, not value
- Document all tokens with usage guidelines
- Version tokens with design system
- Test tokens in all themes
- Provide fallback values
- Group related tokens
- Use semantic naming

### ❌ Don't
- Name tokens by appearance (--color-blue)
- Skip documentation
- Create tokens for single-use values
- Mix naming conventions
- Hardcode values in components
- Create too many token levels
- Use inconsistent scales

## Example: Complete Token System

```css
:root {
  /* 1. GLOBAL TOKENS (Foundation) */

  /* Colors - Raw values */
  --color-blue-600: #2563eb;
  --color-gray-900: #111827;
  --color-white: #ffffff;

  /* Spacing - Base scale */
  --spacing-2: 0.5rem;
  --spacing-4: 1rem;

  /* 2. SEMANTIC TOKENS (Purpose) */

  /* Colors - Meaning */
  --color-primary: var(--color-blue-600);
  --color-text-primary: var(--color-gray-900);
  --color-surface: var(--color-white);

  /* Spacing - Context */
  --spacing-sm: var(--spacing-2);
  --spacing-md: var(--spacing-4);

  /* 3. COMPONENT TOKENS (Specific) */

  /* Button */
  --button-bg-primary: var(--color-primary);
  --button-text-primary: var(--color-surface);
  --button-padding-x: var(--spacing-md);
  --button-padding-y: var(--spacing-sm);
}

/* 4. USAGE */
.button--primary {
  background: var(--button-bg-primary);
  color: var(--button-text-primary);
  padding: var(--button-padding-y) var(--button-padding-x);
}
```

## Just Ask!

Tell me what you need:
- "Create a design token system"
- "Generate spacing tokens"
- "Set up color tokens"
- "Create component tokens for buttons"
- "Convert tokens to Sass format"
- "Set up dark theme tokens"

I'll help you build scalable design token systems!
