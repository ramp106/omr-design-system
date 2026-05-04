---
title: Color
type: foundation
status: stable
last_updated: 2026-05-04
related: [elevation.md, typography.md, button-hierarchy.md, elevation-system.md]
---

# Color

## TL;DR

OMR colors are a **two-layer system**: raw primitives auto-generated from Figma
(never use these directly), and **semantic tokens** that components reference via
Tailwind utilities. Choose tokens by **intent** (`text-primary` for brand,
`text-error` for errors), not by hue. Dark theme works automatically — no extra work needed.

---

## Architecture

| Layer | What it is | Where it lives | When to use it |
|---|---|---|---|
| **Layer 1 — Primitives** | Raw hex palette (e.g. `--color-purple-700`) | `primitiveColors.generated.css` | **Never directly.** Only inside semantic-token definitions. |
| **Layer 2 — Semantic tokens** | Intent-named tokens (e.g. `--text-color-primary`) | `lightTheme.generated.css`, `darkTheme.generated.css` | **Always.** Via Tailwind utilities (`text-primary`). |

> **Why two layers:** primitives can change without breaking components, dark theme
> can swap values per token, and AI agents have a small, intent-based vocabulary
> to choose from instead of hundreds of hex codes.

### Primitive palette (reference only — do not reference directly)

| Scale | Steps |
|---|---|
| **grey** | 0, 25, 50, 100, 150, 200, 250, 300, 350, 400, 450, 500, 550, 600, 650, 700, 750, 800, 850, 900, 950, 975, 1000 (23 steps) |
| **purple** | 25, 50, 100, 200, 300, 400, 500, 600, 700, 800, 900, 950 (12 steps) |
| **yellow** | 50, 100, 200, 300, 400, 500, 600, 700, 800, 900, 950 (11 steps) |
| **blue** | 25, 50, 100, 200, 300, 400, 500, 600, 700, 800, 900, 950 (12 steps) |
| **red** | 50, 100, 200, 300, 400, 500, 600, 700, 800, 900, 950 (11 steps) |
| **jade** | 50, 100, 200, 300, 400, 500, 600, 700, 800, 900, 950 (11 steps) |
| **green** | 50, 100, 200, 300, 400, 500, 600, 700, 800, 900, 950 (11 steps) |
| **mint** | 50, 100, 200, 300, 400, 500, 600, 700, 800, 900, 950 (11 steps) |
| **rose** | 50, 100, 200, 300, 400, 500, 600, 700, 800, 900, 950 (11 steps) |

**Special aliases** (defined in `theme.css`):

| Alias | Resolves to |
|---|---|
| `--color-white` | `var(--color-grey-25)` — near-white `#fdfdfd` |
| `--color-true-white` | `#ffffff` |
| `--color-black` | `var(--color-grey-950)` — near-black `#0c0d0f` |
| `--color-true-black` | `#000000` |

---

## Decision rule — which token category do I need?

```
What am I colouring?
├─ Text or icon       → Text colors / Icon colors
├─ A link             → Link colors
├─ A surface / fill   → Background colors
├─ A 1px line or ring → Border colors
├─ A hover/press/drag feedback layer → Interaction state colors
└─ A focus ring       → Effect colors
```

For **status meaning** (success/error/warning) the same rule applies but the
status modifier picks the variant — e.g. text feedback -> `text-error`,
filled status banner -> `bg-error-subtle` + `border-error` + `text-error`.

---

## Text colors

| Tailwind utility | CSS variable | Usage |
|---|---|---|
| `text-main` | `--text-color-main` | Primary readable body text — the default |
| `text-subtle` | `--text-color-subtle` | Secondary / supporting text |
| `text-subtlest` | `--text-color-subtlest` | Placeholder, hint text |
| `text-primary` | `--text-color-primary` | Brand purple — emphasis, brand mentions |
| `text-primary-subtle` | `--text-color-primary-subtle` | Lighter brand purple text |
| `text-selected` | `--text-color-selected` | Highlighted / selected state text |
| `text-solid` | `--text-color-solid` | Pure black — charts, print contexts |
| `text-solid-inverse` | `--text-color-solid-inverse` | Pure white — charts, print contexts |
| `text-inverse` | `--text-color-inverse` | Text on **dark** backgrounds (use with `bg-surface-inverse`) |
| `text-disabled` | `--text-color-disabled` | Disabled labels |
| `text-error` | `--text-color-error` | Error messages |
| `text-error-inverse` | `--text-color-error-inverse` | Error text on dark backgrounds |
| `text-success` | `--text-color-success` | Success messages |
| `text-success-inverse` | `--text-color-success-inverse` | Success text on dark backgrounds |
| `text-warning` | `--text-color-warning` | Warning messages |
| `text-warning-inverse` | `--text-color-warning-inverse` | Warning text on dark backgrounds |
| `text-badge-filled-success` | `--text-color-badge-filled-success` | Text on filled success badge |
| `text-badge-filled-warning` | `--text-color-badge-filled-warning` | Text on filled warning badge |
| `text-badge-filled-error` | `--text-color-badge-filled-error` | Text on filled error badge |

### Icons

| Utility | Variable | Usage |
|---|---|---|
| `text-icon-main` | `--text-color-icon-main` | Default icons |
| `text-icon-subtle` | `--text-color-icon-subtle` | Secondary icons |
| `text-icon-subtlest` | `--text-color-icon-subtlest` | Tertiary / muted icons |
| `text-icon-primary` | `--text-color-icon-primary` | Brand icons |
| `text-icon-primary-subtle` | `--text-color-icon-primary-subtle` | Lighter brand icons |
| `text-icon-secondary` | `--text-color-icon-secondary` | Secondary brand icons (yellow) |
| `text-icon-secondary-subtle` | `--text-color-icon-secondary-subtle` | Lighter secondary icons |
| `text-icon-selected` | `--text-color-icon-selected` | Selected / highlighted icons |
| `text-icon-solid` | `--text-color-icon-solid` | Pure black icons |
| `text-icon-solid-inverse` | `--text-color-icon-solid-inverse` | Pure white icons |
| `text-icon-inverse` | `--text-color-icon-inverse` | Icons on dark backgrounds |
| `text-icon-disabled` | `--text-color-icon-disabled` | Disabled icons |
| `text-icon-error` | `--text-color-icon-error` | Error icons |
| `text-icon-error-inverse` | `--text-color-icon-error-inverse` | Error icons on dark backgrounds |
| `text-icon-success` | `--text-color-icon-success` | Success icons |
| `text-icon-success-inverse` | `--text-color-icon-success-inverse` | Success icons on dark backgrounds |
| `text-icon-warning` | `--text-color-icon-warning` | Warning icons |
| `text-icon-warning-inverse` | `--text-color-icon-warning-inverse` | Warning icons on dark backgrounds |
| `text-icon-badge-filled-success` | `--text-color-icon-badge-filled-success` | Icon on filled success badge |
| `text-icon-badge-filled-warning` | `--text-color-icon-badge-filled-warning` | Icon on filled warning badge |
| `text-icon-badge-filled-error` | `--text-color-icon-badge-filled-error` | Icon on filled error badge |

### Links

| Utility | Variable | Usage |
|---|---|---|
| `text-link-main` | `--text-color-link-main` | Default link colour |
| `text-link-primary` | `--text-color-link-primary` | Brand-coloured link |
| `text-link-inverse` | `--text-color-link-inverse` | Link on dark backgrounds |
| `text-link-disabled` | `--text-color-link-disabled` | Disabled link |

---

## Background colors

### Surface tiers — **this is how OMR expresses elevation, not shadows**

| Utility | Variable | Usage |
|---|---|---|
| `bg-surface` | `--background-color-surface` | Page base — the canvas |
| `bg-solid` | `--background-color-solid` | Pure white (e.g. cards on tinted pages) |
| `bg-surface-elevation-1` | `--background-color-surface-elevation-1` | +1 depth (lightest grey above page) |
| `bg-surface-elevation-2` | `--background-color-surface-elevation-2` | +2 depth |
| `bg-surface-elevation-3` | `--background-color-surface-elevation-3` | +3 depth |
| `bg-surface-elevation-4` | `--background-color-surface-elevation-4` | +4 depth |
| `bg-surface-elevation-5` | `--background-color-surface-elevation-5` | +5 depth (darkest grey, rare) |
| `bg-surface-inverse` | `--background-color-surface-inverse` | Dark surface (use with `text-inverse`) |

### Alpha surface tiers (for overlays on imagery)

| Utility | Variable | Usage |
|---|---|---|
| `bg-surface-alpha-elevation-1` | `--background-color-surface-alpha-elevation-1` | Transparent +1 depth — content shows through |
| `bg-surface-alpha-elevation-2` | `--background-color-surface-alpha-elevation-2` | Transparent +2 depth |
| `bg-surface-alpha-elevation-3` | `--background-color-surface-alpha-elevation-3` | Transparent +3 depth |
| `bg-surface-alpha-elevation-4` | `--background-color-surface-alpha-elevation-4` | Transparent +4 depth |
| `bg-surface-alpha-elevation-5` | `--background-color-surface-alpha-elevation-5` | Transparent +5 depth |

### Primary fills (brand purple)

| Utility | Variable | Usage |
|---|---|---|
| `bg-primary-main` | `--background-color-primary-main` | Brand purple fill — primary buttons, brand emphasis |
| `bg-primary-strong` | `--background-color-primary-strong` | Darker brand purple — hover on primary |
| `bg-primary-stronger` | `--background-color-primary-stronger` | Even darker — pressed state |
| `bg-primary-strongest` | `--background-color-primary-strongest` | Darkest brand purple |
| `bg-primary-subtle` | `--background-color-primary-subtle` | Pale purple fill — selected items, brand banners |
| `bg-primary-subtler` | `--background-color-primary-subtler` | Lighter pale purple |
| `bg-primary-subtlest` | `--background-color-primary-subtlest` | Lightest pale purple — backgrounds, hovers |

### Primary alpha fills (transparent primary for overlays on imagery)

| Utility | Variable | Usage |
|---|---|---|
| `bg-primary-alpha-strong` | `--background-color-primary-alpha-strong` | Transparent dark brand purple overlay |
| `bg-primary-alpha-stronger` | `--background-color-primary-alpha-stronger` | Transparent darker brand purple overlay |
| `bg-primary-alpha-strongest` | `--background-color-primary-alpha-strongest` | Transparent darkest brand purple overlay |
| `bg-primary-alpha-subtle` | `--background-color-primary-alpha-subtle` | Transparent pale purple overlay |
| `bg-primary-alpha-subtler` | `--background-color-primary-alpha-subtler` | Transparent lighter pale purple overlay |
| `bg-primary-alpha-subtlest` | `--background-color-primary-alpha-subtlest` | Transparent lightest pale purple overlay |

> Use primary alpha fills when layering brand colour on top of imagery or
> content that should remain visible. Analogous to the alpha surface tiers.

### Secondary fills (brand yellow)

| Utility | Variable | Usage |
|---|---|---|
| `bg-secondary-main` | `--background-color-secondary-main` | Secondary yellow fill — accent elements |
| `bg-secondary-strong` | `--background-color-secondary-strong` | Darker secondary — hover on secondary |
| `bg-secondary-stronger` | `--background-color-secondary-stronger` | Even darker secondary |
| `bg-secondary-strongest` | `--background-color-secondary-strongest` | Darkest secondary |
| `bg-secondary-subtle` | `--background-color-secondary-subtle` | Pale yellow fill |
| `bg-secondary-subtler` | `--background-color-secondary-subtler` | Lighter pale yellow |
| `bg-secondary-subtlest` | `--background-color-secondary-subtlest` | Lightest pale yellow — backgrounds |

### Status fills

| Utility | Variable | Usage |
|---|---|---|
| `bg-error-strong` | `--background-color-error-strong` | Solid error fill — high-emphasis indicators |
| `bg-error-subtle` | `--background-color-error-subtle` | Pale error tint — banners, badges |
| `bg-success-strong` | `--background-color-success-strong` | Solid success fill |
| `bg-success-subtle` | `--background-color-success-subtle` | Pale success tint |
| `bg-warning-strong` | `--background-color-warning-strong` | Solid warning fill |
| `bg-warning-subtle` | `--background-color-warning-subtle` | Pale warning tint |
| `bg-disabled` | `--background-color-disabled` | Disabled element fill |

### Badge fills

| Utility | Variable | Usage |
|---|---|---|
| `bg-badge-filled-success` | `--background-color-badge-filled-success` | Filled success badge background |
| `bg-badge-filled-warning` | `--background-color-badge-filled-warning` | Filled warning badge background |
| `bg-badge-filled-error` | `--background-color-badge-filled-error` | Filled error badge background |

> Pair badge backgrounds with matching badge text tokens: `bg-badge-filled-success` + `text-badge-filled-success`.

### Component-specific background tokens (reference only)

These tokens are designed for specific components. Full documentation will live in
the respective component files. Do not use them in general UI — use the semantic
tokens above instead.

| Component | Tokens (Tailwind `bg-*`) |
|---|---|
| **Button** | `button-outline`, `button-outline-color`, `button-outline-destructive`, `button-outline-success`, `button-primary-color`, `button-primary-destructive`, `button-primary-neutral`, `button-primary-success`, `button-secondary-color`, `button-secondary-destructive`, `button-secondary-neutral`, `button-secondary-success` |
| **Timetable** | `timetable-event-active`, `timetable-event-inactive`, `timetable-event-passed`, `timetable-meeting-active`, `timetable-meeting-inactive`, `timetable-meeting-passed` |
| **UI chrome** | `scrollbar-handle`, `toggle-inactive` |

### Backdrop / overlay

| Utility | Variable | Usage |
|---|---|---|
| `bg-effect-backdrop-overlay` | `--background-color-effect-backdrop-overlay` | Modal backdrop — pair with `backdrop-blur-xs` |
| `bg-effect-focused` | `--background-color-effect-focused` | Focus ring background (rare — see Effect colors) |

---

## Border colors

| Utility | Variable | Usage |
|---|---|---|
| `border-main` | `--border-color-main` | Default border — most cards, inputs, dividers |
| `border-main-solid` | `--border-color-main-solid` | Solid (no alpha) variant for crisp edges |
| `border-subtle` | `--border-color-subtle` | De-emphasised dividers |
| `border-strong` | `--border-color-strong` | Strong emphasis — modal headers, sticky bars |
| `border-primary` | `--border-color-primary` | Brand purple border |
| `border-primary-solid` | `--border-color-primary-solid` | Solid brand border |
| `border-primary-subtle` | `--border-color-primary-subtle` | Subtle brand purple border |
| `border-primary-subtle-solid` | `--border-color-primary-subtle-solid` | Solid subtle brand border |
| `border-secondary` | `--border-color-secondary` | Secondary yellow border |
| `border-secondary-subtle` | `--border-color-secondary-subtle` | Subtle secondary border |
| `border-error` | `--border-color-error` | Error state — invalid inputs |
| `border-error-subtle` | `--border-color-error-subtle` | Subtle error border — banners |
| `border-success` | `--border-color-success` | Success state |
| `border-success-subtle` | `--border-color-success-subtle` | Subtle success border |
| `border-warning` | `--border-color-warning` | Warning state |
| `border-warning-subtle` | `--border-color-warning-subtle` | Subtle warning border |
| `border-selected` | `--border-color-selected` | Selection indicator (chips, radio, options) |
| `border-disabled` | `--border-color-disabled` | Disabled state |
| `border-inverse` | `--border-color-inverse` | Border on dark backgrounds |

---

## Effect colors

Focus rings and backdrop overlays.

| Utility | Variable | Usage |
|---|---|---|
| `text-effect-focused` | `--text-color-effect-focused` | Focus ring outline colour (2 px solid) |
| `text-effect-backdrop-overlay` | `--text-color-effect-backdrop-overlay` | Text overlay on backdrop |
| `text-effect-overlay-surface-solid` | `--text-color-effect-overlay-surface-solid` | Text on solid overlay surface |
| `text-effect-overlay-surface-strongest` | `--text-color-effect-overlay-surface-strongest` | Text on strongest overlay surface |
| `text-effect-overlay-surface-subtlest` | `--text-color-effect-overlay-surface-subtlest` | Text on subtlest overlay surface |
| `text-effect-overlay-surface-transparent` | `--text-color-effect-overlay-surface-transparent` | Text on transparent overlay surface |
| `bg-effect-focused` | `--background-color-effect-focused` | Focus ring background |
| `bg-effect-backdrop-overlay` | `--background-color-effect-backdrop-overlay` | Modal backdrop overlay |
| `bg-effect-overlay-surface-solid` | `--background-color-effect-overlay-surface-solid` | Solid overlay surface background |
| `bg-effect-overlay-surface-strongest` | `--background-color-effect-overlay-surface-strongest` | Strongest overlay surface background |
| `bg-effect-overlay-surface-subtlest` | `--background-color-effect-overlay-surface-subtlest` | Subtlest overlay surface background |
| `bg-effect-overlay-surface-transparent` | `--background-color-effect-overlay-surface-transparent` | Transparent overlay surface background |

> Apply focus via `omr-focus-visible-outline` (open layouts) or `omr-focus-visible-inset`
> (clipped containers with `overflow-hidden`). The `blur-overlay-style` utility
> combines `bg-effect-backdrop-overlay` + `backdrop-blur-xs` for modal backdrops.
> Overlay surface tokens provide layered surface backgrounds with matching text tokens
> at different opacity levels.

---

## Graphic colors

Dedicated colours for illustrations, charts, data visualisations, and decorative
graphics. These use the `graphic-*` Tailwind prefix and `--graphic-color-*` CSS
variables — a separate namespace from text/bg/border tokens.

### Core

| Utility | Variable | Usage |
|---|---|---|
| `graphic-black` | `--graphic-color-black` | Black graphic element |
| `graphic-white` | `--graphic-color-white` | White graphic element |
| `graphic-disabled` | `--graphic-color-disabled` | Disabled/inactive graphic element |

### Status

| Utility | Variable | Usage |
|---|---|---|
| `graphic-error` | `--graphic-color-error` | Error indicator in graphics |
| `graphic-success` | `--graphic-color-success` | Success indicator in graphics |
| `graphic-warning` | `--graphic-color-warning` | Warning indicator in graphics |

### Grey scale

| Utility | Variable | Usage |
|---|---|---|
| `graphic-grey-subtle` | `--graphic-color-grey-subtle` | Light grey — background fills, grid lines |
| `graphic-grey-medium` | `--graphic-color-grey-medium` | Medium grey — secondary data series |
| `graphic-grey-strong` | `--graphic-color-grey-strong` | Dark grey — labels, axes |

### Primary scale (purple)

| Utility | Variable | Usage |
|---|---|---|
| `graphic-primary-subtle` | `--graphic-color-primary-subtle` | Light purple — area fills, backgrounds |
| `graphic-primary-medium` | `--graphic-color-primary-medium` | Medium purple — secondary series |
| `graphic-primary-strong` | `--graphic-color-primary-strong` | Dark purple — primary data series, key metrics |

### Secondary scale (yellow)

| Utility | Variable | Usage |
|---|---|---|
| `graphic-secondary-subtle` | `--graphic-color-secondary-subtle` | Light yellow — area fills |
| `graphic-secondary-medium` | `--graphic-color-secondary-medium` | Medium yellow — secondary accent |
| `graphic-secondary-strong` | `--graphic-color-secondary-strong` | Dark yellow — accent data series |

### Tertiary scale

| Utility | Variable | Usage |
|---|---|---|
| `graphic-tertiary-subtle` | `--graphic-color-tertiary-subtle` | Light tertiary — area fills |
| `graphic-tertiary-medium` | `--graphic-color-tertiary-medium` | Medium tertiary — third data series |
| `graphic-tertiary-strong` | `--graphic-color-tertiary-strong` | Dark tertiary — tertiary data series |

> Use graphic colours only for illustrations and data visualisations — not for
> UI surfaces, text, or borders. For UI elements, use the semantic text/bg/border tokens.

---

## Interaction state layers

State layers are **semi-transparent overlays** added on hover, press, drag.
Don't reach for individual `bg-*` tokens to fake hover — use the state-layer system.

### State-layer composite utilities

| Utility | Hover | Press | Drag | Use on |
|---|---|---|---|---|
| `state-layer-neutral` | `bg-state-hover-neutral` | `bg-state-pressed-neutral` | `bg-state-drag-neutral` | Neutral interactive surfaces (cards, list items) |
| `state-layer-primary` | `bg-state-hover-primary` | `bg-state-pressed-primary` | `bg-state-drag-primary` | Brand-coloured interactive elements |
| `state-layer-neutral-inverse` | `bg-state-hover-neutral-inverse` | `bg-state-pressed-neutral-inverse` | `bg-state-drag-neutral-inverse` | Dark-themed surfaces |

> Use the `state-layer-*` utilities on the interactive element directly —
> they handle `::before` pseudo-element, z-index, opacity transition, and
> `:hover` / `:active` / `[data-drag="true"]` states automatically.

### Raw state tokens (for custom implementations only)

| Utility | Variable | Triggered by |
|---|---|---|
| `bg-state-hover-neutral` | `--background-color-state-hover-neutral` | Hover on neutral surface |
| `bg-state-pressed-neutral` | `--background-color-state-pressed-neutral` | Press on neutral surface |
| `bg-state-drag-neutral` | `--background-color-state-drag-neutral` | Drag on neutral surface |
| `bg-state-hover-neutral-inverse` | `--background-color-state-hover-neutral-inverse` | Hover on dark surface |
| `bg-state-pressed-neutral-inverse` | `--background-color-state-pressed-neutral-inverse` | Press on dark surface |
| `bg-state-drag-neutral-inverse` | `--background-color-state-drag-neutral-inverse` | Drag on dark surface |
| `bg-state-hover-primary` | `--background-color-state-hover-primary` | Hover on brand surface |
| `bg-state-pressed-primary` | `--background-color-state-pressed-primary` | Press on brand surface |
| `bg-state-drag-primary` | `--background-color-state-drag-primary` | Drag on brand surface |

---

## Decision rules ("Spielregeln")

### Choosing text colour
- **Default to `text-main`** for body text. Don't use `text-primary` "for emphasis"
  unless the content is brand-related. (How to express emphasis -> see [`concepts/visual-hierarchy.md`](../concepts/visual-hierarchy.md))
- **Use `text-subtle`** for metadata, captions, helper text — anything secondary.
- **Use `text-subtlest`** for placeholders and hint text.
- **Use `text-primary`** *only* for: brand mentions, links inside brand contexts, focused/selected indicators.
- **Use status text colours (`text-error`, `text-success`, `text-warning`)**
  only when the content carries that status meaning. Don't use red text for "important".
- **Use `*-inverse` variants** only on dark/inverse surfaces — never on light backgrounds.

### Choosing background / surface
- **`bg-surface`** is the page. Don't repeat it inside a card.
- **`bg-solid`** for cards on top of `bg-surface` when you want stark white.
- **`bg-surface-elevation-1` and up** when you need visual depth (panels, inset areas, hover states on flat surfaces).
- **Don't stack more than 3 elevation tiers** on screen at once — visual hierarchy collapses.
- **`bg-primary-main`** is reserved for primary call-to-action buttons and brand emphasis. Don't use as page background.
- **`bg-secondary-main`** is the secondary brand color (yellow). Use for accent elements, secondary CTAs, or highlights that complement the primary purple.
- **Subtle status fills (`bg-error-subtle` etc.)** for banners and badges.
  Solid status fills (`bg-error-strong`) only for high-emphasis indicators (notification dots, severity banners).
- **Badge fills** (`bg-badge-filled-*`) pair with matching badge text tokens — always use both together.

### Choosing border
- **Default to `border-main`** for most divisions.
- **`border-subtle`** when the divider is contextual (e.g. inside a card already differentiated by background).
- **`border-strong`** sparingly — typically only on sticky elements that need to "pop" against scrolling content.
- **`border-primary` or `border-selected`** to indicate selection / focus / brand state — never both at the same time.
- **`border-secondary`** for secondary brand-coloured borders (yellow accent).
- **Status borders** (`border-error`, `border-success`, `border-warning`) match the status of the input/element.
- **`*-subtle` status borders** (`border-error-subtle`, etc.) for lower-emphasis status indicators like banners.

### Mixing colours
- **One brand emphasis per view.** If you have a primary button, don't also have brand-purple text headers.
- **One status colour per element.** A success banner uses success bg + success border + success text — not mixed.
- **Backgrounds and borders should match in tier** — `bg-error-subtle` pairs with `border-error-subtle` or `border-error`, not `border-main`.

---

## Anti-patterns

- ❌ `class="bg-purple-700"` — primitive token. **Use** `bg-primary-main`.
- ❌ `style="color: #060708"` — raw hex. **Use** `text-main`.
- ❌ `class="bg-[#fdfdfd]"` — arbitrary value. **Use** `bg-surface`.
- ❌ Using `text-primary` for emphasis on non-brand content. **Use** typography weight instead (see [`concepts/visual-hierarchy.md`](../concepts/visual-hierarchy.md)).
- ❌ Stacking `bg-surface-elevation-3` on `bg-surface-elevation-2` on `bg-surface-elevation-1` on the same screen — collapses depth perception. **Limit to 2-3 visible tiers.**
- ❌ Manual hover via `hover:bg-grey-100`. **Use** the `state-layer-*` system.
- ❌ Using `bg-error-main` — this token does not exist. **Use** `bg-error-strong` for solid error fills.
- ❌ Editing `lightTheme.generated.css` or `darkTheme.generated.css` — these are auto-generated. **Update tokens in Figma**, then run `pnpm extract`.
- ❌ Inventing a new semantic token in code (e.g. `--text-color-warning-bold`). **Pipe the token through Figma -> variables.json first.**
- ❌ Mixing primary and secondary brand colours on the same element — pick one.

---

## Tailwind config reference

OMR uses **Tailwind v4** with CSS-first configuration. Tokens flow through this pipeline:

```
Figma -> variables.json -> pnpm extract -> primitiveColors.generated.css   (@theme — raw palette)
                                         -> colorTheme.generated.css       (@theme — registers semantic vars)
                                         -> lightTheme.generated.css       (@utility light-theme — light values)
                                         -> darkTheme.generated.css        (@utility dark-theme — dark values)
                                                    |
                                       Tailwind v4 resolves utilities
                                                    |
                                       text-main, bg-surface, border-primary ...
```

### How it works

1. **`primitiveColors.generated.css`** — `@theme` block defines `--color-*` primitives (the raw palette).
2. **`colorTheme.generated.css`** — `@theme` block registers all semantic variables as `unset`, telling Tailwind v4 they exist. Tailwind derives utility names from CSS variable namespaces:
   - `--text-color-{name}` -> `text-{name}`
   - `--background-color-{name}` -> `bg-{name}`
   - `--border-color-{name}` -> `border-{name}`
3. **`lightTheme.generated.css`** / **`darkTheme.generated.css`** — `@utility` blocks that assign actual colour values per theme.
4. **`theme.css`** — declares `@custom-variant dark` and `@custom-variant light`, color aliases, typography, and breakpoints.

---

## Dark theme

Dark theme is **automatic**. To enable it for a subtree, wrap a parent element:

```html
<div class="dark-theme">
  <!-- everything inside resolves dark-theme variants -->
  <p class="text-main bg-surface">...</p>
</div>
```

Every semantic token is overridden by `darkTheme.generated.css` — components don't
need any conditional classes. **Do not** write `dark:bg-...` overrides in components.

The implementation uses Tailwind v4 custom variants:
- `@custom-variant dark` — targets `.dark *` descendants
- `@custom-variant light` — targets `.light` descendants
- `@utility dark-theme { ... }` — sets all dark values
- `@utility light-theme { ... }` — sets all light values (active by default on body)

---

## Examples

### Do — primary CTA on a card

```html
<div class="bg-solid border border-main rounded-m p-6">
  <h3 class="txt-headline-m-bold text-main">Upgrade your plan</h3>
  <p class="txt-body-m-regular text-subtle mt-2">More reviews, more insights.</p>
  <button class="bg-primary-main text-inverse rounded px-4 py-2 mt-4 state-layer-primary">
    Upgrade
  </button>
</div>
```

### Do — error state on an input

```html
<input class="bg-solid border border-error rounded text-main px-3 py-2" />
<p class="txt-body-s-regular text-error mt-1">Email is required.</p>
```

### Do — success banner

```html
<div class="bg-success-subtle border border-success-subtle rounded-m p-4 flex items-center gap-3">
  <span class="text-icon-success"><!-- icon --></span>
  <p class="txt-body-s-regular text-success">Changes saved successfully.</p>
</div>
```

### Do — filled badge

```html
<span class="bg-badge-filled-warning text-badge-filled-warning txt-label-s rounded-full px-2 py-0.5">
  Pending
</span>
```

### Do — interactive card with state layer

```html
<div class="bg-solid border border-main rounded-m p-4 cursor-pointer state-layer-neutral">
  <p class="txt-body-m-regular text-main">Click me</p>
</div>
```

### Don't — primitive tokens + raw values

```html
<div class="bg-[#fdfdfd] border border-grey-200 rounded-[8px] p-6">
  <h3 class="text-[#060708] font-bold text-[18px]">...</h3>
  <button class="bg-purple-700 text-white rounded px-4 py-2">Upgrade</button>
</div>
```
**Why wrong:** arbitrary hex/values bypass the token system, primitive tokens
break theming, raw `font-*` bypasses the typography system.

### Don't — fake hover with primitive

```html
<div class="bg-surface hover:bg-grey-100 rounded-m p-4 cursor-pointer">...</div>
```
**Why wrong:** `grey-100` is primitive. **Use** the state layer:
```html
<div class="bg-surface state-layer-neutral rounded-m p-4 cursor-pointer">...</div>
```

### Don't — wrong status fill token name

```html
<div class="bg-error-main p-4">...</div>
```
**Why wrong:** `bg-error-main` does not exist. **Use** `bg-error-strong` for solid error fill.

---

## Cross-references

- [`elevation.md`](./elevation.md) (todo) — surface tiers + z-index combined
- [`typography.md`](./typography.md) (todo) — text-color always pairs with `txt-*`
- [`../concepts/visual-hierarchy.md`](../concepts/visual-hierarchy.md) (todo) — emphasis via typography weight vs. colour
- [`../concepts/button-hierarchy.md`](../concepts/button-hierarchy.md) (todo) — colour usage per button variant
- [`../concepts/interactive-states.md`](../concepts/interactive-states.md) (todo) — full state-layer pattern
- [`../CLAUDE.md`](../CLAUDE.md) — agent rules
