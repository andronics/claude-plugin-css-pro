---
description: Optimize CSS performance, reduce bundle size, and improve rendering
allowed-tools: Read, Write, Edit, Glob, Grep, Bash
---

# CSS Performance Optimization

I'll analyze and optimize your CSS for better performance, smaller bundle size, and faster rendering.

## Target Files

Optimizing: `$ARGUMENTS`

If no specific files provided, I'll optimize all CSS files in the project.

## Optimization Strategy

### Phase 1: Analysis
I'll first analyze your CSS to identify optimization opportunities:

1. **Bundle Size Analysis**
   - Current size (uncompressed, minified, gzipped)
   - Unused CSS detection
   - Duplicate rule identification
   - Optimization potential calculation

2. **Performance Audit**
   - Selector complexity analysis
   - Render-blocking detection
   - Critical CSS identification
   - Animation performance check

3. **Opportunity Assessment**
   - Prioritize optimizations by impact
   - Estimate size savings
   - Calculate performance improvements

### Phase 2: Optimization

Based on analysis, I'll apply these optimizations:

#### 1. Remove Unused CSS
```
Tool: PurgeCSS / Manual analysis
Expected savings: 30-70% of bundle size

Actions:
- Scan HTML/JS/templates for used classes
- Remove unused rules
- Keep safelist patterns (dynamic classes)
```

#### 2. Eliminate Duplicates
```
Expected savings: 5-15% of bundle size

Actions:
- Find duplicate rules
- Merge identical selectors
- Extract common patterns
```

#### 3. Optimize Selectors
```
Performance impact: 20-50% faster style calculation

Actions:
- Reduce selector depth (max 3 levels)
- Remove universal selectors
- Simplify attribute selectors
- Flatten deeply nested rules
```

#### 4. Minify & Compress
```
Expected savings: 60-80% with gzip

Actions:
- Remove whitespace and comments
- Shorten color values (#ffffff → #fff)
- Combine similar rules
- Optimize property values
```

#### 5. Extract Critical CSS
```
Performance impact: 1-2s faster FCP

Actions:
- Identify above-the-fold styles
- Extract critical CSS (< 14KB)
- Set up async loading for remaining CSS
```

#### 6. Optimize Animations
```
Performance impact: Smooth 60fps animations

Actions:
- Convert layout-triggering to transform/opacity
- Add will-change appropriately
- Remove/limit expensive properties
```

#### 7. Split Bundles
```
Expected result: Route-based loading, better caching

Actions:
- Separate vendor from custom CSS
- Split by route/feature
- Create common chunk
```

## What I'll Create

After optimization, you'll have:

✓ **Optimized CSS files** - Reduced, efficient styles
✓ **Critical CSS** - Inline-ready critical styles
✓ **Split bundles** - Separate files for better loading
✓ **Build configuration** - PostCSS/build tool setup
✓ **Performance report** - Before/after metrics
✓ **Documentation** - Optimization decisions explained

## Configuration Files

I may create/update:

```javascript
// postcss.config.js
module.exports = {
  plugins: [
    require('postcss-import'),
    require('autoprefixer'),
    require('cssnano')({
      preset: ['advanced', {
        discardComments: { removeAll: true },
      }]
    })
  ]
}

// purgecss.config.js
module.exports = {
  content: ['./src/**/*.{html,js,jsx,tsx}'],
  safelist: ['active', 'open', /^js-/]
}
```

## Metrics Tracking

I'll track these metrics:

### Before → After

**Bundle Size:**
```
Uncompressed: 250KB → 80KB (68% reduction)
Minified:     180KB → 60KB (67% reduction)
Gzipped:      45KB  → 15KB (67% reduction)
```

**Performance:**
```
First Contentful Paint:  3.2s → 1.5s (↓ 1.7s)
Largest Contentful Paint: 4.5s → 2.2s (↓ 2.3s)
Unused CSS:              65%  → 12%  (↓ 53%)
Avg Selector Depth:      4.8  → 2.1  (↓ 2.7)
```

**Code Quality:**
```
Total Rules:      1,250 → 420 (66% reduction)
Duplicate Rules:    87  → 0   (100% removed)
Complex Selectors:  45  → 8   (82% reduced)
```

## Arguments

```bash
/css-optimize [file-pattern] [--options]
```

**file-pattern** (optional):
- Specific file: `dist/styles.css`
- Pattern: `src/**/*.css`
- (omit to optimize all CSS files)

**options** (optional):
- `--aggressive` - Maximum optimization (may need testing)
- `--safe` - Conservative optimization (no breaking changes)
- `--critical` - Extract critical CSS only
- `--analyze` - Analysis only, no changes

## Examples

```bash
# Optimize all CSS files
/css-optimize

# Optimize specific file
/css-optimize dist/bundle.css

# Aggressive optimization
/css-optimize --aggressive

# Analysis only (no changes)
/css-optimize --analyze

# Extract critical CSS
/css-optimize --critical
```

## Safety & Rollback

### Safety Measures
- Backup original files before modification
- Apply optimizations incrementally
- Run visual regression tests (if available)
- Validate CSS after optimization

### Rollback Plan
If issues occur:
1. Restore from backup
2. Apply optimizations selectively
3. Adjust configuration
4. Re-run with --safe flag

## Post-Optimization

After optimization, I'll:

1. **Validate** - Ensure CSS is valid and working
2. **Test** - Check critical pages/components
3. **Measure** - Confirm performance improvements
4. **Document** - Explain changes and new workflow
5. **Configure CI** - Set up build-time optimization

---

Starting optimization for: `$ARGUMENTS`

Let me analyze your CSS and create an optimization plan...
