---
title: Spacing
type: foundation
status: stable
last_updated: 2026-05-11
related: [typography.md, breakpoints.md, sizing.md, radius.md]

tokens:
  base-unit:
    css_var: "--spacing"
    rem: "0.25rem"
    px: 4
    source: "Tailwind v4 default (not redefined in OMR's theme.css)"

  # === Standard range (0–32px) — ~80% of product UI ===
  scale-standard:
    "0":   { rem: "0",        px: 0,  tailwind: "p-0" }
    "px":  { rem: "—",        px: 1,  tailwind: "p-px" }
    "0.5": { rem: "0.125rem", px: 2,  tailwind: "p-0.5" }
    "1":   { rem: "0.25rem",  px: 4,  tailwind: "p-1" }
    "1.5": { rem: "0.375rem", px: 6,  tailwind: "p-1.5" }
    "2":   { rem: "0.5rem",   px: 8,  tailwind: "p-2" }
    "2.5": { rem: "0.625rem", px: 10, tailwind: "p-2.5" }
    "3":   { rem: "0.75rem",  px: 12, tailwind: "p-3" }
    "3.5": { rem: "0.875rem", px: 14, tailwind: "p-3.5" }
    "4":   { rem: "1rem",     px: 16, tailwind: "p-4" }
    "5":   { rem: "1.25rem",  px: 20, tailwind: "p-5" }
    "6":   { rem: "1.5rem",   px: 24, tailwind: "p-6" }
    "7":   { rem: "1.75rem",  px: 28, tailwind: "p-7" }
    "8":   { rem: "2rem",     px: 32, tailwind: "p-8" }

  # === Extended range (36–384px) — section padding, marketing, hero ===
  scale-extended:
    "9":   { rem: "2.25rem",  px: 36,  tailwind: "p-9" }
    "10":  { rem: "2.5rem",   px: 40,  tailwind: "p-10" }
    "11":  { rem: "2.75rem",  px: 44,  tailwind: "p-11" }
    "12":  { rem: "3rem",     px: 48,  tailwind: "p-12" }
    "14":  { rem: "3.5rem",   px: 56,  tailwind: "p-14" }
    "16":  { rem: "4rem",     px: 64,  tailwind: "p-16" }
    "20":  { rem: "5rem",     px: 80,  tailwind: "p-20" }
    "24":  { rem: "6rem",     px: 96,  tailwind: "p-24" }
    "28":  { rem: "7rem",     px: 112, tailwind: "p-28" }
    "32":  { rem: "8rem",     px: 128, tailwind: "p-32" }
    "36":  { rem: "9rem",     px: 144, tailwind: "p-36" }
    "40":  { rem: "10rem",    px: 160, tailwind: "p-40" }
    "44":  { rem: "11rem",    px: 176, tailwind: "p-44" }
    "48":  { rem: "12rem",    px: 192, tailwind: "p-48" }
    "52":  { rem: "13rem",    px: 208, tailwind: "p-52" }
    "56":  { rem: "14rem",    px: 224, tailwind: "p-56" }
    "60":  { rem: "15rem",    px: 240, tailwind: "p-60" }
    "64":  { rem: "16rem",    px: 256, tailwind: "p-64" }
    "72":  { rem: "18rem",    px: 288, tailwind: "p-72" }
    "80":  { rem: "20rem",    px: 320, tailwind: "p-80" }
    "96":  { rem: "24rem",    px: 384, tailwind: "p-96" }

  utility-families:
    padding:   ["p-*", "px-*", "py-*", "pt-*", "pr-*", "pb-*", "pl-*"]
    margin:    ["m-*", "mx-*", "my-*", "mt-*", "mr-*", "mb-*", "ml-*"]
    gap:       ["gap-*", "gap-x-*", "gap-y-*"]
    space:     ["space-x-*", "space-y-*"]
    inset:     ["inset-*", "top-*", "right-*", "bottom-*", "left-*"]
    negative:  ["-mt-*", "-mb-*", "-mx-*", "-my-*"]

  composite-utilities:
    responsive-container:
      source: "packages/config-tailwind/styles/utilities.css"
      values:
        mobile:  "px-4"
        tablet:  "px-6"
        laptop:  "px-8"
        desktop: "px-16 max-w-[1440px] mx-auto"
      code_drift: "current code ships `desktop:px-[60px]` — canonical is `px-16` (64px). Pending code fix."
    grid-gap:
      source: "packages/config-tailwind/styles/utilities.css"
      values:
        mobile_to_laptop: "gap-4"
        desktop:          "gap-6"
    grid-container:
      source: "packages/config-tailwind/styles/utilities.css"
      composes: ["responsive-container", "grid", "grid-cols-12", "grid-gap", "w-full"]
    card:
      source: "packages/config-tailwind/styles/utilities.css"
      padding_all: "p-6"
      additional: ["rounded", "border border-grey-300", "bg-white"]
    separate-rows:
      source: "packages/config-tailwind/styles/utilities.css"
      effect: "border-b border-grey-300 last:border-b-0"
      usage: "Divider-based row separation (not padding per se)"

  html-element-rhythm:
    # text-common-styles in utilities.css + @layer base in theme.css
    h1: { tailwind: "mb-4", px: 16 }
    h2: { tailwind: "mb-3", px: 12 }
    h3: { tailwind: "mb-2", px: 8 }
    h4: { tailwind: "mb-1", px: 4 }
    h5: { tailwind: "mb-1", px: 4 }
    p:  { tailwind: "mb-4", px: 16 }
    ul: { tailwind: "pb-6 pl-6", px: "24/24" }
    ol: { tailwind: "pb-6 pl-6", px: "24/24" }
    li: { tailwind: "mb-1; :first-child mt-2; :last-child mb-2" }
    table:    { tailwind: "mb-6 w-full", px: 24 }
    table_td: { tailwind: "p-3 align-top", px: 12 }
    pre:      { tailwind: "p-1", px: 4 }
    blockquote: { tailwind: null, raw_css: "padding: 10px 20px; margin: 0 0 20px", note: "off-scale, hardcoded in @layer base — do not replicate" }
---

# Spacing

## TL;DR

OMR uses **Tailwind's default 4px-based spacing scale** for all padding, margin,
and gap. Always pick a Tailwind utility (`p-4`, `mt-2`, `gap-6`) — never raw
pixel values, never arbitrary values like `p-[16px]`. For page-level layout, use
the composite utilities `responsive-container`, `grid-container`, and `grid-gap`
instead of writing breakpoint-specific padding.

---

## Principles

- **Rhythm before novelty.** Reuse the same handful of spacing steps across the
  product so users feel a consistent rhythm. Inventing new spacing values for
  one screen breaks that rhythm.
- **Step, don't tweak.** If `p-4` feels wrong, move to `p-3` or `p-6` — don't
  reach for `p-[14px]`. Off-scale values almost always indicate a different
  underlying problem (wrong size, wrong layout, wrong density).
- **Composite over manual.** When OMR ships a composite utility for a recurring
  layout (`responsive-container`, `grid-gap`, `card`), prefer it over assembling
  the pieces yourself.

---

## Architecture

| Layer | What it is | Where it lives |
|---|---|---|
| **Base unit** | `--spacing: 0.25rem` (4px) — Tailwind v4 default | Tailwind v4 (implicit, not redefined in `theme.css`) |
| **Spacing scale** | `0`, `px`, `0.5`, `1`–`16` and beyond | Tailwind defaults (default scale) |
| **Spacing utilities** | `p-*`, `m-*`, `gap-*`, `space-x-*`, `space-y-*`, `px-*`, `py-*`, etc. | Tailwind defaults |
| **Composite utilities** | `responsive-container`, `grid-container`, `grid-gap`, `card`, `separate-rows` | `utilities.css` |
| **Element defaults** | Vertical rhythm for `h1`–`h5`, `p`, `ul`, `ol`, `li`, `table`, `blockquote` | `text-common-styles` in `utilities.css`, `@layer base` in `theme.css` |

> **No custom spacing tokens.** Unlike colors or typography, spacing has no
> OMR-specific token layer — the scale is Tailwind's default. The OMR layer
> sits *above* the scale: composite utilities and element rhythm.

> **Marketing tokens not included.** The Figma file defines an additional layer
> of semantic spacing tokens (`Custom.Website.hspace-*`, `vspace-*`, `gap-*`,
> `container-max-width`) for the marketing site (omr.com / brand.omr.com).
> Those are **not part of the omr-js product UI token system** and are
> deliberately omitted here.

---

## Spacing scale

Tailwind's default 4px-based scale. Each step multiplies the base unit (`0.25rem` / 4px).
The full scale is split into two ranges below — the **standard range** covers
~80% of product-UI work; the **extended range** is reserved for section padding,
large vertical rhythm, and marketing/hero contexts.

### Standard range (0–32px)

The everyday vocabulary. If a value isn't here, you're probably in the wrong
range — most product UI never leaves this band.

| Step | rem | px | Tailwind class |
|---|---|---|---|
| `0` | 0 | 0px | `p-0` / `m-0` / `gap-0` |
| `px` | — | 1px | `p-px` / `m-px` |
| `0.5` | 0.125rem | 2px | `p-0.5` |
| `1` | 0.25rem | 4px | `p-1` |
| `1.5` | 0.375rem | 6px | `p-1.5` |
| `2` | 0.5rem | 8px | `p-2` |
| `2.5` | 0.625rem | 10px | `p-2.5` |
| `3` | 0.75rem | 12px | `p-3` |
| `3.5` | 0.875rem | 14px | `p-3.5` |
| `4` | 1rem | 16px | `p-4` |
| `5` | 1.25rem | 20px | `p-5` |
| `6` | 1.5rem | 24px | `p-6` |
| `7` | 1.75rem | 28px | `p-7` |
| `8` | 2rem | 32px | `p-8` |

### Extended range (36–384px)

Larger steps for section-level padding, full-width hero spacing, and marketing
layouts. Use sparingly — anything ≥ `20` (80px) usually signals a section, not
a component.

| Step | rem | px | Tailwind class |
|---|---|---|---|
| `9` | 2.25rem | 36px | `p-9` |
| `10` | 2.5rem | 40px | `p-10` |
| `11` | 2.75rem | 44px | `p-11` |
| `12` | 3rem | 48px | `p-12` |
| `14` | 3.5rem | 56px | `p-14` |
| `16` | 4rem | 64px | `p-16` |
| `20` | 5rem | 80px | `p-20` |
| `24` | 6rem | 96px | `p-24` |
| `28` | 7rem | 112px | `p-28` |
| `32` | 8rem | 128px | `p-32` |
| `36` | 9rem | 144px | `p-36` |
| `40` | 10rem | 160px | `p-40` |
| `44` | 11rem | 176px | `p-44` |
| `48` | 12rem | 192px | `p-48` |
| `52` | 13rem | 208px | `p-52` |
| `56` | 14rem | 224px | `p-56` |
| `60` | 15rem | 240px | `p-60` |
| `64` | 16rem | 256px | `p-64` |
| `72` | 18rem | 288px | `p-72` |
| `80` | 20rem | 320px | `p-80` |
| `96` | 24rem | 384px | `p-96` |

> **Practical guidance.** In product UI, almost everything lives in steps `1`–`8`.
> Steps `9`–`16` appear for section padding and large vertical rhythm. Steps `20`
> and beyond are rare and usually marketing/hero context only.

The scale applies identically to every spacing utility:

| Utility family | What it controls |
|---|---|
| `p-*`, `px-*`, `py-*`, `pt-*`, `pr-*`, `pb-*`, `pl-*` | Padding |
| `m-*`, `mx-*`, `my-*`, `mt-*`, `mr-*`, `mb-*`, `ml-*` | Margin |
| `gap-*`, `gap-x-*`, `gap-y-*` | Flex/grid gap |
| `space-x-*`, `space-y-*` | Margin between siblings |
| `inset-*`, `top-*`, `right-*`, `bottom-*`, `left-*` | Positioning offsets |
| `-mt-*`, `-mb-*`, `-mx-*`, … | Negative margins (allowed when explicitly needed) |

---

## Composite spacing utilities

Pre-built utilities that bundle canonical spacing patterns. Use these instead
of re-assembling the same paddings/gaps in every component.

### `responsive-container`

Page-level wrapper. Bumps horizontal padding at each breakpoint and caps content
width on desktop. **Use this on any top-level page or section instead of writing
manual responsive padding.**

```css
/* utilities.css */
@utility responsive-container {
  @apply px-4 tablet:px-6 laptop:px-8;
  @apply desktop:mx-auto desktop:max-w-[1440px] desktop:px-16;
}
```

| Breakpoint | Horizontal padding |
|---|---|
| mobile (< 640px) | `px-4` (16px) |
| tablet (≥ 640px) | `px-6` (24px) |
| laptop (≥ 1024px) | `px-8` (32px) |
| desktop (≥ 1440px) | `px-16` (64px) + `max-w-[1440px]` + `mx-auto` |

> **⚠️ Code drift — pending fix.** The current `utilities.css` in `omr-js` ships
> `desktop:px-[60px]` (an arbitrary value — 60px). The canonical value per the
> design system is `desktop:px-16` (64px, on the Tailwind scale). The code will
> be aligned in a follow-up. Until then, **generate UI against the canonical
> value (`px-16`)** — do not propagate the 60px drift.

### `grid-gap`

Responsive gap for 12-column grids and card layouts.

```css
@utility grid-gap {
  @apply gap-4 desktop:gap-6;
}
```

| Breakpoint | Gap |
|---|---|
| mobile → laptop | `gap-4` (16px) |
| desktop (≥ 1440px) | `gap-6` (24px) |

### `grid-container`

Composite of `responsive-container` + 12-col grid + `grid-gap`. Use for any
12-column layout — never combine these utilities manually.

```css
@utility grid-container {
  @apply responsive-container;
  @apply grid grid-cols-12 grid-gap w-full;
}
```

### `card`

Standard card padding (and border + radius + bg). Spacing-relevant aspect:
`px-6 py-6` (24px on all sides).

```css
@utility card {
  @apply rounded border border-grey-300 bg-white px-6 py-6;
}
```

### `separate-rows`

Adds a bottom border (not spacing per se), but is the canonical way to space
list items in lists where dividers are preferred over gaps.

```css
@utility separate-rows {
  @apply border-b border-grey-300 last:border-b-0;
}
```

---

## HTML element vertical rhythm

Inside `text-common-styles` scopes (CMS content, rich text, markdown rendering),
HTML elements use these baked-in margins. **In normal Vue components, set
spacing explicitly with utilities — don't rely on element defaults.**

| Element | Spacing applied | Why |
|---|---|---|
| `h1` | `mb-4` (16px) | Major section break |
| `h2` | `mb-3` (12px) | Sub-section break |
| `h3` | `mb-2` (8px) | Group title |
| `h4`, `h5` | `mb-1` (4px) | Tight group title |
| `p` | `mb-4` (16px) | Paragraph rhythm |
| `ul`, `ol` | `pb-6 pl-6` (24px / 24px) | List wrapper |
| `li` | `mb-1` (4px), `:first-child mt-2`, `:last-child mb-2` | List item rhythm |
| `table` | `mb-6 w-full` (24px) | Block separator |
| `table td` | `p-3 align-top` (12px) | Cell padding |
| `pre` | `p-1` (4px) | Code block padding |
| `blockquote` | `padding: 10px 20px; margin: 0 0 20px` | Off-scale, hardcoded in `@layer base` |

> **Off-scale callout.** The `blockquote` values (10px, 20px) are inline literals
> in `@layer base`, not Tailwind utilities. They predate the Tailwind migration
> and are an exception, not a precedent — never copy this pattern into new code.

---

## Decision rules ("Spielregeln")

> **Separation rule:** This file documents single-foundation rules only. When
> spacing combines with sizing (component heights, touch targets) or typography
> (vertical rhythm in real layouts), see the relevant concept file.

### Picking a step

- **Default to even steps** (`2`, `4`, `6`, `8`) — they cover ~80 % of cases.
- **Use `1` (4px)** for tight, intentional gaps: icon-to-label, chip internals,
  badge padding.
- **Use `2` (8px)** for inline gaps inside form rows, toolbar items, button groups.
- **Use `4` (16px)** as the standard padding for cards, panels, list items.
- **Use `6` (24px)** for card/panel padding when the content is dense or has
  multiple sections.
- **Use `8` (32px)** for vertical separation between major content blocks.
- **Use `10`–`16` (40–64px)** for section-level vertical rhythm on marketing or
  full-width pages.
- **Step up or down by one**, not two, when adjusting. `p-4` → `p-6`, not `p-4` → `p-8`.

### Padding vs margin vs gap

- **Prefer `gap-*`** over `space-x-*`/`space-y-*` for flex and grid layouts —
  works correctly with wrapping and is more predictable.
- **Use `space-y-*`** only on non-flex/grid stacks where a gap utility cannot apply.
- **Use margin** for explicit "this element pushes away from its neighbour"
  intent — typically `mt-*` or `mb-*` on individual elements.
- **Use padding** for "this container has internal breathing room" — applied
  to the container, not its children.

### Page-level layout

- **Wrap pages in `responsive-container`** instead of writing manual responsive padding.
- **Use `grid-container`** for any 12-column layout.
- **Use `grid-gap`** when you need the standard responsive gap but a different
  outer wrapper.
- **Never apply both `responsive-container` and manual `px-*`** — pick one.

### Negative margins

- **Allowed but rare.** Use only to compensate for a parent's padding when
  pulling a child element to a wrapper edge (e.g. full-bleed image inside a
  padded card).
- **Always use scale values** (`-mt-4`, not `-mt-[14px]`).

---

## Anti-patterns

- ❌ `padding: 16px` or `style="padding: 16px"` — raw CSS. **Use** `p-4`.
- ❌ `p-[16px]` — arbitrary value when a scale step exists. **Use** `p-4`.
- ❌ `p-[14px]` to "match a Figma export" — the scale step `p-3.5` exists, but
  question whether the value really is `14px` or whether the design intends `p-3`
  (12px) or `p-4` (16px). Off-scale is almost always wrong.
- ❌ `space-x-4` inside a `flex` container with wrapping. **Use** `gap-4` —
  `space-*` breaks on wrap.
- ❌ Stacking `responsive-container px-4 tablet:px-8` — the utility already sets
  responsive padding. **Use** `responsive-container` alone.
- ❌ Manual breakpoint padding on a page wrapper:
  `<div class="px-4 tablet:px-6 laptop:px-8 desktop:max-w-[1440px] desktop:px-16 desktop:mx-auto">`
  — that's literally what `responsive-container` exists for.
- ❌ `desktop:px-[60px]` — legacy drift in `responsive-container`. **Use** `desktop:px-16` (Tailwind step 16 = 64px). The drift will be cleaned up in a code fix.
- ❌ Mixing `space-y-4` and `gap-4` on the same element — pick one model.
- ❌ Inventing a new "card" utility with different padding — extend or reuse the
  `card` utility, or use `p-6` directly so it stays on-scale.
- ❌ `mb-[10px]` to match a blockquote — that off-scale value is a legacy in
  `@layer base`, not a pattern to replicate.
- ❌ Massive vertical margins (`mt-32`, `mb-48`) in product UI — usually a sign
  the layout is missing structure. Use a section wrapper with sensible padding.

---

## Tailwind config reference

```css
/* Tailwind v4 defaults — not redefined in OMR's theme.css */
@theme {
  --spacing: 0.25rem; /* 4px base unit, multiplies through the scale */
}
```

```css
/* utilities.css — OMR composite spacing utilities */
@utility responsive-container { … }
@utility grid-gap { … }
@utility grid-container { … }
@utility card { … }
@utility separate-rows { … }
```

> The base unit (`--spacing`) is **inherited from Tailwind v4** and not declared
> in OMR's `@theme` block. If it ever needs to change, it must be redeclared in
> `theme.css`.

---

## Examples

### Do — page wrapper with responsive padding

```html
<div class="responsive-container py-8">
  <h1 class="txt-headline-4xl-bold text-main">Page title</h1>
  <p class="txt-body-m-regular text-subtle mt-4 max-w-prose text-pretty">
    Content with a comfortable reading width.
  </p>
</div>
```

### Do — 12-column grid with responsive gap

```html
<div class="grid-container py-8">
  <article class="col-span-12 tablet:col-span-6 desktop:col-span-4 card">
    Card 1
  </article>
  <article class="col-span-12 tablet:col-span-6 desktop:col-span-4 card">
    Card 2
  </article>
</div>
```

### Do — flex row with consistent gap

```html
<div class="flex items-center gap-2">
  <Icon class="h-4 w-4" />
  <span class="txt-label-m-medium text-main">Label</span>
</div>
```

### Do — vertical stack with explicit rhythm

```html
<section class="flex flex-col gap-6">
  <h2 class="txt-headline-2xl-bold text-main">Section title</h2>
  <p class="txt-body-m-regular text-subtle max-w-prose">Intro paragraph.</p>
  <div class="grid grid-cols-3 gap-4">…</div>
</section>
```

### Don't — arbitrary value bypassing the scale

```html
<div class="p-[14px] mb-[22px]">…</div>
```
**Why wrong:** breaks the rhythm. **Use** `p-3 mb-6` (or `p-4 mb-5`,
depending on which scale step the design actually means).

### Don't — manual responsive padding on a page

```html
<div class="px-4 tablet:px-6 laptop:px-8 desktop:px-16 desktop:max-w-[1440px] desktop:mx-auto">…</div>
```
**Why wrong:** duplicates `responsive-container`. **Use** `responsive-container`.

### Don't — `space-y` on a wrapping flex layout

```html
<div class="flex flex-wrap space-x-4">…</div>
```
**Why wrong:** `space-x-*` breaks on wrap (no margin between rows).
**Use** `flex flex-wrap gap-4`.

---

## Cross-references

- [`breakpoints.md`](./breakpoints.md) — `responsive-container`, `grid-gap`,
  `grid-container` from the responsive-layout angle
- [`typography.md`](./typography.md) — `txt-*` baked-in line heights pair with
  vertical spacing for rhythm
- [`sizing.md`](./sizing.md) (todo) — component heights, container widths, icon
  sizes
- [`radius.md`](./radius.md) (todo) — border radius scale (separate from spacing)
- [`../concepts/padding-tokens.md`](../concepts/padding-tokens.md) (planned) —
  semantic padding-token layer (separate planning session — addresses the
  Figma-side scope restriction on `Spacing.space-*`)
- [`../concepts/density-and-rhythm.md`](../concepts/density-and-rhythm.md) (todo) —
  how spacing combines with sizing and typography for density tiers
- [`../concepts/visual-hierarchy.md`](../concepts/visual-hierarchy.md) (todo) —
  how spacing reinforces emphasis alongside color and typography
- [`../concepts/accessibility.md`](../concepts/accessibility.md) (todo) — touch
  target spacing (≥ 44 px)
- [`../CLAUDE.md`](../CLAUDE.md) — agent rules
