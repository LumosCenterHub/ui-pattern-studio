# LUMOS V2.0 Design System — Global Constraints

> This file defines the mandatory rules for ALL generated files.
> Upload this file to Stitch workspace. Reference it in every generation step.

---

## VISUAL IDENTITY: Professional SaaS Admin — Classic Blue Business

```
STYLE:     Clean, professional SaaS admin dashboard
PRIMARY:   #2563EB (Blue 600)
SURFACE:   Pure white #FFFFFF backgrounds, light gray #F8FAFC secondary
BORDER:    #E2E8F0 (1px solid), clean and visible
SHADOW:    Light and subtle — 0 1px 3px rgba(0,0,0,0.06)
RADIUS:    Buttons/Inputs: 6px | Cards: 8px | Modals: 12px
FONT:      "Inter", "Segoe UI", sans-serif — clean sans-serif only
TONE:      Trustworthy, efficient, spacious whitespace, zero decoration
```

---

## ABSOLUTE RED LINES (violation = regenerate)

### RED LINE 1: No Frameworks
```
BANNED:  <script src="https://cdn.tailwindcss.com">
BANNED:  <script src="...tailwind...">
BANNED:  tailwind.config = { ... }
BANNED:  class="flex items-center gap-3 px-4 py-2 rounded-lg bg-primary/10"
BANNED:  Any Tailwind utility class (flex, grid, px-, py-, bg-, text-, rounded-, etc.)

REQUIRED: Raw CSS only. Write styles in <style> tag or inline style="" attributes.
```

### RED LINE 2: No External Resources
```
BANNED:  <link href="https://fonts.googleapis.com/...">
BANNED:  <link href="https://fonts.gstatic.com/...">
BANNED:  Material Symbols / Material Icons / Font Awesome / any CDN icon library
BANNED:  <span class="material-symbols-outlined">...</span>
BANNED:  Any external <script src="..."> or <link href="..."> (except nothing)

REQUIRED: Zero external requests. Every file must work fully offline.
REQUIRED: All icons = hand-written inline SVG only.
```

### RED LINE 3: Consistent Color
```
BANNED:  Orange (#F97316, #EA580C, etc.) as accent or decoration
BANNED:  Purple, teal, or any non-blue accent color
BANNED:  Gradients as backgrounds
BANNED:  Dark/black backgrounds (except code snippets)
BANNED:  Glassmorphism, blur, frosted effects

REQUIRED: Primary actions = #2563EB blue only
REQUIRED: Backgrounds = #FFFFFF or #F8FAFC only
REQUIRED: Semantic colors: green=#10B981 success, amber=#F59E0B warning, red=#EF4444 error ONLY
```

---

## MANDATORY TOKENS (:root block for EVERY HTML file)

Every generated HTML file must include this EXACT :root block at the top of its `<style>` tag.
Do NOT modify, rename, or abbreviate any variable name.

```css
:root {
  /* Primary Blue */
  --color-primary-50: #EFF6FF;
  --color-primary-100: #DBEAFE;
  --color-primary-200: #BFDBFE;
  --color-primary-300: #93C5FD;
  --color-primary-400: #60A5FA;
  --color-primary-500: #3B82F6;
  --color-primary-600: #2563EB;
  --color-primary-700: #1D4ED8;
  --color-primary-800: #1E40AF;
  --color-primary-900: #1E3A8A;

  /* Slate Gray */
  --color-slate-50: #F8FAFC;
  --color-slate-100: #F1F5F9;
  --color-slate-200: #E2E8F0;
  --color-slate-300: #CBD5E1;
  --color-slate-400: #94A3B8;
  --color-slate-500: #64748B;
  --color-slate-600: #475569;
  --color-slate-700: #334155;
  --color-slate-800: #1E293B;
  --color-slate-900: #0F172A;

  /* Text */
  --color-text-primary: #0F172A;
  --color-text-secondary: #475569;
  --color-text-muted: #94A3B8;
  --color-text-inverse: #FFFFFF;
  --color-text-link: #2563EB;

  /* Semantic */
  --color-success: #10B981;
  --color-success-bg: #ECFDF5;
  --color-warning: #F59E0B;
  --color-warning-bg: #FFFBEB;
  --color-error: #EF4444;
  --color-error-bg: #FEF2F2;

  /* Backgrounds */
  --color-bg-primary: #FFFFFF;
  --color-bg-secondary: #F8FAFC;
  --color-bg-tertiary: #F1F5F9;
  --color-bg-hover: #F8FAFC;
  --color-bg-active: #EFF6FF;
  --color-bg-overlay: rgba(0, 0, 0, 0.4);
  --color-surface-soft: #F1F5F9;

  /* Borders */
  --color-border-default: #E2E8F0;
  --color-border-strong: #CBD5E1;
  --color-border-focus: #2563EB;

  /* Shadows */
  --shadow-sm: 0 1px 2px rgba(0,0,0,0.05);
  --shadow-md: 0 1px 3px rgba(0,0,0,0.06), 0 1px 2px rgba(0,0,0,0.04);
  --shadow-lg: 0 4px 12px rgba(0,0,0,0.08);
  --shadow-xl: 0 8px 24px rgba(0,0,0,0.10);

  /* Radius */
  --radius-sm: 4px;
  --radius-md: 6px;
  --radius-lg: 8px;
  --radius-xl: 12px;
  --radius-full: 9999px;

  /* Spacing */
  --space-1: 4px;  --space-2: 8px;  --space-3: 12px;
  --space-4: 16px; --space-5: 20px; --space-6: 24px;
  --space-8: 32px; --space-10: 40px; --space-12: 48px;

  /* Sizes */
  --size-control-sm: 32px;
  --size-control-md: 36px;
  --size-control-lg: 44px;
  --size-header-height: 56px;
  --size-sidebar-width: 220px;
  --size-sidebar-collapsed: 56px;
  --size-content-max-width: 1200px;

  /* Font */
  --font-family: "Inter", "Segoe UI", "PingFang SC", "Microsoft YaHei", sans-serif;
  --font-size-xs: 12px;  --font-size-sm: 13px;
  --font-size-base: 14px; --font-size-md: 16px;
  --font-size-lg: 18px;  --font-size-xl: 20px;
  --font-size-2xl: 24px;

  /* Interaction */
  --transition-fast: all 0.15s ease;
  --focus-ring: 0 0 0 3px rgba(37, 99, 235, 0.15);
}
```

---

## HTML SKELETON (every file must follow this structure)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>FILE N. Title</title>
  <style>
    :root { /* FULL tokens from above */ }
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body {
      background: var(--color-bg-primary);
      font-family: var(--font-family);
      color: var(--color-text-primary);
      -webkit-font-smoothing: antialiased;
      padding: 40px;
    }
    .page-wrap { max-width: 960px; margin: 0 auto; }
    .page-title { font-size: 32px; font-weight: 700; color: var(--color-text-primary); }
    .page-desc { font-size: 14px; color: var(--color-text-secondary); margin-top: 8px; }
    .divider { border: none; border-top: 1px solid var(--color-border-default); margin: 24px 0; }
    .section-title { font-size: 18px; font-weight: 600; margin-bottom: 16px; color: var(--color-text-primary); }
    .section-gap { height: 40px; }
    /* Component-specific styles below... */
  </style>
</head>
<body>
  <div class="page-wrap">
    <h1 class="page-title">FILE N. Title</h1>
    <p class="page-desc">Description text</p>
    <hr class="divider">

    <h3 class="section-title">1. Variant Name</h3>
    <div><!-- component with inline SVG icons --></div>
    <div class="section-gap"></div>

    <h3 class="section-title">2. Variant Name</h3>
    <div><!-- component --></div>
  </div>

  <script>
    function toggleActive(el) { el.classList.toggle('active'); }
    document.addEventListener('click', function(e) {
      document.querySelectorAll('.dropdown.active').forEach(function(d) {
        if (!d.contains(e.target)) d.classList.remove('active');
      });
    });
  </script>
</body>
</html>
```

---

## ICON SPECIFICATION

All icons must be inline SVG. Standard format:
```html
<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
  <path d="..."/>
</svg>
```

Rules:
- stroke="currentColor" always (inherits parent text color)
- NEVER hardcode stroke="#2563EB" or fill="#xxx" inside SVG
- NEVER use Unicode symbols (▾ ▸ ▼ ► etc.)
- NEVER use CSS border to draw triangles/arrows

---

## INTERACTION REQUIREMENTS

- Every clickable element must have `transition: var(--transition-fast)` on hover
- Hover states: background shift or shadow increase, must be visible
- Focus states: `box-shadow: var(--focus-ring)` on focusable elements
- Button sizes locked: sm=32px, md=36px, lg=44px via `height` property
- All `<select>` must be div-simulated, BANNED native `<select>` tag
- All date pickers must be div-simulated, BANNED native `<input type="date">`
- Toggle switches: div+CSS only, BANNED native checkbox
- Standard JS: `toggleActive(el)` function name, do not rename
- Click-outside-close: `document.addEventListener('click', ...)` for dropdowns

---

## PAGE STRUCTURE RULES

- Line 1: Bold English title with file number (e.g., "FILE 1. Buttons")
- Line 2: English description (e.g., "8 button variants")
- Then: horizontal divider
- Then: numbered variant sections
- NOTHING ELSE. No navbar, no logo bar, no sidebar, no footer, no tabs, no avatar, no breadcrumbs.

---

## VARIABLE NAME LOCK

- The :root block above is the SOLE authority for variable names
- BANNED: inventing new names (e.g., `--primary` instead of `--color-primary-600`)
- BANNED: abbreviating (e.g., `--bg-white` instead of `--color-bg-primary`)
- If unsure about a name, copy exactly from the :root block above
