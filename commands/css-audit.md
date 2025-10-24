---
description: Full CSS audit covering performance, accessibility, best practices, and compatibility
allowed-tools: Read, Glob, Grep, Bash, WebFetch
---

# CSS Comprehensive Audit

I'll perform a complete audit of your CSS covering all aspects: performance, accessibility, best practices, browser compatibility, and code quality.

## Audit Scope

This is a comprehensive audit that examines:

✓ **Performance** - Bundle size, render speed, critical CSS
✓ **Accessibility** - WCAG 2.2 compliance, contrast, focus
✓ **Best Practices** - Code quality, methodology, maintainability
✓ **Browser Compatibility** - Cross-browser support, fallbacks
✓ **Security** - CSS injection risks, safe patterns

## Audit Categories

### 1. Performance Audit

**Metrics I'll Measure:**
- Bundle size (uncompressed, minified, gzipped)
- Unused CSS percentage
- Selector complexity
- Render-blocking resources
- Critical CSS opportunities
- Animation performance

**Performance Checks:**
- [ ] Bundle size < 50KB (gzipped)
- [ ] Unused CSS < 20%
- [ ] No universal selectors
- [ ] Animations use transform/opacity only
- [ ] Critical CSS identified and separated
- [ ] CSS loading optimized

### 2. Accessibility Audit (WCAG 2.2)

**Level A Checks:**
- [ ] Color not sole indicator of information
- [ ] All functionality keyboard accessible
- [ ] Skip navigation available
- [ ] No keyboard traps

**Level AA Checks:**
- [ ] Text contrast ≥ 4.5:1 (7:1 for AAA)
- [ ] Large text contrast ≥ 3:1
- [ ] UI components contrast ≥ 3:1
- [ ] Focus indicators visible
- [ ] Touch targets ≥ 44x44px
- [ ] Text can resize to 200%

**Level AAA Checks:**
- [ ] Text contrast ≥ 7:1
- [ ] Enhanced visual presentation
- [ ] No time limits on interactions

**Motion & Animation:**
- [ ] prefers-reduced-motion support
- [ ] No auto-playing animations
- [ ] No flashing content (seizure risk)
- [ ] Parallax warnings

### 3. Best Practices Audit

**Code Quality:**
- [ ] Consistent naming convention
- [ ] Appropriate methodology (BEM, etc.)
- [ ] Low specificity (average < 30)
- [ ] Minimal nesting depth (≤ 3 levels)
- [ ] No !important abuse
- [ ] Proper code organization

**Maintainability:**
- [ ] Clear file structure
- [ ] Documented complex logic
- [ ] No duplicate rules
- [ ] Modular, reusable patterns
- [ ] Version control friendly

**CSS Architecture:**
- [ ] Separation of concerns
- [ ] Scalable structure
- [ ] Clear component boundaries
- [ ] Proper cascade usage

### 4. Browser Compatibility

**Modern Features:**
- [ ] Feature queries for new CSS
- [ ] Appropriate vendor prefixes
- [ ] Fallbacks for unsupported features
- [ ] Progressive enhancement

**Testing:**
- [ ] Tested in Chrome
- [ ] Tested in Firefox
- [ ] Tested in Safari
- [ ] Tested in Edge
- [ ] Mobile browser testing

### 5. Security Audit

**CSS Injection Risks:**
- [ ] No user input in CSS
- [ ] Safe use of custom properties
- [ ] No expression() usage
- [ ] Proper escaping of special characters

## Audit Report Structure

### Executive Summary

```markdown
# CSS Audit Report

**Project**: [Project Name]
**Date**: [Date]
**Auditor**: Claude CSS Pro

## Overall Score: 72/100

### Grade: C+

**Summary**: The CSS has moderate quality with several areas for improvement.
Performance and accessibility need attention. Architecture is sound but requires
optimization.

### Critical Issues: 8
### Important Issues: 23
### Minor Issues: 45

### Top Priorities:
1. Fix color contrast failures (8 instances)
2. Remove unused CSS (estimated 120KB savings)
3. Add focus indicators to all interactive elements
4. Optimize expensive selectors (15 found)
5. Implement critical CSS strategy
```

### Detailed Findings

#### Performance: 65/100 🟡

```
Bundle Size Analysis:
- Current: 180KB (minified), 55KB (gzipped)
- Target: < 50KB (gzipped)
- Status: ⚠️ 10% over budget

Unused CSS:
- Unused: 45% (81KB)
- Status: 🔴 Critical - needs cleanup

Selector Performance:
- Average depth: 3.8
- Complex selectors: 15
- Universal selectors: 3
- Status: ⚠️ Needs optimization

Critical CSS:
- Above-fold CSS: ~40KB
- Currently inline: 0KB
- Status: 🔴 Not implemented

Recommendations:
1. Remove unused CSS (PurgeCSS)
2. Extract critical CSS (< 14KB)
3. Optimize expensive selectors
4. Load non-critical CSS async
```

#### Accessibility: 68/100 🟡

```
WCAG 2.2 Compliance:
- Level A: ✓ Pass (3/3 criteria)
- Level AA: ⚠️ Partial (5/8 criteria)
- Level AAA: ✗ Fail (2/6 criteria)

Color Contrast:
- Failing elements: 8
- Issues:
  * .text-muted: 2.85:1 (needs 4.5:1)
  * .caption: 3.2:1 (needs 4.5:1)
  * .button-outline: 3.9:1 (needs 4.5:1)

Focus Indicators:
- Missing: 12 elements
- Insufficient: 5 elements

Touch Targets:
- Too small (< 44px): 7 elements

Motion & Animation:
- prefers-reduced-motion: ✗ Not implemented
- Auto-playing: 2 animations

Recommendations:
1. Fix all color contrast failures
2. Add focus-visible indicators
3. Increase touch target sizes
4. Implement reduced motion support
```

#### Best Practices: 75/100 🟢

```
Code Quality:
- Naming consistency: ✓ Good (BEM used)
- Specificity: ⚠️ Some high specificity
- Nesting depth: ✓ Good (avg 2.3)
- !important usage: ⚠️ 18 instances

Maintainability:
- File organization: ✓ Good structure
- Documentation: ⚠️ Limited comments
- Duplicates: 12 duplicate rules
- Modularity: ✓ Good separation

Architecture:
- Methodology: ✓ BEM implemented
- Scalability: ✓ Good patterns
- Reusability: ✓ Component-based

Recommendations:
1. Reduce !important usage
2. Add more code comments
3. Remove duplicate rules
4. Flatten some high-specificity selectors
```

#### Browser Compatibility: 80/100 ✅

```
Modern Feature Usage:
- Container queries: ⚠️ No fallback
- :has() selector: ⚠️ No fallback
- CSS Grid: ✓ Has fallback
- Custom properties: ✓ Has fallback

Vendor Prefixes:
- Status: ✓ Autoprefixer configured
- Coverage: 98% browser support

Fallback Strategies:
- Feature queries: ✓ Used appropriately
- Progressive enhancement: ✓ Implemented

Browser Testing:
- Chrome: ✓ Tested
- Firefox: ✓ Tested
- Safari: ⚠️ Not tested
- Edge: ✓ Tested
- Mobile: ⚠️ Limited testing

Recommendations:
1. Add fallbacks for container queries
2. Test in Safari
3. Expand mobile browser testing
```

#### Security: 95/100 ✅

```
CSS Injection:
- User input in CSS: ✓ None found
- Expression() usage: ✓ None found
- Safe custom properties: ✓ Properly used

Recommendations:
- Current practices are secure
- Continue avoiding user input in CSS
```

### Priority Action Items

#### 🔴 Critical (Fix Immediately)
1. **Color Contrast Failures** - 8 elements fail WCAG AA
   - Impact: Accessibility
   - Effort: 2 hours
   - Fix: Update to darker/lighter colors

2. **Missing Focus Indicators** - 12 interactive elements
   - Impact: Accessibility, keyboard navigation
   - Effort: 3 hours
   - Fix: Add :focus-visible styles

3. **Unused CSS** - 45% unused (81KB)
   - Impact: Performance, bundle size
   - Effort: 4 hours
   - Fix: Configure PurgeCSS

#### 🟠 Important (Fix Soon)
1. **Critical CSS** - Not implemented
   - Impact: FCP, LCP performance
   - Effort: 6 hours
   - Fix: Extract and inline critical CSS

2. **Reduced Motion** - No support
   - Impact: Accessibility
   - Effort: 2 hours
   - Fix: Add @media (prefers-reduced-motion)

3. **Touch Targets** - 7 elements too small
   - Impact: Mobile usability
   - Effort: 3 hours
   - Fix: Increase min-width/height to 44px

#### 🟡 Minor (Consider Fixing)
1. **!important Usage** - 18 instances
   - Impact: Maintainability
   - Effort: 8 hours
   - Fix: Refactor specificity

2. **Duplicate Rules** - 12 found
   - Impact: Bundle size, maintainability
   - Effort: 3 hours
   - Fix: Consolidate duplicate CSS

### Timeline & Effort Estimate

**Total Estimated Effort: 31 hours (4 days)**

Week 1:
- Fix critical accessibility issues (8h)
- Remove unused CSS (4h)

Week 2:
- Implement critical CSS (6h)
- Fix touch targets and motion support (5h)

Week 3:
- Refactor !important usage (8h)

### Score Improvement Projection

With all fixes implemented:

Current: 72/100 (C+)
Projected: 88/100 (B+)

- Performance: 65 → 85
- Accessibility: 68 → 95
- Best Practices: 75 → 85
- Compatibility: 80 → 85
- Security: 95 → 95

---

Starting comprehensive audit...

Analyzing CSS files across all dimensions...
