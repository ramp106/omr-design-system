---
title: Breakpoints
type: foundation
status: stable
last_updated: 2026-05-04
related: [typography.md, spacing.md, elevation.md]
---

# Breakpoints

## TL;DR

OMR uses **4 named breakpoints** in a **mobile-first** system: `tablet` (640px),
`laptop` (1024px), `desktop` (1440px), `wide` (1920px). Write base styles for
mobile, then layer on changes with `tablet:`, `laptop:`, `desktop:` prefixes.
Typography scales fluidly via `clamp()` — most responsive work is already handled
by the `txt-*` and `responsive-container` utilities.

---

## Architecture

| Layer | What it is | Where it lives |
|---|---|---|
| **Breakpoint values** | Pixel thresholds for each named breakpoint | `screens.ts` (source of truth) |
| **CSS variables** | `--breakpoint-*` and `--width-*` custom properties | `theme.css` `@theme` block |
| **Tailwind prefixes** | `tablet:`, `laptop:`, `desktop:` responsive modifiers | Tailwind v4 config |
| **Responsive utilities** | `responsive-container`, `grid-container`, `grid-gap` | `utilities.css` |
| **JS runtime detection** | `useDisplay()` Vue composable | `useDisplay.ts` |

> **Mobile-first.** Base styles apply to all screen sizes. Breakpoint prefixes
> add or override styles at that width **and above**. There is no `mobile:` prefix —
> mobile is the default.

---

## Breakpoint scale

| Name | Min-width | Tailwind prefix | CSS variable | Typical devices |
|---|---|---|---|---|
| **mobile** | 0px | (none — base styles) | — | Phones, small screens |
| **tablet** | 640px | `tablet:` | `--breakpoint-tablet` | Large phones landscape, small tablets |
| **laptop** | 1024px | `laptop:` | `--breakpoint-laptop` | Tablets landscape, laptops |
| **desktop** | 1440px | `desktop:` | `--breakpoint-desktop` | Desktop monitors |
| **wide** | 1920px | — | `--breakpoint-wide` | Large/ultra-wide monitors |

> **`wide` is CSS-variable-only.** It is defined as a token (`--breakpoint-wide`,
> `--width-wide`) but **not registered as a Tailwind utility prefix**. Use it in
> raw CSS via `@media (min-width: var(--breakpoint-wide))` when needed.

### Viewport ranges

```
          0        640       1024       1440       1920
          |---------|---------|----------|----------|-------->
 mobile   |xxxxxxxxx|
 tablet              |xxxxxxxx|
 laptop                        |xxxxxxxxx|
 desktop                                  |xxxxxxxxx|
 wide                                                |xxxxxx>
```

---

## CSS variables

All breakpoints are available as CSS custom properties for use in raw CSS contexts:

| Variable | Value | Usage |
|---|---|---|
| `--breakpoint-tablet` | 640px | Media query threshold |
| `--breakpoint-laptop` | 1024px | Media query threshold |
| `--breakpoint-desktop` | 1440px | Media query threshold |
| `--breakpoint-wide` | 1920px | Media query threshold |
| `--width-tablet` | 640px | Width constraints, containers |
| `--width-laptop` | 1024px | Width constraints, containers |
| `--width-desktop` | 1440px | Width constraints, containers |
| `--width-wide` | 1920px | Width constraints, containers |

---

## Responsive layout utilities

Pre-built utilities that handle breakpoint-specific padding, max-width, and grid
spacing. Use these instead of writing custom responsive padding.

### `responsive-container`

The primary page-level wrapper. Adjusts horizontal padding per breakpoint and
caps content width at desktop.

| Breakpoint | Behaviour |
|---|---|
| mobile | `px-4` (16px padding) |
| tablet | `px-6` (24px padding) |
| laptop | `px-8` (32px padding) |
| desktop | `max-w-[1440px] px-16 mx-auto` (64px padding, centered, 1440px max) |

### `grid-gap`

Responsive gap for grid layouts.

| Breakpoint | Behaviour |
|---|---|
| mobile - laptop | `gap-4` (16px) |
| desktop | `gap-6` (24px) |

### `grid-container`

Composite utility combining responsive layout + 12-column grid:

```html
<div class="grid-container">
  <!-- responsive-container + grid grid-cols-12 grid-gap w-full -->
</div>
```

---

## JS runtime detection — `useDisplay()`

Vue composable for breakpoint-aware logic in JavaScript/TypeScript. Import from
`@ramp106/omrjs-core-ui`.

```typescript
import { useDisplay, Breakpoint } from '@ramp106/omrjs-core-ui'

const { breakpoint, width, height, isMobile, isInitialized } = useDisplay()

// breakpoint.value is one of: Breakpoint.Mobile | Breakpoint.Tablet | Breakpoint.Laptop | Breakpoint.Desktop
// isMobile.value is true for Mobile AND Tablet (< 1024px)
```

| Return value | Type | Description |
|---|---|---|
| `breakpoint` | `Ref<Breakpoint>` | Current breakpoint enum value |
| `width` | `Ref<number>` | Current viewport width in px |
| `height` | `Ref<number>` | Current viewport height in px |
| `isMobile` | `ComputedRef<boolean>` | `true` when breakpoint is Mobile or Tablet (< 1024px) |
| `isInitialized` | `Ref<boolean>` | `true` after first resize event fires |

> **Prefer CSS-first.** Use `useDisplay()` only when you need JS logic (e.g. conditionally
> rendering entire component trees). For visual changes, use Tailwind breakpoint prefixes.

---

## Decision rules ("Spielregeln")

### When to use breakpoint prefixes
- **Default to mobile-first.** Write the mobile layout as base styles, then add
  `tablet:`, `laptop:`, `desktop:` for larger screens.
- **Most text is already handled.** The `txt-*` fluid typography system scales via
  `clamp()` — no breakpoint prefixes needed for text sizing.
- **Use `responsive-container`** for page-level padding instead of manual responsive padding.
- **Use `grid-container`** for 12-column layouts that need responsive gaps.

### Which breakpoint for what
- **`tablet:`** — switch from single-column to 2-column layouts, expand card grids.
- **`laptop:`** — add sidebars, expand navigation, show more content per row.
- **`desktop:`** — cap content width, add generous whitespace, show full-density layouts.
- **`wide` (CSS only)** — rare. Only for full-bleed backgrounds or cinema-width hero sections.

### `isMobile` vs breakpoint prefixes
- **CSS prefixes** for show/hide, layout, spacing, typography.
- **`useDisplay()`** only for conditional rendering of entirely different component trees,
  lazy-loading, or JS logic that depends on screen size.

---

## Anti-patterns

- ❌ `@media (min-width: 768px)` — arbitrary value. **Use** `tablet:` (640px) or `laptop:` (1024px).
- ❌ `sm:`, `md:`, `lg:`, `xl:` — default Tailwind prefixes. **Use** `tablet:`, `laptop:`, `desktop:` (OMR semantic names).
- ❌ `wide:hidden` or `wide:flex` — `wide` is not registered as a Tailwind prefix. Use a raw `@media` query with `--breakpoint-wide` or reconsider if `desktop:` suffices.
- ❌ Writing responsive text sizes manually (`tablet:text-lg laptop:text-xl`) — the `txt-*` fluid system handles this. **Use** `txt-body-m-regular` and let `clamp()` scale it.
- ❌ Desktop-first styles with `max-width` media queries — OMR is **mobile-first**. Base styles are mobile, breakpoints layer upward.
- ❌ Using `useDisplay()` for layout changes that CSS can handle — JS breakpoint detection causes layout shift. **Use** CSS breakpoint prefixes instead.

---

## Examples

### Do — responsive card grid

```html
<div class="grid-container">
  <div class="col-span-12 tablet:col-span-6 desktop:col-span-4">Card 1</div>
  <div class="col-span-12 tablet:col-span-6 desktop:col-span-4">Card 2</div>
  <div class="col-span-12 tablet:col-span-6 desktop:col-span-4">Card 3</div>
</div>
```

### Do — responsive page layout

```html
<div class="responsive-container">
  <h1 class="txt-headline-4xl-bold text-main">Page title</h1>
  <p class="txt-body-m-regular text-subtle max-w-prose text-pretty mt-4">
    Content that reads well at any width.
  </p>
</div>
```

### Do — conditional rendering with useDisplay

```vue
<script setup lang="ts">
import { useDisplay, Breakpoint } from '@ramp106/omrjs-core-ui'

const { breakpoint } = useDisplay()
</script>

<template>
  <FullNavigation v-if="breakpoint === Breakpoint.Desktop" />
  <MobileMenu v-else />
</template>
```

### Don't — arbitrary breakpoints

```html
<div class="hidden md:block lg:flex">...</div>
```
**Why wrong:** `md:` and `lg:` are default Tailwind breakpoints, not OMR semantic names.
**Use:** `hidden tablet:block laptop:flex`

### Don't — manual responsive text

```html
<h2 class="text-xl tablet:text-2xl laptop:text-3xl">Title</h2>
```
**Why wrong:** bypasses the fluid typography system. **Use:** `txt-headline-3xl-bold`

---

## Cross-references

- [`typography.md`](./typography.md) — fluid typography uses tablet/laptop breakpoints for `clamp()` scaling
- [`spacing.md`](./spacing.md) — responsive spacing patterns
- [`../concepts/density-and-rhythm.md`](../concepts/density-and-rhythm.md) (todo) — how layout density changes across breakpoints
- [`../CLAUDE.md`](../CLAUDE.md) — agent rules
