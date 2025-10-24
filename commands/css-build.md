---
description: Build and compile CSS with comprehensive error analysis and optimization
allowed-tools: Read, Write, Glob, Grep, Bash
---

# CSS Build & Compile

I'll build and compile your CSS with error analysis, optimization, and detailed reporting.

## Arguments

```bash
/css-build [--options]
```

**options**:
- `--watch` - Watch mode for development
- `--production` - Production build with optimization
- `--analyze` - Generate bundle analysis report
- `--sourcemaps` - Generate source maps
- (omit for standard build)

## Build Process

### Phase 1: Pre-Build Validation

**Checks Before Building:**
1. ✓ Validate CSS syntax
2. ✓ Check for missing dependencies
3. ✓ Verify configuration files
4. ✓ Lint CSS files (if configured)
5. ✓ Check for breaking changes

### Phase 2: Compilation

**What Gets Compiled:**

#### Preprocessors
```bash
# Sass/SCSS
sass src/styles/main.scss dist/styles.css

# Less
lessc src/styles/main.less dist/styles.css

# Stylus
stylus src/styles/main.styl -o dist/
```

#### PostCSS Pipeline
```javascript
// postcss.config.js
module.exports = {
  plugins: [
    require('postcss-import'),           // Combine @import files
    require('postcss-nested'),           // Unwrap nested rules
    require('autoprefixer'),             // Add vendor prefixes
    require('postcss-preset-env')({      // Use future CSS
      stage: 3,
      features: {
        'nesting-rules': true,
        'custom-properties': true
      }
    }),
    require('cssnano')({                 // Minify
      preset: ['advanced', {
        discardComments: { removeAll: true }
      }]
    })
  ]
}
```

### Phase 3: Optimization

**Development Build:**
- Source maps enabled
- No minification
- Fast rebuild times
- Readable output

**Production Build:**
- Minification
- Vendor prefixes
- Dead code elimination
- Compression (gzip/brotli)
- Cache busting
- Bundle splitting

### Phase 4: Validation & Reporting

**Post-Build Checks:**
- ✓ CSS validity
- ✓ File size analysis
- ✓ Compression ratios
- ✓ Build time metrics
- ✓ Error summary

## Build Output

### Development Build

```bash
Building CSS...

✓ Compiled: src/styles/main.scss → dist/styles.css
✓ Generated source maps
✓ Build completed in 324ms

Output:
  dist/styles.css         85KB
  dist/styles.css.map     42KB

Watching for changes...
```

### Production Build

```bash
Building CSS for production...

✓ Compiled SCSS files
✓ Applied PostCSS transformations
✓ Added vendor prefixes
✓ Minified CSS
✓ Generated compressed versions

Build Summary:
  Original:       250KB (100%)
  Minified:       180KB (72%)
  Gzipped:        45KB  (18%)
  Brotli:         38KB  (15%)

Output Files:
  dist/styles.css           180KB
  dist/styles.css.gz        45KB
  dist/styles.css.br        38KB
  dist/styles.css.map       95KB

Build time: 2.8s
✓ Build successful!
```

### Build with Errors

```bash
Building CSS...

✗ Build failed!

Errors (3):

styles/button.scss:45:12
  ✗ Unexpected token, expected "}"
    43 | .button {
    44 |   padding: 1rem
  > 45 |   color: blue
       |             ^
    46 | }

styles/card.scss:12:3
  ✗ Undefined variable $spacing-lg
    10 | .card {
    11 |   background: white;
  > 12 |   padding: $spacing-lg;
       |            ^^^^^^^^^^^
    13 | }

styles/nav.scss:8:1
  ✗ Invalid property value
    7 | .nav {
  > 8 |   display: flexbox;
      |   ^^^^^^^^^^^^^^^^^
    9 | }

Warnings (2):

styles/legacy.scss:34:5
  ⚠ Using !important may indicate specificity issues
    34 |   color: red !important;

styles/global.scss:89:1
  ⚠ Universal selector (*) may impact performance
    89 | * { box-sizing: border-box; }

Build failed with 3 errors, 2 warnings.
```

## Watch Mode

```bash
/css-build --watch

Watching for changes in src/**/*.{css,scss,sass}

✓ Initial build completed (324ms)

[10:23:45] File changed: src/styles/button.scss
[10:23:45] Rebuilding...
[10:23:46] ✓ Build completed (128ms)

[10:24:12] File changed: src/styles/card.scss
[10:24:12] Rebuilding...
[10:24:12] ✓ Build completed (95ms)

Press Ctrl+C to stop watching
```

## Bundle Analysis

```bash
/css-build --analyze

Building and analyzing CSS bundle...

Bundle Composition:

Total: 180KB (minified)

By Category:
  Base/Reset:      15KB  (8%)
  Typography:      12KB  (7%)
  Components:      85KB  (47%)
  Layouts:         28KB  (16%)
  Utilities:       25KB  (14%)
  Vendor:          15KB  (8%)

Top 10 Largest Components:
  1. Modal:        12KB
  2. DataTable:    10KB
  3. Calendar:     8KB
  4. Dropdown:     6KB
  5. Carousel:     5KB
  6. Tabs:         4KB
  7. Accordion:    4KB
  8. Tooltip:      3KB
  9. Badge:        2KB
  10. Alert:       2KB

Opportunities:
  - Remove unused utilities (estimated 8KB)
  - Simplify Modal component (overly complex)
  - Consider lazy-loading Calendar (rarely used)

Detailed analysis saved to: dist/css-analysis.html
```

## Configuration Detection

I'll automatically detect and use:

### Sass Configuration
```scss
// sass.config.js or in package.json
{
  "includePaths": ["node_modules"],
  "outputStyle": "compressed",
  "sourceMap": true
}
```

### PostCSS Configuration
```javascript
// postcss.config.js
module.exports = {
  plugins: [
    // Auto-detected plugins
  ]
}
```

### Build Tools
- **Webpack**: Uses webpack config
- **Vite**: Uses vite.config
- **Parcel**: Auto-configuration
- **Gulp**: Uses gulpfile
- **npm scripts**: Uses package.json scripts

## Error Handling

### Common Errors & Solutions

**1. Missing Semicolon**
```
Error: Unexpected token }
Fix: Add semicolon at end of declaration
```

**2. Undefined Variable**
```
Error: Undefined variable $color-primary
Fix: Import variables file or define variable
```

**3. Invalid Property**
```
Error: Unknown property "colour"
Fix: Use correct spelling "color"
```

**4. Missing Import**
```
Error: File to import not found: variables
Fix: Check file path and extension
```

**5. Syntax Error in Nested Rules**
```
Error: Unexpected "{"
Fix: Check nesting syntax and braces
```

## Build Optimization Tips

### Speed Up Builds

**Development:**
```javascript
{
  "sourceMap": "cheap-source-map",  // Faster source maps
  "minify": false,                  // Skip minification
  "autoprefixer": false,            // Skip in dev
}
```

**Production:**
```javascript
{
  "parallel": true,                 // Parallel processing
  "cache": true,                    // Cache compiled files
  "incremental": true,              // Only rebuild changed
}
```

### Reduce Bundle Size

1. Remove unused CSS (PurgeCSS)
2. Split critical from non-critical
3. Tree-shake vendor CSS
4. Use CSS Modules for scoping
5. Minify and compress

## CI/CD Integration

### GitHub Actions
```yaml
name: Build CSS
on: [push, pull_request]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - run: npm install
      - run: npm run build:css
      - run: npm run analyze:css
```

### Build Scripts
```json
{
  "scripts": {
    "build:css": "postcss src/**/*.css --dir dist/",
    "build:css:prod": "NODE_ENV=production npm run build:css",
    "build:css:watch": "npm run build:css -- --watch",
    "analyze:css": "webpack-bundle-analyzer stats.json"
  }
}
```

## Examples

```bash
# Standard build
/css-build

# Watch mode for development
/css-build --watch

# Production build with optimization
/css-build --production

# Build and analyze bundle
/css-build --analyze

# Production build with source maps
/css-build --production --sourcemaps
```

## Post-Build Actions

After successful build:

✓ **Validate output** - Check generated CSS
✓ **Run tests** - Visual regression, unit tests
✓ **Generate reports** - Size, composition, coverage
✓ **Update documentation** - Build stats, changes
✓ **Deploy** - Copy to appropriate location

---

Starting build...

Arguments: `$ARGUMENTS`

Detecting build configuration...
