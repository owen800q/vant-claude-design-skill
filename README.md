# Vant PWA Design Skill for Claude Code

A Claude Code skill that helps you design and build Progressive Web Apps (PWA) and mobile applications using the **Vant** UI component library.

## Installation

### Option 1: Clone this repository (Recommended)

```bash
# Clone into your project directory
git clone https://github.com/owen800q/vant-claude-design-skill.git
cd vant-claude-design-skill

# Or copy the skills to your existing project
cp -r .claude/skills/* /path/to/your/project/.claude/skills/
```

### Option 2: Manual Installation

1. Create the skills directory in your project:
```bash
mkdir -p .claude/skills
```

2. Download the skill files into `.claude/skills/`:
   - `vant-pwa-design.md` - Main design system reference (Vue.js focused)
   - `vant-page-templates.md` - Vue.js page templates and components
   - `vant-html-prototype.md` - HTML prototyping (no build tools needed)

### Option 3: Add as Git Submodule

```bash
git submodule add https://github.com/owen800q/vant-claude-design-skill.git .claude/skills/vant
```

## Directory Structure

```
your-project/
├── .claude/
│   └── skills/
│       ├── vant-pwa-design.md      # Design system & Vue components
│       ├── vant-page-templates.md   # Complete Vue page templates
│       └── vant-html-prototype.md   # HTML/CSS prototyping
├── src/
└── ...
```

## Usage

Once the skill files are in your `.claude/skills/` directory, Claude Code will **automatically** use them when you ask questions about:

- Mobile app design
- PWA development
- Vant components
- Mobile UI patterns
- HTML prototyping

### Example Prompts

**For HTML Prototypes:**
```
Create an HTML prototype for a login page using Vant design
```
```
Design a mobile e-commerce home page as HTML mockup
```
```
Build a static HTML profile page with Vant styling
```

**For Vue.js Apps:**
```
Create a Vue component for a product list using Vant
```
```
Build a shopping cart page with Vant components
```
```
Implement dark mode toggle with Vant ConfigProvider
```

**Design Questions:**
```
What are the Vant color tokens?
```
```
How do I use Vant's spacing system?
```
```
Show me the Vant button sizes
```

## What's Included

### 1. `vant-pwa-design.md`
- Complete design tokens (colors, typography, spacing)
- CSS variables reference
- Dark mode configuration
- Component architecture patterns
- Layout system (Grid, Row/Col)
- Common UI patterns
- PWA best practices
- Theme customization

### 2. `vant-page-templates.md`
- Login page template
- Home page with tab bar
- Product list/detail pages
- Shopping cart page
- Profile/settings page
- Component compositions (address picker, coupon selector, etc.)

### 3. `vant-html-prototype.md`
- CDN-based setup (no build tools)
- Pure HTML/CSS component examples
- Complete static page templates
- Icon reference
- Dark mode toggle
- Prototyping tips

## Quick Start for HTML Prototypes

```html
<!DOCTYPE html>
<html>
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="https://fastly.jsdelivr.net/npm/vant@4/lib/index.css">
</head>
<body>
  <!-- Your prototype here -->
</body>
</html>
```

## Design Tokens Quick Reference

| Token | Value |
|-------|-------|
| Primary Color | `#1989fa` |
| Success Color | `#07c160` |
| Danger Color | `#ee0a24` |
| Warning Color | `#ff976a` |
| Text Color | `#323233` |
| Background | `#f7f8fa` |
| Border Radius SM | `2px` |
| Border Radius MD | `4px` |
| Border Radius LG | `8px` |
| Padding Base | `4px` |
| Padding MD | `16px` |

## Requirements

- Claude Code CLI
- For Vue.js: Vue 3.x, Vant 4.x
- For HTML: Any modern browser

## License

MIT
