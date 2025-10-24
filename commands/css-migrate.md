---
description: Migrate CSS between approaches, frameworks, or preprocessors with intelligent conversion wizard
allowed-tools: Read, Write, Edit, Glob, Grep, Bash
---

# CSS Migration Wizard

I'll help you migrate your CSS between different approaches, frameworks, methodologies, or preprocessors.

## Arguments

```bash
/css-migrate [source-type] [target-type]
```

**source-type**: Current CSS approach
**target-type**: Desired CSS approach

If omitted, I'll detect source and ask for target.

## Supported Migrations

### Preprocessor Migrations
- Sass/SCSS → CSS
- Less → Sass
- Sass → PostCSS
- Stylus → CSS

### Framework Migrations
- Bootstrap → Tailwind
- Material UI → Custom CSS
- Bulma → Custom CSS
- Foundation → Modern CSS

### Methodology Migrations
- Legacy CSS → BEM
- OOCSS → Atomic CSS
- No methodology → SMACSS/ITCSS

### CSS-in-JS Migrations
- Styled Components → Emotion
- CSS-in-JS → CSS Modules
- Inline styles → CSS-in-JS
- CSS-in-JS → Vanilla CSS

## Migration Process

### Phase 1: Analysis & Planning

I'll analyze your current setup:

1. **Detect source type** - What you're using now
2. **Assess scope** - Size and complexity
3. **Identify dependencies** - What relies on current CSS
4. **Find risk areas** - Complex components, critical pages
5. **Estimate effort** - Time and difficulty
6. **Create migration plan** - Step-by-step strategy

### Phase 2: Preparation

Before migration starts:

1. **Backup current files** - Safety first
2. **Set up coexistence** - Old and new can run together
3. **Create conversion guide** - Document patterns
4. **Set up testing** - Visual regression, automated tests
5. **Establish rollback plan** - Quick revert if needed

### Phase 3: Conversion

Incremental migration approach:

1. **Start with utilities** - Lowest-level styles first
2. **Convert components** - One at a time, test each
3. **Update layouts** - Page-level styles
4. **Migrate pages** - Route by route
5. **Remove old code** - Clean up after conversion

### Phase 4: Validation

Ensure everything works:

1. **Visual comparison** - Before/after screenshots
2. **Functional testing** - All interactions work
3. **Performance check** - No regressions
4. **Accessibility audit** - Maintain compliance
5. **Browser testing** - Cross-browser verification

## Example Migrations

### 1. Sass → Modern CSS

```scss
// BEFORE: Sass
$primary-color: #007bff;
$spacing-base: 1rem;

@mixin button-size($padding) {
  padding: $padding;
  font-size: $padding * 1.5;
}

.button {
  background: $primary-color;
  @include button-size(0.75rem);

  &:hover {
    background: darken($primary-color, 10%);
  }

  &--large {
    @include button-size(1rem);
  }
}
```

```css
/* AFTER: Modern CSS */
:root {
  --color-primary: #007bff;
  --color-primary-dark: #0056b3;
  --spacing-base: 1rem;
}

.button {
  --button-padding: 0.75rem;

  background: var(--color-primary);
  padding: var(--button-padding);
  font-size: calc(var(--button-padding) * 1.5);
}

.button:hover {
  background: var(--color-primary-dark);
}

.button--large {
  --button-padding: 1rem;
}
```

### 2. Bootstrap → Tailwind

```html
<!-- BEFORE: Bootstrap -->
<div class="container">
  <div class="row">
    <div class="col-md-6">
      <button class="btn btn-primary btn-lg">
        Click me
      </button>
    </div>
  </div>
</div>
```

```html
<!-- AFTER: Tailwind -->
<div class="container mx-auto px-4">
  <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
    <div>
      <button class="px-6 py-3 text-lg font-semibold text-white bg-blue-600 rounded hover:bg-blue-700">
        Click me
      </button>
    </div>
  </div>
</div>
```

### 3. Legacy CSS → BEM

```css
/* BEFORE: Legacy nested CSS */
.header {
  background: #333;
}

.header .nav {
  display: flex;
}

.header .nav ul {
  list-style: none;
}

.header .nav ul li a {
  color: white;
}

.header .nav ul li.active a {
  font-weight: bold;
}
```

```css
/* AFTER: BEM methodology */
.header {
  background: #333;
}

.header__nav {
  display: flex;
}

.nav__list {
  list-style: none;
}

.nav__link {
  color: white;
}

.nav__link--active {
  font-weight: bold;
}
```

### 4. Styled Components → CSS Modules

```javascript
// BEFORE: Styled Components
import styled from 'styled-components';

const Button = styled.button`
  padding: 0.75rem 1.5rem;
  background: ${props => props.primary ? '#007bff' : '#6c757d'};
  color: white;
  border: none;
  border-radius: 0.375rem;

  &:hover {
    background: ${props => props.primary ? '#0056b3' : '#5a6268'};
  }
`;

export default Button;
```

```css
/* AFTER: CSS Module (Button.module.css) */
.button {
  padding: 0.75rem 1.5rem;
  color: white;
  border: none;
  border-radius: 0.375rem;
}

.primary {
  background: #007bff;
}

.primary:hover {
  background: #0056b3;
}

.secondary {
  background: #6c757d;
}

.secondary:hover {
  background: #5a6268;
}
```

```javascript
// Button.jsx
import styles from './Button.module.css';

export default function Button({ primary, children }) {
  const className = `${styles.button} ${primary ? styles.primary : styles.secondary}`;
  return <button className={className}>{children}</button>;
}
```

## Migration Strategy Options

### 1. Big Bang (Not Recommended)
- Migrate everything at once
- High risk, difficult rollback
- Fast but dangerous

### 2. Incremental (Recommended)
- Migrate piece by piece
- Low risk, easy rollback
- Slower but safer
- Can release incrementally

### 3. Parallel Development
- Build new alongside old
- Feature flag switching
- Gradual user migration
- Safe but resource-intensive

## Coexistence Setup

Allow old and new to run together:

```javascript
// webpack.config.js
module.exports = {
  module: {
    rules: [
      {
        test: /\.legacy\.css$/,
        use: ['style-loader', 'css-loader']
      },
      {
        test: /\.module\.css$/,
        use: [
          'style-loader',
          {
            loader: 'css-loader',
            options: { modules: true }
          }
        ]
      }
    ]
  }
};
```

## Migration Checklist

### Pre-Migration
- [ ] Backup all CSS files
- [ ] Document current patterns
- [ ] Set up visual regression testing
- [ ] Create rollback plan
- [ ] Get stakeholder approval

### During Migration
- [ ] Follow chosen strategy (incremental/parallel)
- [ ] Test each component after conversion
- [ ] Maintain visual parity
- [ ] Document new patterns
- [ ] Update team on progress

### Post-Migration
- [ ] Remove old CSS files
- [ ] Update documentation
- [ ] Train team on new approach
- [ ] Set up linting for new methodology
- [ ] Monitor for issues

## Automated Conversion

I can automate:

✓ **Syntax conversion** - Sass → CSS, etc.
✓ **Class name updates** - Bootstrap → Tailwind mapping
✓ **Import updates** - New file paths
✓ **Config generation** - New build config

Requires manual review:
- Complex logic conversions
- Dynamic class generation
- Custom patterns
- Edge cases

## Testing Strategy

### Visual Regression
```bash
# BackstopJS
backstop test

# Percy
percy exec -- node snapshots.js
```

### Manual QA
- Test all pages/routes
- Check responsive breakpoints
- Verify interactive states
- Test browser compatibility
- Validate accessibility

## Examples

```bash
# Interactive migration wizard
/css-migrate

# Sass to CSS
/css-migrate sass css

# Bootstrap to Tailwind
/css-migrate bootstrap tailwind

# Legacy to BEM
/css-migrate legacy bem

# Styled Components to CSS Modules
/css-migrate styled-components css-modules
```

## Timeline Estimation

Small project (< 20 components):
- Analysis: 1-2 hours
- Setup: 2-3 hours
- Migration: 1-2 days
- Testing: 1 day
- Total: 3-4 days

Medium project (20-100 components):
- Analysis: 1 day
- Setup: 1 day
- Migration: 1-2 weeks
- Testing: 2-3 days
- Total: 2-3 weeks

Large project (> 100 components):
- Analysis: 2-3 days
- Setup: 1-2 days
- Migration: 3-8 weeks
- Testing: 1 week
- Total: 6-12 weeks

## Support & Guidance

Throughout migration, I'll:
- Provide pattern examples
- Answer questions
- Suggest best practices
- Help with edge cases
- Review converted code
- Troubleshoot issues

---

Starting migration analysis...

Current setup: `$1`
Target setup: `$2`

Let me analyze your project and create a migration plan.
