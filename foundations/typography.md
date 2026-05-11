---
title: Typography
type: foundation
status: stable
last_updated: 2026-05-04
related: [color.md, spacing.md, breakpoints.md]
---

# Typography

## TL;DR

OMR uses a **fluid typography system** built on `clamp()`. All text must use
`txt-{category}-{size}-{weight}` utilities — never raw `font-size`, `font-weight`,
or `letter-spacing`. Four categories: **label** (static, UI chrome), **body** (prose),
**headline** (section headings), **display** (hero/marketing). Sizes scale automatically
between breakpoints — no responsive overrides needed.

---

## Principles

- **Clarity before style.** Typography serves the content and its information
  architecture. Use headings to express hierarchy — not decoration. Keep emphasis
  lightweight and meaningful; avoid styling that competes with the message.
- **Predictable rhythm.** A consistent scale, line heights, and spacing create a
  rhythm users can scan quickly. Use the documented size steps and avoid inventing
  other sizes unless they graduate into a documented token.
- **Accessibility by default.** Keep body text >= 16px (14px only in dense UI,
  12px very sparingly). Everything must remain readable under zoom (100-250%).
  Links are underlined by default. Prefer relative units (rem, em, %).

---

## Architecture

| Layer | What it is | Where it lives |
|---|---|---|
| **Font families** | OMR One (variable), OMR Sans (static), Futura ND (legacy) | `omr-one.css`, `omr-sans.css`, `futurand.css` |
| **Theme tokens** | Font stacks, base size, tracking, leading | `theme.css` `@theme` block |
| **Typography utilities** | `txt-*` composites with fluid sizing | `typography-fluid.css` |
| **Legacy aliases** | Old `text-*` names mapped to new `txt-*` | `typography-legacy.css` (deprecated) |

> **CSS-first system.** Unlike colors, typography is not generated from Figma.
> The source of truth is `typography-fluid.css`, hand-maintained.

### Naming convention

```
txt-{category}-{size}-{weight}

category : label | body | headline | display
size     : s | m | l | xl | 2xl | 3xl | 4xl | 5xl  (varies by category)
weight   : regular | medium | semibold | bold | bold-uppercase | extrabold-uppercase
```

Not every combination exists — see the tables below for available utilities.

---

## Decision rule — which category do I need?

```
What kind of text am I setting?
├─ A UI label, tag, overline, chip text     -> Label (static, small, wider tracking)
├─ Prose, description, helper text, form    -> Body (fluid, normal leading)
├─ Section heading, card title, page title  -> Headline (fluid, tight leading)
└─ Hero text, marketing banner, splash      -> Display (fluid, large, tight leading)
```

---

## Font families

| Token | Tailwind class | Value | Usage |
|---|---|---|---|
| `--font-sans` | `font-sans` | 'OMR One', 'Avenir', 'Helvetica', 'Arial', sans-serif | Default for all UI text |
| `--font-mono` | `font-mono` | 'ui-monospace', 'SFMono-Regular', 'Menlo', 'Monaco', ... | Code blocks, technical content |

### Font files

| Font | File | Type | Weights | Usage |
|---|---|---|---|---|
| **OMR One** | `omr-one.css` | Variable (woff2) | 400-800 | Primary brand font — all new UI |
| **OMR Sans** | `omr-sans.css` | Static (woff2/woff) | regular (100-400), bold (500-700), extra-bold (800-900) | Fallback, legacy use |
| **Futura ND** | `futurand.css` | Static | 100-900 | Legacy only — do not use in new UI |

---

## Label utilities

Static sizes (no fluid scaling). Use for UI chrome: labels, tags, overlines, chip text, badges.

| Utility | Size | Weight | Leading | Tracking |
|---|---|---|---|---|
| `txt-label-s-regular` | 0.75rem (12px) | 400 normal | 140% | 2% wider |
| `txt-label-s-medium` | 0.75rem (12px) | 500 medium | 140% | 2% wider |
| `txt-label-s-semibold` | 0.75rem (12px) | 600 semibold | 140% | 2% wider |
| `txt-label-s-bold` | 0.75rem (12px) | 700 bold | 140% | 2% wider |
| `txt-label-s-bold-uppercase` | 0.75rem (12px) | 700 bold + uppercase | 140% | 2% wider |
| `txt-label-m-regular` | 0.875rem (14px) | 400 normal | 140% | 2% wider |
| `txt-label-m-medium` | 0.875rem (14px) | 500 medium | 140% | 2% wider |
| `txt-label-m-semibold` | 0.875rem (14px) | 600 semibold | 140% | 2% wider |
| `txt-label-m-bold` | 0.875rem (14px) | 700 bold | 140% | 2% wider |
| `txt-label-m-bold-uppercase` | 0.875rem (14px) | 700 bold + uppercase | 140% | 2% wider |

---

## Body utilities

Fluid sizes — scale up from the `laptop` breakpoint (1024px) via `clamp()`.
Use for prose, descriptions, UI text, form content.

| Utility | Mobile | Laptop+ | Weight | Leading | Tracking |
|---|---|---|---|---|---|
| `txt-body-s-regular` | 14px | 14px -> 16px | 400 normal | 140% | 1% wide |
| `txt-body-s-medium` | 14px | 14px -> 16px | 500 medium | 140% | 1% wide |
| `txt-body-s-semibold` | 14px | 14px -> 16px | 600 semibold | 140% | 1% wide |
| `txt-body-s-bold` | 14px | 14px -> 16px | 700 bold | 140% | 1% wide |
| `txt-body-m-regular` | 16px | 16px -> 18px | 400 normal | 140% | 0 normal |
| `txt-body-m-medium` | 16px | 16px -> 18px | 500 medium | 140% | 0 normal |
| `txt-body-m-semibold` | 16px | 16px -> 18px | 600 semibold | 140% | 0 normal |
| `txt-body-m-bold` | 16px | 16px -> 18px | 700 bold | 140% | 0 normal |
| `txt-body-l-regular` | 18px | 18px -> 20px | 400 normal | 140% | 0 normal |
| `txt-body-l-medium` | 18px | 18px -> 20px | 500 medium | 140% | 0 normal |
| `txt-body-l-semibold` | 18px | 18px -> 20px | 600 semibold | 140% | 0 normal |
| `txt-body-l-bold` | 18px | 18px -> 20px | 700 bold | 140% | 0 normal |
| `txt-body-xl-regular` | 20px | 20px -> 22px | 400 normal | 140% | 0 normal |
| `txt-body-xl-medium` | 20px | 20px -> 22px | 500 medium | 140% | 0 normal |
| `txt-body-xl-semibold` | 20px | 20px -> 22px | 600 semibold | 140% | 0 normal |
| `txt-body-xl-bold` | 20px | 20px -> 22px | 700 bold | 140% | 0 normal |

---

## Headline utilities

Fluid sizes — headlines scale across `tablet` (640px) and `laptop` (1024px) breakpoints.
Use for section headings, card titles, page titles. Tight leading (120%) differentiates
headlines from body at the same size.

| Utility | Mobile | Laptop+ | Weight | Leading | Tracking |
|---|---|---|---|---|---|
| `txt-headline-s-semibold` | 14px | 14px -> 16px | 600 semibold | 120% | 1% wide |
| `txt-headline-s-bold` | 14px | 14px -> 16px | 700 bold | 120% | 1% wide |
| `txt-headline-s-extrabold-uppercase` | 14px | 14px -> 16px | 800 extrabold + uppercase | 120% | 1% wide |
| `txt-headline-m-semibold` | 16px | 16px -> 18px | 600 semibold | 120% | 0 normal |
| `txt-headline-m-bold` | 16px | 16px -> 18px | 700 bold | 120% | 0 normal |
| `txt-headline-m-extrabold-uppercase` | 16px | 16px -> 18px | 800 extrabold + uppercase | 120% | 2% wider |
| `txt-headline-l-semibold` | 18px | 18px -> 20px | 600 semibold | 120% | 0 normal |
| `txt-headline-l-bold` | 18px | 18px -> 20px | 700 bold | 120% | 0 normal |
| `txt-headline-l-extrabold-uppercase` | 18px | 18px -> 20px | 800 extrabold + uppercase | 120% | 2% wider |
| `txt-headline-xl-semibold` | 20px | 20px -> 22px | 600 semibold | 120% | 0 normal |
| `txt-headline-xl-bold` | 20px | 20px -> 22px | 700 bold | 120% | 0 normal |
| `txt-headline-xl-extrabold-uppercase` | 20px | 20px -> 22px | 800 extrabold + uppercase | 120% | 2% wider |
| `txt-headline-2xl-semibold` | 22px | -> 28px | 600 semibold | 120% | 0 normal |
| `txt-headline-2xl-bold` | 22px | -> 28px | 700 bold | 120% | 0 normal |
| `txt-headline-2xl-extrabold-uppercase` | 22px | -> 28px | 800 extrabold + uppercase | 120% | 1% wide |
| `txt-headline-3xl-semibold` | -> 26px | -> 36px | 600 semibold | 120% | 0 normal |
| `txt-headline-3xl-bold` | -> 26px | -> 36px | 700 bold | 120% | 0 normal |
| `txt-headline-3xl-extrabold-uppercase` | -> 26px | -> 36px | 800 extrabold + uppercase | 120% | 1% wide |
| `txt-headline-4xl-semibold` | -> 32px | -> 48px | 600 semibold | 120% | 0 normal |
| `txt-headline-4xl-bold` | -> 32px | -> 48px | 700 bold | 120% | 0 normal |
| `txt-headline-4xl-extrabold-uppercase` | -> 32px | -> 48px | 800 extrabold + uppercase | 120% | 0 normal |
| `txt-headline-5xl-semibold` | -> 38px | -> 60px | 600 semibold | 120% | 0 normal |
| `txt-headline-5xl-bold` | -> 38px | -> 60px | 700 bold | 120% | 0 normal |
| `txt-headline-5xl-extrabold-uppercase` | -> 38px | -> 60px | 800 extrabold + uppercase | 120% | 0 normal |

---

## Display utilities

Large fluid sizes for hero text and marketing banners. Aggressive fluid scaling
with `clamp()` across all three breakpoints (mobile, tablet, laptop).

| Utility | Mobile | Tablet | Laptop+ | Weight | Leading | Tracking |
|---|---|---|---|---|---|---|
| `txt-display-s-semibold` | -> 44px | -> 60px | -> 72px | 600 semibold | 120% | 0 normal |
| `txt-display-s-bold` | -> 44px | -> 60px | -> 72px | 700 bold | 120% | 0 normal |
| `txt-display-s-extrabold-uppercase` | -> 44px | -> 60px | -> 72px | 800 extrabold + uppercase | 120% | 0 normal |
| `txt-display-m-semibold` | -> 48px | -> 66px | -> 84px | 600 semibold | 120% | 0 normal |
| `txt-display-m-bold` | -> 48px | -> 66px | -> 84px | 700 bold | 120% | 0 normal |
| `txt-display-m-extrabold-uppercase` | -> 48px | -> 66px | -> 84px | 800 extrabold + uppercase | 120% | -1% tight |
| `txt-display-l-semibold` | -> 48px | -> 72px | -> 96px | 600 semibold | 120% | -1% tight |
| `txt-display-l-bold` | -> 48px | -> 72px | -> 96px | 700 bold | 120% | -1% tight |
| `txt-display-l-extrabold-uppercase` | -> 48px | -> 72px | -> 96px | 800 extrabold + uppercase | 120% | -1% tight |
| `txt-display-xl-semibold` | -> 48px | -> 84px | -> 108px | 600 semibold | 120% | -1% tight |
| `txt-display-xl-bold` | -> 48px | -> 84px | -> 108px | 700 bold | 120% | -1% tight |
| `txt-display-xl-extrabold-uppercase` | -> 48px | -> 84px | -> 108px | 800 extrabold + uppercase | 120% | -1% tight |

---

## Tracking tokens (letter spacing)

| Tailwind class | CSS variable | Value |
|---|---|---|
| `tracking-tighter` | `--tracking-tighter` | -2% |
| `tracking-tight` | `--tracking-tight` | -1% |
| `tracking-normal` | `--tracking-normal` | 0 |
| `tracking-wide` | `--tracking-wide` | 1% |
| `tracking-wider` | `--tracking-wider` | 2% |

> Tracking is baked into each `txt-*` utility — you rarely need these standalone.
> Only use them when overriding tracking in a specific context.

---

## Leading tokens (line height)

| Tailwind class | CSS variable | Value | Used by |
|---|---|---|---|
| `leading-none` | (Tailwind built-in) | 100% | Button links, tight stacking (rare) |
| `leading-tight` | `--leading-tight` | 120% | Headlines, Display |
| `leading-normal` | `--leading-normal` | 140% | Labels, Body |
| `leading-wide` | `--leading-wide` | 160% | (available but not used by default utilities) |

> Leading is baked into each `txt-*` utility. The key distinction: **body uses 140%**
> (comfortable reading), **headlines use 120%** (compact stacking). This is why
> headline and body at the same font size look different.

---

## Base tokens

| Token | Value | Usage |
|---|---|---|
| `--text-base` | 16px | Root font size (set on `<html>`) |
| `--text-base-line-height` | 24px | Root line height |

---

## Feature defaults

| Feature | Default | Notes |
|---|---|---|
| **Case** | Sentence case | Uppercase only for short labels (`txt-label-*-bold-uppercase`, `txt-headline-*-extrabold-uppercase`) |
| **Numbers** | Tabular figures in data/UI | Proportional allowed in editorial copy |
| **Minimum body size** | 16px (1rem) | 14px only in dense UI; 12px very sparingly (labels only) |
| **Line length** | 60-80 characters | 40-60 on small screens. Use `max-w-prose` (~65ch) on paragraphs |
| **Links** | Underlined by default | Only remove underline with a clear alternate affordance |

---

## Typographic helper utilities

Tailwind built-in utilities recommended for use alongside `txt-*`:

| Utility | What it does | When to use |
|---|---|---|
| `text-pretty` | `text-wrap: pretty` — avoids orphans/widows | Apply to all body text elements |
| `text-balance` | `text-wrap: balance` — even line lengths | Apply to headlines and short text blocks |
| `max-w-prose` | `max-width: 65ch` — controlled reading width | Apply to paragraph or body text containers |
| `hyphens-auto` | `hyphens: auto` — automatic hyphenation | Use on narrow columns where long words break layout |
| `hyphens-none` | `hyphens: none` — disable hyphenation | Default — use explicitly when overriding `hyphens-auto` |
| `underline` | Underline decoration | Links, emphasis in specific contexts |
| `uppercase` | `text-transform: uppercase` | Prefer the `-uppercase` weight variants; only use standalone when composing custom utilities |

---

## Additive modifiers

When the predefined `txt-*` utilities don't provide the exact combination you need,
you can compose a base utility with standalone modifiers. This is the exception, not
the rule — prefer the named `txt-*` utilities when they exist.

| Modifier | What it controls | Values |
|---|---|---|
| `font-{weight}` | Font weight | `font-normal` (400), `font-medium` (500), `font-semibold` (600), `font-bold` (700), `font-extrabold` (800) |
| `leading-{value}` | Line height | `leading-none` (100%), `leading-tight` (120%), `leading-normal` (140%), `leading-wide` (160%) |
| `tracking-{value}` | Letter spacing | `tracking-tighter` (-2%), `tracking-tight` (-1%), `tracking-normal` (0), `tracking-wide` (1%), `tracking-wider` (2%) |

> Example: `txt-body-m-base font-semibold leading-tight` — body-m sizing with custom
> weight and tighter leading. Only use `-base` utilities for composition, never
> the named weight variants (e.g. don't do `txt-body-m-bold font-semibold`).

---

## Decision rules ("Spielregeln")

### Choosing a category
- **Default to `txt-body-m-regular`** for general UI text. This is the system's baseline.
- **Use labels** for small, supportive text: tag text, overlines, badge labels, chip text, table headers. Labels don't scale — they stay fixed.
- **Use headlines** for anything that structures content: section titles, card titles, modal titles, page titles. The tight leading and heavier weights separate them from body.
- **Use display** only for hero sections, marketing banners, and splash screens. Never for regular page content.

### Choosing a size
- **Work down from `m`**, not up from `s`. If `m` works, use it. Only go smaller if space is tight, larger if hierarchy demands it.
- **Don't skip more than 2 sizes** in the same view — `txt-headline-5xl` next to `txt-body-s` collapses the scale.
- **Labels have only 2 sizes** (`s` and `m`). If you need bigger "label-like" text, it's probably a headline.

### Choosing a weight
- **`regular`** (400) for body text — the default reading weight.
- **`medium`** (500) for subtle emphasis within body text.
- **`semibold`** (600) for strong emphasis, active states, selected items.
- **`bold`** (700) for headings and primary emphasis.
- **`extrabold-uppercase`** (800) for display/headline only — aggressive brand statements.
- **`bold-uppercase`** (700) for labels only — tags, badges, overlines.

### Readability constraints
- **Apply `text-pretty`** to body text elements to avoid orphans and widows.
- **Apply `text-balance`** to headlines for even line lengths.
- **Apply `max-w-prose`** to paragraph containers to keep line length at ~65ch.
- **Never go below 12px** (0.75rem) — that's `txt-label-s`, the absolute minimum.
- **Don't stretch or squash fonts** — maintain aspect ratios and line height.
- Contrast, color-as-meaning, and reduced motion are cross-cutting concerns ->
  see [`concepts/accessibility.md`](../concepts/accessibility.md).

### Fluid sizing — what you need to know
- Labels are **static** — same size on all screens.
- Body scales from **laptop** (1024px) onward — mobile and tablet get the base size.
- Headlines scale from **tablet** (640px) for 2xl+ sizes, from **laptop** for smaller sizes.
- Display scales aggressively from **mobile** — hero text that fills the viewport.
- **Never add responsive overrides** like `laptop:txt-headline-xl-bold` — the fluid system handles this.

---

## Anti-patterns

- ❌ `font-size: 14px` or `text-[14px]` — raw size. **Use** `txt-body-s-regular` or `txt-label-m-regular`.
- ❌ `font-weight: 700` or `font-bold` — raw weight. **Use** the `-bold` suffix: `txt-body-m-bold`.
- ❌ `letter-spacing: 0.5px` — raw spacing. **Use** `txt-*` utilities (tracking is baked in).
- ❌ `laptop:txt-headline-xl-bold` — responsive override. The fluid system handles scaling automatically.
- ❌ Using `txt-display-*` for a card title — wrong category. **Use** `txt-headline-*`.
- ❌ Using `txt-label-*` for body text — labels have wider tracking optimised for short strings, not prose.
- ❌ Mixing `font-sans` with manual size/weight/leading — recreating what `txt-*` already provides.
- ❌ Using Futura ND (`futurand.css`) in new components — legacy only.
- ❌ Body text below 16px without justification — 14px only in dense UI, 12px only for labels.
- ❌ Paragraphs without `max-w-prose` — uncontrolled line length hurts readability.
- ❌ Headlines without `text-balance` — causes uneven, ragged line breaks.
- ❌ Using `uppercase` on body text or long strings — only for short labels and brand statements.

---

## HTML element defaults

The `text-common-styles` utility maps HTML elements to the typography scale:

| Element | Typography utility |
|---|---|
| `<h1>` | `txt-headline-4xl` |
| `<h2>` | `txt-headline-3xl` |
| `<h3>` | `txt-headline-2xl` |
| `<h4>` | `txt-headline-l` |
| `<h5>` | `txt-headline-m` |
| `<p>` | `txt-body-m` |
| `<body>` | `text-body-s` (via `@layer base`) |

> These defaults apply inside `text-common-styles` scopes (CMS content, rich text).
> In Vue components, always use explicit `txt-*` utilities — don't rely on element defaults.

---

## Examples

### Do — card with headline and body

```html
<div class="bg-solid border border-main rounded-m p-6">
  <h3 class="txt-headline-l-bold text-main">Product overview</h3>
  <p class="txt-body-m-regular text-subtle mt-2">A short description of this product.</p>
  <span class="txt-label-s-bold-uppercase text-primary mt-4 inline-block">Featured</span>
</div>
```

### Do — hero section with display text

```html
<section class="bg-primary-main p-12">
  <h1 class="txt-display-l-extrabold-uppercase text-inverse">OMR Festival 2026</h1>
  <p class="txt-body-xl-regular text-inverse mt-4">The biggest marketing event in Europe.</p>
</section>
```

### Don't — raw font values

```html
<h3 class="text-[18px] font-bold leading-[1.2]">Title</h3>
```
**Why wrong:** bypasses the fluid system, tracking, and font-stack. **Use** `txt-headline-l-bold`.

### Don't — responsive override on fluid text

```html
<h2 class="txt-headline-3xl-bold laptop:txt-headline-4xl-bold">Title</h2>
```
**Why wrong:** the fluid `clamp()` already scales between breakpoints. Adding responsive variants creates jumps.

---

## Cross-references

- [`color.md`](./color.md) — text colours pair with typography: `text-main` + `txt-body-m-regular`
- [`breakpoints.md`](./breakpoints.md) (todo) — tablet (640px) and laptop (1024px) drive fluid scaling
- [`spacing.md`](./spacing.md) — vertical rhythm between text elements
- [`../concepts/visual-hierarchy.md`](../concepts/visual-hierarchy.md) (todo) — how typography weight and colour combine for emphasis
- [`../concepts/density-and-rhythm.md`](../concepts/density-and-rhythm.md) (todo) — spacing between typographic elements
- [`../concepts/accessibility.md`](../concepts/accessibility.md) (todo) — contrast 4.5:1, color-as-meaning, reduced motion (cross-cutting)
- [`../CLAUDE.md`](../CLAUDE.md) — agent rules
