---
description: Comprehensive CSS code review with best practices, accessibility, and performance analysis
allowed-tools: Read, Glob, Grep, Bash
---

# CSS Code Review

I'll perform a comprehensive review of your CSS, checking for best practices, accessibility, performance, and maintainability issues.

## Review Scope

Analyzing: `$ARGUMENTS`

If no specific files provided, I'll review all CSS files in the project.

## What I'll Check

### 1. **Code Quality & Organization**
- File structure and organization
- Naming conventions consistency
- Methodology adherence (BEM, OOCSS, etc.)
- Code duplication
- Selector specificity
- Code comments and documentation

### 2. **Accessibility (WCAG 2.2)**
- Color contrast ratios
- Focus indicators
- Text sizing and readability
- Screen reader compatibility
- Motion and animation accessibility
- Keyboard navigation support

### 3. **Performance**
- Bundle size analysis
- Selector efficiency
- Render-blocking issues
- Animation performance
- Unused CSS detection
- Critical CSS opportunities

### 4. **Browser Compatibility**
- Modern CSS feature usage
- Missing vendor prefixes
- Fallback strategies
- Feature query usage

### 5. **Best Practices**
- CSS architecture patterns
- Responsive design implementation
- Maintainability concerns
- Anti-patterns and code smells

## Review Process

1. **Scan all CSS files** - Identify files and analyze structure
2. **Run static analysis** - Check with Stylelint (if configured)
3. **Calculate metrics** - Specificity, complexity, bundle size
4. **Check accessibility** - Contrast ratios, focus styles
5. **Performance audit** - Expensive selectors, render triggers
6. **Generate report** - Prioritized findings with recommendations

## Report Format

I'll provide a detailed report with:

### Summary
- Overall assessment
- Total issues found
- Critical issues count
- Quick wins

### Issues by Priority

**🔴 CRITICAL** - Must fix (security, accessibility blockers)
- Issue description
- Location (file:line)
- Why it's critical
- How to fix

**🟠 IMPORTANT** - Should fix (performance, best practices)
- Issue description
- Impact analysis
- Recommended solution

**🟡 MINOR** - Consider fixing (code quality, maintainability)
- Suggestion
- Benefit of fixing
- Optional improvement

**✅ GOOD** - Positive aspects to highlight
- What's done well
- Patterns to maintain

### Metrics

```
Bundle Size: 150KB → Target: <50KB (gzipped)
Unused CSS: 45% → Target: <20%
Avg Selector Depth: 4.2 → Target: <3
Specificity Issues: 23 found
Accessibility Issues: 5 critical, 12 warnings
Performance Warnings: 8 found
```

### Recommendations

Prioritized action items:
1. Remove unused CSS
2. Fix critical accessibility issues
3. Optimize expensive selectors
4. Improve naming consistency
5. Add documentation

## Arguments

```bash
/css-review [file-pattern]
```

**file-pattern** (optional):
- Specific file: `styles/button.css`
- Pattern: `components/**/*.css`
- Multiple: `src/**/*.{css,scss}`
- (omit to review all CSS files)

## Examples

```bash
# Review all CSS files
/css-review

# Review specific directory
/css-review src/components

# Review specific file
/css-review styles/main.css

# Review with pattern
/css-review "src/**/*.module.css"
```

## Post-Review Actions

After the review, I can:
- Fix issues automatically (where safe)
- Create a TODO list of manual fixes
- Generate a refactoring plan
- Set up linting to prevent future issues
- Create a style guide document

---

Starting review now for: `$ARGUMENTS`

Let me analyze your CSS...
