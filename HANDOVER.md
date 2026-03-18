# MidWest Design System — Developer Handover

> Version 1.0 · Tailwind CSS · AI Product Components

## Quick Start

```bash
npm install
npm run dev     # Watch mode
npm run build   # Production build
```

Open `index.html` in a browser to view the full component library.

---

## File Structure

```
midwest-design-system/
├── index.html          # Component documentation (single-page)
├── tailwind.config.js  # All design tokens
├── src/
│   └── input.css       # Tailwind directives + component classes
├── dist/
│   └── output.css      # Generated CSS (gitignored)
├── HANDOVER.md         # This file
└── package.json
```

---

## Token System

All tokens live in `tailwind.config.js`. They map to CSS utility classes:

| Token group | Prefix | Example |
|---|---|---|
| Ink (neutrals) | `mw-ink-{shade}` | `bg-mw-ink-950`, `text-mw-ink-400` |
| Surface | `mw-surface-{variant}` | `bg-mw-surface`, `border-mw-surface-border` |
| Primary | `mw-primary-{shade}` | `bg-mw-primary-600`, `text-mw-primary-500` |
| Accent | `mw-accent-{shade}` | `bg-mw-accent-100`, `text-mw-accent-700` |
| Semantic | `mw-success`, `mw-danger`, `mw-warning` | `bg-mw-success-light`, `text-mw-danger-dark` |

### Color decisions
- **mw-ink-950** (`#09090B`) — darkest surface, sidebar background
- **mw-ink-900** (`#111318`) — dark cards, secondary dark surfaces
- **mw-primary-600** (`#4F46E5`) — primary CTA, links, active states
- **mw-surface-border** (`#E4E4E7`) — all borders on white surfaces

---

## Component Classes

Reusable component classes are defined in `src/input.css` under `@layer components`.

### Buttons

```html
<button class="btn-primary">Primary</button>
<button class="btn-secondary">Secondary</button>
<button class="btn-ghost">Ghost</button>
<button class="btn-dark">Dark</button>
<button class="btn-danger">Danger</button>

<!-- Size modifiers -->
<button class="btn-primary btn-sm">Small</button>
<button class="btn-primary btn-lg">Large</button>
```

### Cards

```html
<div class="card p-5">Default card</div>
<div class="card-elevated p-5">Elevated (hover shadow)</div>
<div class="card-flat p-5">Flat / muted background</div>
<div class="card-dark p-5">Dark card</div>
```

### Badges

```html
<span class="badge-primary">Primary</span>
<span class="badge-accent">Accent</span>
<span class="badge-success">Active</span>
<span class="badge-danger">Error</span>
<span class="badge-warning">Warning</span>
<span class="badge-neutral">Neutral</span>
```

### Inputs

```html
<input class="input" type="text" placeholder="..." />
<input class="input-search" type="search" placeholder="Search..." />
```

### Sidebar

```html
<aside class="sidebar">
  <a class="sidebar-item">Nav item</a>
  <a class="sidebar-item-active">Active item</a>
</aside>
```

### Chat

```html
<!-- AI message -->
<div class="chat-bubble-ai">Response from AI</div>

<!-- User message -->
<div class="chat-bubble-user">User input</div>

<!-- Input bar -->
<div class="chat-input-bar">
  <input class="flex-1 focus:outline-none text-sm" placeholder="What would you like to do?" />
</div>
```

### Tables

```html
<table class="table-mw">
  <thead><tr><th>Task</th><th>Owner</th><th>Status</th></tr></thead>
  <tbody>
    <tr><td>Review wireframes</td><td>Person B</td><td><span class="badge-warning">In progress</span></td></tr>
  </tbody>
</table>
```

### Layouts

```html
<!-- Two column: content + side panel -->
<div class="layout-two-col">
  <main>Main content</main>
  <aside>Side panel</aside>
</div>

<!-- Three column card grid -->
<div class="layout-three-col">
  <div class="card">Card 1</div>
  <div class="card">Card 2</div>
  <div class="card">Card 3</div>
</div>

<!-- Full-screen sidebar + content shell -->
<div class="layout-sidebar-content">
  <aside class="sidebar">...</aside>
  <main class="flex-1 overflow-y-auto">...</main>
</div>
```

---

## Typography Scale

| Class | Size | Usage |
|---|---|---|
| `text-5xl font-bold` | 3rem | Display / hero |
| `text-4xl font-bold` | 2.25rem | Page H1 |
| `text-3xl font-semibold` | 1.875rem | Section H2 |
| `text-2xl font-semibold` | 1.5rem | Card title H3 |
| `text-xl font-semibold` | 1.25rem | Subsection H4 |
| `text-base` | 1rem | Body copy |
| `text-sm` | 0.875rem | UI labels, descriptions |
| `text-xs` | 0.75rem | Captions, meta |
| `text-2xs` (custom) | 0.625rem | Micro labels |

---

## Dark Mode

Dark mode uses Tailwind's `class` strategy. Toggle by adding/removing `dark` on `<html>`:

```js
document.documentElement.classList.toggle('dark')
```

In HTML, prefix dark variants:
```html
<div class="bg-white dark:bg-mw-ink-950 text-mw-ink-900 dark:text-white">
  Content
</div>
```

---

## Spacing System

4px base grid. Key values:
- `p-2` = 8px (tight padding)
- `p-3` = 12px (compact)
- `p-4` = 16px (default)
- `p-5` = 20px (card padding)
- `p-6` = 24px (section padding)
- `gap-4` = 16px (default gap)
- `gap-6` = 24px (section gap)

---

## Adding New Components

1. Define the component in `src/input.css` under `@layer components`
2. Use existing token names (`mw-primary-600`, `mw-ink-950`, etc.)
3. Document it in `index.html` with a preview section and code snippet
4. Update this `HANDOVER.md` with usage examples

---

## Browser Support

- Chrome 90+, Firefox 88+, Safari 14+, Edge 90+
- Tailwind generates only used utility classes in production builds
- No JS framework dependency — pure HTML + CSS

---

## Extending the System

This design system is structured to evolve as a skill:

- **New color**: Add to `tailwind.config.js` colors, document in Colors section
- **New component**: Add to `@layer components` in `input.css`
- **New pattern**: Add a section to `index.html` with preview + code
- **New token type** (animation, blur, etc.): Extend `tailwind.config.js` theme
