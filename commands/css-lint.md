---
description: Lint and validate CSS files with configurable rules
allowed-tools: Read, Write, Glob, Grep, Bash
---

# CSS Linting

I'll lint your CSS files to catch errors, enforce coding standards, and ensure best practices.

## Target Files

Linting: `$ARGUMENTS`

If no specific files provided, I'll lint all CSS files in the project.

## Linting Capabilities

### What I Check

#### 1. **Syntax Errors**
- Invalid CSS syntax
- Malformed selectors
- Incorrect property values
- Missing semicolons/braces
- Invalid color formats

#### 2. **Best Practices**
- Naming conventions (BEM, camelCase, kebab-case)
- Selector specificity limits
- Nesting depth limits
- Property order
- Shorthand usage

#### 3. **Potential Bugs**
- Duplicate selectors
- Overqualified selectors
- Vendor prefix issues
- Known browser bugs
- !important overuse

#### 4. **Performance**
- Universal selectors
- Expensive selectors
- Large file sizes
- Too many rules
- Render-blocking issues

#### 5. **Accessibility**
- Color contrast warnings
- Focus style requirements
- Text sizing issues
- Motion preferences

#### 6. **Compatibility**
- Browser support warnings
- Missing vendor prefixes
- Unsupported properties
- Feature query suggestions

## Linting Tools

### Stylelint (Recommended)

I'll use Stylelint with appropriate configurations:

```javascript
// .stylelintrc.js
module.exports = {
  extends: [
    'stylelint-config-standard',
    'stylelint-config-recommended'
  ],
  rules: {
    // Naming
    'selector-class-pattern': '^[a-z][a-z0-9-]*(__[a-z0-9-]+)?(--[a-z0-9-]+)?$',

    // Specificity
    'selector-max-id': 0,
    'selector-max-specificity': '0,4,0',
    'selector-max-compound-selectors': 3,

    // Best practices
    'declaration-no-important': true,
    'selector-no-qualifying-type': true,
    'shorthand-property-no-redundant-values': true,

    // Performance
    'selector-max-universal': 0,
    'selector-max-type': 2,

    // Order
    'order/properties-alphabetical-order': true,

    // Accessibility
    'a11y/media-prefers-reduced-motion': true,
    'a11y/no-outline-none': true,
  }
};
```

## Lint Report Format

### Summary
```
✓ 125 rules passed
✗ 18 errors found
⚠ 34 warnings found

Files linted: 42
Time: 1.2s
```

### Issues by Severity

#### Errors 🔴 (Must Fix)
```
styles/button.css
  12:3  ✗  Unexpected invalid hex color "#gggggg"  color-no-invalid-hex
  24:5  ✗  Expected "color" before "background"    order/properties-order

styles/card.css
  8:1   ✗  Unexpected duplicate selector ".card"   no-duplicate-selectors
  15:10 ✗  Unexpected !important                   declaration-no-important
```

#### Warnings ⚠️ (Should Fix)
```
styles/nav.css
  5:3   ⚠  Expected class selector to match BEM    selector-class-pattern
  18:1  ⚠  Expected selector depth ≤ 3 levels     selector-max-compound-selectors

styles/layout.css
  23:3  ⚠  Unexpected qualifying type selector     selector-no-qualifying-type
```

### Statistics
```
Top Issues:
- selector-max-compound-selectors: 12 violations
- declaration-no-important: 8 violations
- color-no-invalid-hex: 5 violations
- selector-class-pattern: 4 violations

Files with Most Issues:
1. styles/legacy.css (23 issues)
2. styles/vendor.css (15 issues)
3. styles/global.css (9 issues)
```

## Auto-Fix Capabilities

I can automatically fix:

✓ **Formatting** - Whitespace, indentation, line breaks
✓ **Property order** - Alphabetical or logical ordering
✓ **Color formats** - Consistent hex, rgb, hsl
✓ **Quotes** - Single vs double quotes
✓ **Semicolons** - Add missing semicolons
✓ **Shorthand** - Convert to shorthand properties

Cannot auto-fix (manual review needed):
- Specificity issues
- !important usage
- Duplicate selectors
- Logic errors

## Linting Modes

### 1. Check Mode (Default)
- Report issues only
- No file modifications
- Exit code indicates pass/fail

### 2. Fix Mode
- Auto-fix fixable issues
- Report unfixable issues
- Modify files in place

### 3. Report Mode
- Detailed report generation
- Export to JSON/HTML
- CI/CD integration

## Configuration Options

### Strictness Levels

**Strict:**
```javascript
{
  'selector-max-id': 0,
  'declaration-no-important': true,
  'selector-max-specificity': '0,3,0',
  'max-nesting-depth': 2
}
```

**Moderate (Default):**
```javascript
{
  'selector-max-id': 1,
  'declaration-no-important': [true, { severity: 'warning' }],
  'selector-max-specificity': '0,4,0',
  'max-nesting-depth': 3
}
```

**Lenient:**
```javascript
{
  'selector-max-id': 2,
  'declaration-no-important': [true, { severity: 'warning' }],
  'selector-max-specificity': '0,5,0',
  'max-nesting-depth': 4
}
```

## Integration

### VS Code
```json
{
  "stylelint.enable": true,
  "stylelint.validate": ["css", "scss", "sass"],
  "editor.codeActionsOnSave": {
    "source.fixAll.stylelint": true
  }
}
```

### Pre-commit Hook
```bash
#!/bin/sh
# .git/hooks/pre-commit
npx stylelint "**/*.css" --fix
```

### CI/CD
```yaml
# .github/workflows/lint.yml
name: Lint CSS
on: [push, pull_request]
jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - run: npm install
      - run: npm run lint:css
```

## Arguments

```bash
/css-lint [file-pattern] [--options]
```

**file-pattern** (optional):
- Specific file: `styles/button.css`
- Pattern: `src/**/*.css`
- (omit to lint all CSS files)

**options** (optional):
- `--fix` - Auto-fix fixable issues
- `--strict` - Use strict rules
- `--lenient` - Use lenient rules
- `--format=json` - Output format (json, html, markdown)
- `--quiet` - Only show errors (hide warnings)

## Examples

```bash
# Lint all CSS files
/css-lint

# Lint specific directory
/css-lint src/components

# Lint and auto-fix
/css-lint --fix

# Strict linting
/css-lint --strict

# JSON output for CI
/css-lint --format=json

# Errors only
/css-lint --quiet
```

## Setup Workflow

If Stylelint isn't configured, I'll:

1. **Detect project type** - React, Vue, vanilla, etc.
2. **Install dependencies** - Stylelint and appropriate configs
3. **Create configuration** - .stylelintrc.js with rules
4. **Add npm scripts** - lint:css, lint:css:fix
5. **Configure editor** - VS Code settings
6. **Set up git hooks** - Pre-commit linting (optional)
7. **Run initial lint** - Show current issues

## Ignoring Files

Create `.stylelintignore`:
```
# Dependencies
node_modules/
vendor/

# Build output
dist/
build/

# Legacy code (fix separately)
legacy/

# Minified files
**/*.min.css
```

## Post-Linting Actions

After linting, I can:

- **Fix issues automatically** (where safe)
- **Create TODO list** of manual fixes
- **Generate report** for team review
- **Set up CI integration** - Fail builds on errors
- **Configure editor integration** - Real-time linting

---

Starting lint for: `$ARGUMENTS`

Analyzing CSS files...
