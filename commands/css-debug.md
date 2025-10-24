---
description: Debug CSS issues including specificity conflicts, cascade problems, and layout bugs
allowed-tools: Read, Write, Edit, Glob, Grep
---

# CSS Debugging Assistant

I'll help you debug CSS issues systematically using proven techniques and tools.

## What's the Problem?

Describe your CSS issue: `$ARGUMENTS`

If no description provided, I'll ask diagnostic questions.

## Common CSS Issues I Can Debug

### 1. **Layout Problems**
- Flexbox not working
- Grid items overflowing
- Collapsed container height
- Centering not working
- Unexpected wrapping

### 2. **Specificity Conflicts**
- Styles not applying
- Rules being overridden
- !important issues
- Cascade problems

### 3. **Visual Bugs**
- Elements overlapping
- Z-index not working
- Positioning issues
- Gap/spacing problems

### 4. **Responsive Issues**
- Media queries not triggering
- Mobile layout broken
- Container queries not working

### 5. **Browser Compatibility**
- Works in Chrome, broken in Safari
- Vendor prefix missing
- Feature not supported

## Debugging Process

### Step 1: Information Gathering

I'll ask:
1. **What's the expected behavior?**
2. **What's actually happening?**
3. **When does it occur?** (viewport size, browser, etc.)
4. **Which element(s) are affected?**
5. **Can you share the CSS code?**

### Step 2: Systematic Analysis

I'll check:
- ✓ CSS syntax validity
- ✓ Selector specificity
- ✓ Cascade order
- ✓ Box model values
- ✓ Display properties
- ✓ Positioning context
- ✓ Z-index stacking
- ✓ Browser DevTools computed values

### Step 3: Root Cause Identification

Using elimination:
1. Remove styles until problem disappears
2. Add back one at a time
3. Identify the specific rule causing the issue
4. Understand why it's causing the problem

### Step 4: Solution & Fix

Provide:
- **Root cause explanation**
- **Specific fix with code**
- **Why the fix works**
- **How to prevent in future**

## Example Debugging Sessions

### Example 1: "My flexbox isn't working!"

**Your code:**
```css
.container {
  display: flex;
}

.item {
  width: 100%;
}
```

**Problem:** Items not growing/shrinking as expected

**Analysis:**
- `width: 100%` prevents flex-grow from working
- Flex items have `min-width: auto` by default
- Content width determines minimum size

**Solution:**
```css
.container {
  display: flex;
}

.item {
  flex: 1;      /* Allow growing */
  min-width: 0; /* Allow shrinking below content size */
  /* Remove width: 100% */
}
```

**Explanation:** Using `flex: 1` instead of `width: 100%` allows flex properties to work properly. `min-width: 0` allows items to shrink below their content size.

### Example 2: "This style won't apply!"

**Your code:**
```css
.button {
  background: blue;  /* Not applying! */
}
```

**Found in DevTools:**
```css
/* Higher specificity */
nav .menu .button {
  background: red;  /* This wins */
}
```

**Specificity Analysis:**
```
.button              → (0,0,1,0)
nav .menu .button    → (0,0,3,0) ← Wins
```

**Solutions:**

**Option 1: Increase specificity**
```css
.nav .menu .button--primary {
  background: blue;
}
```

**Option 2: Use :where() for lower specificity (recommended)**
```css
:where(nav .menu) .button {
  background: red;  /* (0,0,1,0) - same as .button alone */
}
```

**Option 3: Refactor to flat BEM (best)**
```css
.button {
  background: red;
}

.button--primary {
  background: blue;
}
```

### Example 3: "Centering doesn't work!"

**Your code:**
```css
.element {
  margin: 0 auto;  /* Not centering! */
}
```

**Problem:** No width defined

**Solution:**
```css
.element {
  margin: 0 auto;
  width: 50%;        /* or max-width: 600px; */
}
```

**Why:** `margin: 0 auto` only works when element has a defined width less than its container.

### Example 4: "Z-index not working!"

**Your code:**
```css
.element {
  z-index: 9999;  /* Still behind other elements! */
}
```

**Problem:** Element not positioned

**Solution:**
```css
.element {
  position: relative;  /* or absolute, fixed, sticky */
  z-index: 9999;
}
```

**Why:** `z-index` only works on positioned elements (not static).

### Example 5: "Container has zero height!"

**Your code:**
```css
.container {
  /* Children are floated or absolutely positioned */
}
```

**Modern Solution:**
```css
.container {
  display: flex;  /* or grid */
  /* Flex/grid containers don't collapse */
}
```

**Legacy Solution (for floats):**
```css
.container::after {
  content: '';
  display: table;
  clear: both;
}
```

## Debugging Tools & Techniques

### Browser DevTools

**Chrome/Edge DevTools:**
```
1. Inspect element (right-click → Inspect)
2. Styles tab:
   - See applied rules
   - Crossed-out = overridden
   - Click checkbox to toggle rules
   - Edit values live
3. Computed tab:
   - Final calculated values
   - Which rule each property came from
4. Layout tab:
   - Box model visualization
   - Grid/Flexbox overlays
```

**Firefox DevTools:**
```
- Excellent Grid inspector
- Shows specificity values
- Layout debugging tools
- Inactive CSS warnings
```

### Visual Debugging

**Outline Everything:**
```css
* {
  outline: 1px solid red !important;
}
```

**Specific Area:**
```css
.problem-area * {
  outline: 1px solid red !important;
}
```

### Specificity Calculator

```
Calculate specificity for:
#header .nav .item a:hover

Breakdown:
- IDs: 1 (#header)
- Classes: 3 (.nav, .item, :hover)
- Elements: 1 (a)

Result: (0,1,3,1)
```

## Common Issue Checklist

### Layout Issues
- [ ] Check `display` property
- [ ] Verify `width`/`height` values
- [ ] Inspect box model (margin, padding, border)
- [ ] Check `overflow` property
- [ ] Verify parent container setup

### Styles Not Applying
- [ ] Check selector specificity
- [ ] Verify cascade order
- [ ] Look for !important conflicts
- [ ] Check for typos in property names
- [ ] Validate property values

### Positioning Issues
- [ ] Check `position` property
- [ ] Verify positioning context (parent)
- [ ] Check `top`, `right`, `bottom`, `left` values
- [ ] Inspect `z-index` and stacking context

### Responsive Issues
- [ ] Check viewport meta tag
- [ ] Verify media query syntax
- [ ] Check breakpoint values
- [ ] Test with browser DevTools device mode

## Debugging Workflow

### 1. Reproduce the Issue
- Identify when it happens
- Note the conditions
- Try to trigger consistently

### 2. Isolate the Problem
- Create minimal test case
- Remove unrelated code
- Use browser DevTools

### 3. Form Hypothesis
- What might be causing this?
- What properties are involved?
- Is it specificity, cascade, or logic?

### 4. Test Solution
- Apply potential fix
- Verify issue resolved
- Check for side effects

### 5. Document & Prevent
- Add comments explaining fix
- Update conventions
- Add linting rules if needed

## Examples

```bash
# General debugging help
/css-debug

# Specific issue
/css-debug "My flexbox items won't wrap"

# Layout problem
/css-debug "Container has no height"

# Specificity issue
/css-debug "Button background won't change"

# Responsive issue
/css-debug "Mobile layout is broken"
```

## What I'll Provide

For your issue:

✓ **Root cause explanation** - Why it's happening
✓ **Specific fix** - Exact code to solve it
✓ **Why it works** - Understanding the solution
✓ **Prevention tips** - Avoid this in future
✓ **Alternative approaches** - Other ways to solve it
✓ **Browser DevTools guide** - How to debug yourself

---

Let's debug your CSS issue!

Issue description: `$ARGUMENTS`

Tell me what's wrong, and I'll help you fix it systematically.
