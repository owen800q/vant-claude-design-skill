# Vant Design Skill for Claude Code

A Claude Code skill for designing and building mobile apps and PWAs using the **Vant** UI component library. Supports both Vue.js development and pure HTML/CSS prototyping.

## Installation

### Option 1: Clone and Copy (Recommended)

```bash
# Clone the repo
git clone https://github.com/owen800q/vant-claude-design-skill.git

# Copy to your project
cp -r vant-claude-design-skill/.claude/skills/vant-design /path/to/your/project/.claude/skills/
```

### Option 2: Manual Installation

```bash
# Create skills directory in your project
mkdir -p .claude/skills/vant-design

# Download SKILL.md (or copy manually)
curl -o .claude/skills/vant-design/SKILL.md \
  https://raw.githubusercontent.com/owen800q/vant-claude-design-skill/main/.claude/skills/vant-design/SKILL.md
```

## Directory Structure

```
your-project/
├── .claude/
│   └── skills/
│       └── vant-design/
│           └── SKILL.md    # Complete Vant design system
├── src/
└── ...
```

## Usage

Once installed, Claude Code will **automatically** use this skill when you ask about:

- Mobile app design
- PWA development
- Vant components
- HTML prototyping
- Mobile UI patterns

### Example Prompts

```
Create an HTML prototype for a mobile login page
```
```
Build a product list page with Vant styling
```
```
Design a shopping cart with Vue and Vant
```
```
What are the Vant color tokens?
```

## What's Included

The unified skill covers:

- **Design Tokens** - Colors, typography, spacing, borders, animations
- **HTML Prototyping** - CDN setup, pure HTML/CSS components, page templates
- **Vue.js Components** - Tab bar, forms, lists, cards, dialogs, toasts
- **Page Templates** - Login, home, profile pages (both HTML and Vue)
- **Dark Mode** - Theme switching support
- **PWA Setup** - Manifest, viewport, safe areas
- **Icon Reference** - 100+ icons with usage patterns

## Quick Start

### HTML Prototype
```html
<!DOCTYPE html>
<html>
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="https://fastly.jsdelivr.net/npm/vant@4/lib/index.css">
</head>
<body>
  <!-- Your prototype -->
</body>
</html>
```

### Vue.js
```bash
npm install vant
```

## Design Tokens Quick Reference

| Token | Value |
|-------|-------|
| Primary | `#1989fa` |
| Success | `#07c160` |
| Danger | `#ee0a24` |
| Warning | `#ff976a` |
| Text | `#323233` |
| Background | `#f7f8fa` |
| Radius SM/MD/LG | `2px` / `4px` / `8px` |
| Padding MD | `16px` |

## License

MIT
