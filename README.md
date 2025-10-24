# CSS Pro Plugin

A comprehensive CSS development toolkit for Claude Code with specialized agents, commands, skills, and hooks covering the full styling lifecycle.

## Overview

CSS Pro provides end-to-end CSS development support from project architecture through production optimization, with intelligent methodology detection and best practice enforcement.

## Features

### 🤖 7 Specialized Sub-Agents

Expert agents for every aspect of CSS development:

- **css-architect** - CSS architecture, methodology selection (BEM, OOCSS, SMACSS, ITCSS), file organization
- **css-developer** - Modern CSS implementation with Grid, Flexbox, custom properties, and container queries
- **css-designer** - Design systems, design tokens, color systems, typography scales, and theming
- **css-optimizer** - Performance tuning for bundle size, critical CSS, and render optimization
- **css-reviewer** - Comprehensive code review with accessibility and browser compatibility checks
- **css-debugger** - Layout debugging, specificity conflicts, cascade issues, and rendering glitches
- **css-migrator** - Migration between CSS approaches, frameworks, and methodologies

### ⚡ 10 Slash Commands

Powerful workflows for common CSS tasks:

- `/css-init [architecture-type]` - Smart CSS project initialization with methodology selection
- `/css-layout [layout-type]` - Interactive Flexbox and Grid layout generator
- `/css-debug [issue]` - Systematic CSS debugging assistance
- `/css-review [file-pattern]` - Comprehensive CSS code review
- `/css-optimize [options]` - Performance optimization and bundle size reduction
- `/css-audit` - Full CSS audit (performance, accessibility, best practices)
- `/css-build [--watch]` - Build and compile CSS with error analysis
- `/css-lint [file-pattern]` - Lint and validate CSS files with Stylelint
- `/css-migrate [source] [target]` - Migration wizard between CSS approaches
- `/css-tokens [operation]` - Design token operations and management

### 🎯 8 Autonomous Skills

AI-powered capabilities that activate automatically:

- **layout-builder** - Generate production-ready Flexbox and Grid layouts
- **animation-creator** - Create optimized CSS animations with accessibility support
- **color-tools** - Color palette generation, WCAG contrast checking, and harmonies
- **a11y-checker** - Accessibility audit for focus styles, contrast, and WCAG compliance
- **responsive-helper** - Responsive design with breakpoints, fluid typography, container queries
- **design-tokens** - Design token management in multiple formats (CSS, Sass, JS, JSON)
- **css-inspector** - Deep analysis of specificity, cascade, and inheritance
- **performance-analyzer** - CSS performance analysis and optimization strategies

### 🔗 Development Hooks

Event-driven automation for your workflow:

- **Pre-write hooks** - Validate CSS syntax with Stylelint before saving
- **Post-write hooks** - Format CSS with Prettier after file changes
- **Pre-build hooks** - Analyze CSS health and performance before builds

## Installation

### Option 1: Copy Plugin to User Directory

```bash
cp -r css-pro ~/.claude/plugins/
```

### Option 2: Copy to Project Directory

```bash
cp -r css-pro /path/to/your/project/.claude/plugins/
```

### Option 3: Symlink for Development

```bash
ln -s /path/to/css-pro ~/.claude/plugins/css-pro
```

## Usage

### Using Sub-Agents

Sub-agents are automatically invoked by Claude Code based on context, or you can request them explicitly:

```
"Can you review this CSS code?" → Invokes css-reviewer
"Help me set up a CSS architecture for my React project" → Invokes css-architect
"Fix this flexbox layout issue" → Invokes css-debugger
```

### Using Slash Commands

Invoke commands directly in Claude Code:

```
/css-init bem           → Initialize project with BEM methodology
/css-layout navbar      → Generate navbar layout
/css-debug "button won't center" → Debug centering issue
/css-review src/styles/ → Review all CSS in directory
/css-optimize --production → Optimize for production
```

### Using Skills

Skills activate automatically based on context:

- Need layout code → `layout-builder` generates it
- Ask about colors → `color-tools` checks contrast
- Create animation → `animation-creator` optimizes it
- Check accessibility → `a11y-checker` audits CSS
- Mention performance → `performance-analyzer` evaluates it

### Using Hooks

Hooks run automatically during development:

- Save `.css` file → Stylelint validation runs
- Write CSS file → Prettier formats it
- Run build command → CSS health analysis executes

## Examples

### Initialize a New CSS Project

```
/css-init modules
```

This will:
1. Analyze project structure
2. Select CSS methodology (BEM, OOCSS, ITCSS, etc.)
3. Create file organization
4. Set up preprocessor if needed
5. Configure Stylelint and Prettier
6. Create base styles
7. Set up design token structure

### Generate a Responsive Layout

```
/css-layout dashboard
```

This will:
1. Ask about layout requirements
2. Generate Grid or Flexbox code
3. Add responsive breakpoints
4. Include fallbacks for older browsers
5. Optimize for performance
6. Add accessibility features
7. Provide usage documentation

### Debug CSS Issues

```
/css-debug "My flexbox items won't center vertically"
```

This will:
1. Analyze the issue description
2. Check common centering problems
3. Inspect specificity conflicts
4. Review parent/child relationships
5. Identify root cause
6. Provide solution with explanation
7. Suggest preventive measures

### Create Design Token System

```
/css-tokens create
```

This will:
1. Analyze design requirements
2. Create color tokens
3. Set up spacing scale
4. Define typography tokens
5. Generate token files (CSS, Sass, JS)
6. Create documentation
7. Provide usage examples

### Optimize CSS for Production

```
/css-optimize --production
```

This will:
1. Analyze CSS bundle size
2. Remove unused selectors
3. Extract critical CSS
4. Minify stylesheets
5. Optimize selector complexity
6. Generate performance report
7. Expected: 60-80% size reduction

### Migrate from Sass to CSS-in-JS

```
/css-migrate sass styled-components
```

This will:
1. Analyze Sass codebase
2. Create migration plan
3. Convert variables to JS
4. Transform mixins to functions
5. Update component styles
6. Handle theme system
7. Track migration progress

## Project Structure

```
css-pro/
├── .claude-plugin/
│   └── plugin.json              # Plugin manifest
├── agents/                      # Sub-agents
│   ├── css-architect.md
│   ├── css-developer.md
│   ├── css-designer.md
│   ├── css-optimizer.md
│   ├── css-reviewer.md
│   ├── css-debugger.md
│   └── css-migrator.md
├── commands/                    # Slash commands
│   ├── css-init.md
│   ├── css-layout.md
│   ├── css-debug.md
│   ├── css-review.md
│   ├── css-optimize.md
│   ├── css-audit.md
│   ├── css-build.md
│   ├── css-lint.md
│   ├── css-migrate.md
│   └── css-tokens.md
├── skills/                      # Autonomous skills
│   ├── layout-builder/
│   ├── animation-creator/
│   ├── color-tools/
│   ├── a11y-checker/
│   ├── responsive-helper/
│   ├── design-tokens/
│   ├── css-inspector/
│   └── performance-analyzer/
├── hooks/
│   └── hooks.json               # Event hooks
└── README.md                    # This file
```

## Requirements

- Claude Code (latest version)
- Node.js 18+ (for CSS tooling)
- Git (recommended)

## Supported Technologies

- **CSS Approaches**: Vanilla CSS, Sass, Less, PostCSS, CSS-in-JS
- **Frameworks**: Styled Components, Emotion, CSS Modules, Tailwind, Bootstrap
- **Methodologies**: BEM, OOCSS, SMACSS, ITCSS, Atomic CSS
- **Build Tools**: Vite, webpack, Parcel, esbuild, Rollup
- **Preprocessors**: Sass/SCSS, Less, Stylus, PostCSS
- **Linters**: Stylelint, PostCSS plugins
- **Formatters**: Prettier, Stylefmt

## Configuration

### Enable/Disable Hooks

Edit `hooks/hooks.json` to customize hook behavior or disable specific hooks.

### Customize Sub-Agents

Edit agent `.md` files to adjust:
- Available tools
- Model selection (sonnet, opus, haiku)
- System prompts and behavior

### Modify Commands

Edit command `.md` files to change:
- Command descriptions
- Argument hints
- Command behavior

### Stylelint Configuration

Create `.stylelintrc.js` in your project:

```javascript
module.exports = {
  extends: 'stylelint-config-standard',
  rules: {
    'selector-class-pattern': '^[a-z][a-z0-9-]*(__[a-z0-9-]+)?(--[a-z0-9-]+)?$',
    'selector-max-id': 0,
    'declaration-no-important': true
  }
};
```

### Prettier Configuration

Create `.prettierrc` in your project:

```json
{
  "printWidth": 100,
  "tabWidth": 2,
  "useTabs": false,
  "semi": true
}
```

## Troubleshooting

### Plugin Not Loading

Check that the plugin is in the correct location:
```bash
ls ~/.claude/plugins/css-pro/.claude-plugin/plugin.json
```

### Commands Not Available

Verify Claude Code recognizes the plugin:
```
/help
```

Look for CSS Pro commands in the list.

### Hooks Not Running

Ensure hooks are enabled in Claude Code settings and that the required tools (Stylelint, Prettier) are installed.

### Stylelint Errors

Install Stylelint and config:
```bash
npm install --save-dev stylelint stylelint-config-standard
```

## Contributing

Contributions welcome! To contribute:

1. Fork the plugin
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

MIT License - feel free to use and modify as needed.

## Support

For issues, questions, or feedback:
- Create an issue: https://github.com/andronics/claude-plugin-css-pro/issues
- Check Claude Code documentation: https://docs.claude.com/claude-code

## Changelog

### Version 1.0.0 (2025-01-24)

- Initial release
- 7 specialized sub-agents
- 10 slash commands
- 8 autonomous skills
- Development hooks
- Full CSS project lifecycle support
