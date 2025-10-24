---
description: Design token operations: generate, extract, convert, and apply design tokens
allowed-tools: Read, Write, Edit, Glob, Grep
---

# Design Token Manager

I'll help you manage design tokens: generate token systems, extract tokens from existing CSS, convert between formats, and apply tokens to your project.

## Arguments

```bash
/css-tokens [operation] [options]
```

**operation**:
- `generate` - Create new token system
- `extract` - Extract tokens from existing CSS
- `convert` - Convert between formats (CSS/Sass/JS/JSON)
- `apply` - Apply tokens to CSS files
- `audit` - Audit token usage
- `sync` - Sync tokens from design tools
- (omit for interactive mode)

## Operations

### 1. Generate Tokens

Create a complete design token system from scratch.

**What I'll create:**

```
tokens/
├── global/
│   ├── colors.css       # Color primitives
│   ├── spacing.css      # Spacing scale
│   ├── typography.css   # Font tokens
│   └── effects.css      # Shadows, transitions
├── semantic/
│   ├── colors.css       # Semantic color tokens
│   └── spacing.css      # Semantic spacing tokens
├── component/
│   ├── button.css       # Button tokens
│   ├── card.css         # Card tokens
│   └── input.css        # Input tokens
└── tokens.css           # Combined output
```

**Token Categories:**

#### Color Tokens
```css
/* Global - Raw color values */
--color-blue-500: #3b82f6;
--color-gray-900: #111827;

/* Semantic - Purpose-based */
--color-primary: var(--color-blue-500);
--color-text-primary: var(--color-gray-900);

/* Component - Specific usage */
--button-bg-primary: var(--color-primary);
```

#### Spacing Tokens
```css
/* Global - Base scale */
--spacing-4: 1rem;
--spacing-6: 1.5rem;

/* Semantic - Context */
--spacing-md: var(--spacing-4);
--spacing-lg: var(--spacing-6);

/* Component - Usage */
--button-padding-x: var(--spacing-md);
```

#### Typography Tokens
```css
/* Global - Sizes and weights */
--font-size-base: 1rem;
--font-weight-semibold: 600;

/* Semantic - Purpose */
--text-base: var(--font-size-base);
--text-bold: var(--font-weight-semibold);

/* Component - Application */
--button-font-size: var(--text-base);
--button-font-weight: var(--text-bold);
```

### 2. Extract Tokens

Extract design tokens from existing CSS files.

**What I'll analyze:**
- Color values (hex, rgb, hsl)
- Spacing values (margins, paddings, gaps)
- Font sizes and weights
- Border radius values
- Shadow definitions
- Transition timings

**Example:**

**Input (existing CSS):**
```css
.button {
  background: #3b82f6;
  padding: 0.75rem 1.5rem;
  font-size: 1rem;
  border-radius: 0.375rem;
}

.card {
  background: #ffffff;
  padding: 1.5rem;
  border-radius: 0.5rem;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}
```

**Output (extracted tokens):**
```css
:root {
  /* Colors */
  --color-blue-500: #3b82f6;
  --color-white: #ffffff;

  /* Spacing */
  --spacing-3: 0.75rem;
  --spacing-4: 1rem;
  --spacing-6: 1.5rem;

  /* Border radius */
  --radius-md: 0.375rem;
  --radius-lg: 0.5rem;

  /* Shadows */
  --shadow-sm: 0 2px 4px rgba(0,0,0,0.1);
}
```

**Refactored CSS:**
```css
.button {
  background: var(--color-blue-500);
  padding: var(--spacing-3) var(--spacing-6);
  font-size: var(--spacing-4);
  border-radius: var(--radius-md);
}

.card {
  background: var(--color-white);
  padding: var(--spacing-6);
  border-radius: var(--radius-lg);
  box-shadow: var(--shadow-sm);
}
```

### 3. Convert Formats

Convert tokens between different formats.

**Supported Formats:**
- CSS Custom Properties
- Sass variables
- JavaScript/TypeScript
- JSON
- Style Dictionary

**Example Conversion:**

**CSS → Sass:**
```css
/* Input: tokens.css */
:root {
  --color-primary: #3b82f6;
  --spacing-4: 1rem;
}
```

```scss
// Output: tokens.scss
$color-primary: #3b82f6;
$spacing-4: 1rem;

// Map format
$colors: (
  'primary': #3b82f6,
);

$spacing: (
  '4': 1rem,
);
```

**CSS → JavaScript:**
```javascript
// Output: tokens.js
export const tokens = {
  color: {
    primary: '#3b82f6'
  },
  spacing: {
    4: '1rem'
  }
};
```

**CSS → JSON:**
```json
{
  "color": {
    "primary": {
      "value": "#3b82f6",
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

### 4. Apply Tokens

Apply existing tokens to CSS files.

**What I'll do:**
1. Scan CSS for hardcoded values
2. Match values to available tokens
3. Replace with token references
4. Generate report of changes

**Example:**

**Before:**
```css
.header {
  background: #3b82f6;
  padding: 1rem 2rem;
  color: #ffffff;
}
```

**After:**
```css
.header {
  background: var(--color-primary);
  padding: var(--spacing-4) var(--spacing-8);
  color: var(--color-white);
}
```

### 5. Audit Tokens

Analyze token usage across project.

**Audit Report:**
```markdown
# Token Usage Audit

## Summary
- Total tokens: 85
- Used tokens: 62 (73%)
- Unused tokens: 23 (27%)
- Hardcoded values: 34

## Unused Tokens
- --color-teal-500 (never used)
- --spacing-9 (never used)
- --shadow-2xl (never used)

## Hardcoded Values Still Present
- #3b82f6 in styles/legacy.css:45 → Use --color-primary
- 1rem in styles/card.css:23 → Use --spacing-4
- 2rem in styles/layout.css:89 → Use --spacing-8

## Token Consistency Issues
- --color-primary used 45 times ✓
- --color-secondary used 3 times ⚠️ (underutilized)
- Direct blue values: 12 instances (should use tokens)

## Recommendations
1. Remove 23 unused tokens
2. Replace 34 hardcoded values with tokens
3. Consider adding tokens for repeated values
```

### 6. Sync from Design Tools

Sync tokens from Figma, Sketch, or design token files.

**Supported Sources:**
- Figma (via API or Tokens Studio plugin)
- Sketch (via Style Dictionary)
- Design Token Format (W3C spec)
- Style Dictionary JSON

## Token Naming Convention

I follow this pattern: `[category]-[property]-[variant]-[state]`

```css
/* Color tokens */
--color-primary             /* Brand primary */
--color-primary-hover       /* Hover state */
--color-text-primary        /* Primary text */

/* Spacing tokens */
--spacing-4                 /* Base size */
--spacing-md                /* Semantic size */

/* Component tokens */
--button-padding-x          /* Horizontal padding */
--button-bg-primary         /* Primary button background */
```

## Token Architecture

### Three-Layer System

```
Layer 1: Global (Foundation)
  Raw values: #3b82f6, 1rem, 16px

Layer 2: Semantic (Purpose)
  --color-primary, --spacing-md

Layer 3: Component (Usage)
  --button-bg-primary, --card-padding
```

### Benefits

✓ **Single source of truth** - Change once, apply everywhere
✓ **Consistency** - Same values across design system
✓ **Maintainability** - Easy to update themes
✓ **Documentation** - Self-documenting code
✓ **Themeing** - Easy dark mode, brand variations
✓ **Scalability** - Grows with project

## Examples

```bash
# Interactive mode
/css-tokens

# Generate new token system
/css-tokens generate

# Extract tokens from existing CSS
/css-tokens extract src/styles/**/*.css

# Convert CSS tokens to Sass
/css-tokens convert --from=css --to=sass

# Apply tokens to CSS files
/css-tokens apply src/components/**/*.css

# Audit token usage
/css-tokens audit

# Sync from Figma
/css-tokens sync --source=figma
```

## What You'll Get

Depending on the operation:

✓ **Token files** - Organized token definitions
✓ **Refactored CSS** - Using tokens instead of hardcoded values
✓ **Conversion scripts** - Multi-format token output
✓ **Usage reports** - Token utilization analysis
✓ **Documentation** - Token usage guidelines
✓ **Theme variations** - Light/dark themes ready

## Configuration

```javascript
// css-tokens.config.js
module.exports = {
  // Input/output paths
  input: 'src/styles/**/*.css',
  output: 'tokens/',

  // Naming convention
  prefix: '--',
  separator: '-',

  // Token categories
  categories: [
    'color',
    'spacing',
    'typography',
    'shadow',
    'radius',
    'transition'
  ],

  // Formats to generate
  formats: ['css', 'scss', 'js', 'json'],

  // Theme variations
  themes: ['light', 'dark', 'high-contrast']
};
```

---

Starting token operation...

Operation: `$1`
Options: `$2`

Let me help you manage your design tokens!
