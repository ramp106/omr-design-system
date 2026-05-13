---
title: Sizing
type: foundation
status: stable
last_updated: 2026-05-12
related: [spacing.md, breakpoints.md, typography.md, color.md, radius.md]

tokens:
  # === Inherited scale — same 4px base as spacing ===
  scale:
    inherits-from: "spacing.md"
    note: "h-*, w-*, size-*, min-w-*, min-h-*, max-h-* all share the spacing scale (0 → 96, 4px base unit). See spacing.md for the full Standard (0–64px) and Extended (80–384px) tables."

  # === Keyword utilities ===
  keywords:
    width:
      w-auto:   { value: "auto",         usage: "Content-driven width (default for inline-block)" }
      w-full:   { value: "100%",         usage: "Fill parent's width — by far the most common keyword (159 uses)" }
      w-screen: { value: "100vw",        usage: "Full viewport width — rare, use sparingly" }
      w-fit:    { value: "fit-content",  usage: "Sized to content with min/max constraints" }
      w-min:    { value: "min-content",  usage: "Smallest content (e.g., longest unbreakable word)" }
      w-max:    { value: "max-content",  usage: "Widest content without wrapping" }
    height:
      h-auto:   { value: "auto",         usage: "Content-driven height (default)" }
      h-full:   { value: "100%",         usage: "Fill parent's height (99 uses)" }
      h-screen: { value: "100vh",        usage: "Full viewport height" }
      h-fit:    { value: "fit-content",  usage: "Sized to content with constraints" }
      h-min:    { value: "min-content",  usage: "Smallest possible content height" }
      h-max:    { value: "max-content",  usage: "Tallest content without overflow" }

  # === size-* shorthand (Tailwind v4) ===
  size-shorthand:
    pattern: "size-N"
    expands-to: "h-N w-N"
    description: "Tailwind v4 shorthand for equal height and width"
    usage: "Square elements: icons, avatars, square buttons"
    real-example: "IconButton.vue uses size-8/10/12/16 for xs/s/m/l variants"

  # === Fractional widths (and heights) ===
  fractional-dimensions:
    width-pattern: "w-<num>/<denom>"
    height-pattern: "h-<num>/<denom>"
    description: "Tailwind generates any fraction you write; resolves to a percentage"
    common-fractions: ["1/2", "1/3", "2/3", "1/4", "3/4", "1/5", "2/5", "3/5", "4/5", "1/6", "5/6", "1/12", "5/12", "7/12", "11/12"]
    note: "Same system applies to heights (h-1/2 etc.)"

  # === Max-width scale ===
  max-widths:
    named:
      max-w-xs:    { rem: "20rem", px: 320,  usage: "Small constrained surface (narrow popover)" }
      max-w-sm:    { rem: "24rem", px: 384,  usage: "Compact dialog" }
      max-w-md:    { rem: "28rem", px: 448,  usage: "Medium dialog" }
      max-w-lg:    { rem: "32rem", px: 512,  usage: "Larger dialog" }
      max-w-xl:    { rem: "36rem", px: 576,  usage: "Large dialog, focused content" }
      max-w-2xl:   { rem: "42rem", px: 672,  usage: "Constrained reading width (wider than prose)" }
      max-w-3xl:   { rem: "48rem", px: 768,  usage: "Medium content section" }
      max-w-4xl:   { rem: "56rem", px: 896,  usage: "Wider content section" }
      max-w-5xl:   { rem: "64rem", px: 1024, usage: "Large content section" }
      max-w-6xl:   { rem: "72rem", px: 1152, usage: "Very wide content" }
      max-w-7xl:   { rem: "80rem", px: 1280, usage: "Page-level wide layout" }
      max-w-prose: { value: "~65ch",         usage: "Optimal reading width for paragraphs — see typography.md" }
    keywords:
      max-w-full:   { value: "100%", usage: "Don't exceed parent width (common safety override)" }
      max-w-none:   { value: "none", usage: "Explicitly remove a max-width constraint" }
      max-w-screen: { value: "100vw", usage: "Don't exceed viewport — rare" }

  # === Aspect ratios ===
  aspect-ratios:
    named:
      aspect-auto:   { value: "auto",   usage: "Default — no constraint" }
      aspect-square: { value: "1 / 1",  usage: "1:1 — avatars, icon thumbnails, symmetric tiles" }
      aspect-video:  { value: "16 / 9", usage: "16:9 — video embeds, hero media" }
    arbitrary-syntax:
      pattern: "aspect-[num]/[denom]"
      examples-in-code: ["aspect-9/16 (2x, vertical video)", "aspect-4/3 (1x)", "aspect-16/9 (1x, same as aspect-video)"]
      note: "Arbitrary aspect ratios explicitly allowed — no scale to violate"

  # === Object-fit + position (pairs with explicit dimensions) ===
  object-fit:
    object-cover:      { behavior: "Scale to fill, preserve aspect; content may crop",            usage: "Hero images, card thumbnails — most common" }
    object-contain:    { behavior: "Scale to fit, preserve aspect; letterboxing possible",         usage: "Logos, illustrations (full-image reveal)" }
    object-fill:       { behavior: "Stretch to fill; aspect ratio not preserved",                  usage: "Rarely the right choice" }
    object-none:       { behavior: "Original size; position via object-position",                  usage: "Sprite images, pixel-perfect content" }
    object-scale-down: { behavior: "Smaller of contain or none",                                   usage: "Don't enlarge small images" }
    note: "Pair with object-{position} utilities for placement (object-center is default)"

  # === Icon sizes (OMR custom) ===
  icon-sizes:
    source: "packages/config-tailwind/styles/lucide-icons.css"
    lucide-icon-xs: { tailwind: "lucide-icon-xs", composes: "h-3 w-3",   px: 12, usage: "Dense UI, badges, inline meta",        uses-in-code: 12 }
    lucide-icon-s:  { tailwind: "lucide-icon-s",  composes: "h-4 w-4",   px: 16, usage: "Default inline icons — most common",   uses-in-code: 81 }
    lucide-icon-m:  { tailwind: "lucide-icon-m",  composes: "h-6 w-6",   px: 24, usage: "Primary actions, prominent UI",        uses-in-code: 37 }
    lucide-icon-l:  { tailwind: "lucide-icon-l",  composes: "h-8 w-8",   px: 32, usage: "Standout icons, large buttons",        uses-in-code: 6 }
    lucide-icon-xl: { tailwind: "lucide-icon-xl", composes: "h-12 w-12", px: 48, usage: "Hero illustrations, marketing icons",  uses-in-code: 7 }

  # === Composite utilities (OMR custom) ===
  composite-utilities:
    full-bleed:
      source: "packages/config-tailwind/styles/utilities.css"
      definition: "@utility full-bleed { @apply relative left-1/2 -translate-x-1/2; width: calc(100vw - var(--scrollbar-width, 0px)); }"
      use-case: "Child element spans the full viewport width even though its parent is constrained (e.g. full-bleed image inside responsive-container)"
      runtime-dependency:
        variable: "--scrollbar-width"
        set-by: "packages/core-ui/src/components/HorizontalSlider/FullBleed.vue (JS, document.documentElement.style.setProperty)"
        note: "Runtime-measured, not a static design token. Falls back to 0px if Vue runtime isn't present."

  # === Known drifts ===
  known-drifts:
    button-min-widths:
      examples: ["w-[100px] (31x — button xs/s min-width)", "w-[160px] (34x — button m/l min-width)"]
      action: "w-[160px] = w-40 (trivial fix). w-[100px] is genuinely off-scale (nearest: w-24 = 96px or w-28 = 112px) — needs design review."
    arbitrary-widths:
      examples: ["w-[300px] (15x)", "w-[500px] (9x)", "w-[250px] (8x)", "w-[220px] (3x)"]
      action: "Most need design review — many are dropdown/modal widths that should be on-scale or component-tokenized."
    arbitrary-max-widths:
      examples: ["max-w-[500px] (8x — fix to max-w-lg per dev confirmation)", "max-w-[1440px] (4x — use max-w-content token)", "max-w-[1096px] (3x — fix to max-w-6xl per dev confirmation)", "max-w-[300px] (2x)", "max-w-[288px] (2x — on-scale = max-w-72)", "max-w-[220px] (3x)", "max-w-[250px] (3x)", "max-w-[70%] (2x)"]
      action: "max-w-[500px] → max-w-lg (12px drift, dev-confirmed). max-w-[1096px] → max-w-6xl (56px drift, dev-confirmed). max-w-[1440px] → max-w-content token. max-w-[288px] = max-w-72 (trivial). Others need design review."
    arbitrary-heights:
      examples: ["h-[70px] (6x)", "h-[300px] (6x)", "h-[96px] (5x — on-scale = h-24)", "min-h-[420px] (3x)"]
      action: "h-[96px] = h-24 (trivial fix). h-[70px] needs design review (nearest h-16=64 or h-20=80). h-[300px] = h-72 (288) or h-80 (320)."
---

# Sizing

## TL;DR

OMR sizing **inherits Tailwind v4's scale and utilities** — the same 4px-based scale that powers spacing. The only OMR-custom layer is a small set of icon-size utilities (`lucide-icon-*`) and one composite utility (`full-bleed`). Always pick a Tailwind utility (`size-*`, `max-w-*`, `aspect-*`) over arbitrary values — most "off-scale" values in the codebase have an on-scale equivalent.

---

## Architecture

| Layer | What it is | Where it lives |
|---|---|---|
| **Inherited scale** | `--spacing` (4px) drives `h-*`, `w-*`, `size-*`, `min-w-*`, `min-h-*`, `max-h-*` | Tailwind v4 default (`--spacing: 0.25rem`) |
| **Keyword utilities** | `w-auto`, `w-full`, `w-screen`, `w-fit`, `w-min`, `w-max` (and `h-*` analogs) | Tailwind v4 |
| **Max-width scale** | `max-w-xs` … `max-w-7xl` + `max-w-prose` + keywords | Tailwind v4 |
| **Aspect ratios** | `aspect-square`, `aspect-video`, arbitrary `aspect-[N/N]` | Tailwind v4 |
| **Icon sizes (OMR custom)** | `lucide-icon-{xs,s,m,l,xl}` | `packages/config-tailwind/styles/lucide-icons.css` |
| **`full-bleed` (OMR custom)** | Edge-to-edge child inside constrained parent | `packages/config-tailwind/styles/utilities.css` |
| **Page-level width tokens** | `--width-tablet/laptop/desktop/wide` (640/1024/1440/1920px) | `theme.css`; see [`breakpoints.md`](./breakpoints.md) |

> **No OMR-custom h/w/size scale.** Unlike colors or typography (which have full semantic layers), sizing reuses Tailwind v4's utilities directly. The two OMR-side declarations are deliberately narrow: icon dimensions (semantic family) and one layout-mechanic utility (`full-bleed`).

---

## Width & height scale

Same scale as [`spacing.md`](./spacing.md) — the `--spacing` variable (4px base) powers all of:
- `w-*` (width), `h-*` (height)
- `size-*` (shorthand for `h-N w-N`)
- `min-w-*`, `min-h-*`, `max-h-*`

The **Standard range** (0–64px, steps `0`–`16`) covers component dimensions; the **Extended range** (80–384px, steps `20`–`96`) covers section, full-width, and marketing layouts. See [`spacing.md`](./spacing.md) for the full scale table.

> **Don't reach for arbitrary values** like `w-[100px]` when an on-scale equivalent exists. See [Known drifts](#known-drifts) for the current code-side audit.

---

## Keyword utilities

For sizes that depend on context rather than a fixed value.

### Width keywords

| Utility | Value | When to use |
|---|---|---|
| `w-auto` | `auto` | Content-driven width (default for inline-block) |
| `w-full` | `100%` | Fill parent's width — by far the most common keyword (159×) |
| `w-screen` | `100vw` | Full viewport width — rare, use sparingly |
| `w-fit` | `fit-content` | Sized to content with min/max constraints |
| `w-min` | `min-content` | Sized to smallest content (e.g., longest unbreakable word) |
| `w-max` | `max-content` | Sized to widest content without wrapping |

### Height keywords

| Utility | Value | When to use |
|---|---|---|
| `h-auto` | `auto` | Content-driven height (default) |
| `h-full` | `100%` | Fill parent's height (99×) |
| `h-screen` | `100vh` | Full viewport height |
| `h-fit` | `fit-content` | Sized to content with constraints |
| `h-min` | `min-content` | Smallest possible content height |
| `h-max` | `max-content` | Tallest content without overflow |

---

## `size-*` shorthand

Tailwind v4 introduced `size-N` as shorthand for `h-N w-N`. Use it whenever an element should have equal width and height (most icons, avatars, square buttons).

```html
<!-- equivalent -->
<button class="h-10 w-10">…</button>
<button class="size-10">…</button>
```

**Real-world use:** `IconButton.vue` uses `size-8 / size-10 / size-12 / size-16` for its xs / s / m / l variants. When you see `size-*` in code, it's typically a square interactive element.

---

## Fractional widths (and heights)

Tailwind generates any fraction you write — `w-<num>/<denom>` resolves to a percentage. The same fractions work for heights.

**Common fractions:**

| Fraction family | Examples |
|---|---|
| Halves | `w-1/2` |
| Thirds | `w-1/3`, `w-2/3` |
| Quarters | `w-1/4`, `w-3/4` |
| Fifths | `w-1/5`, `w-2/5`, `w-3/5`, `w-4/5` |
| Sixths | `w-1/6`, `w-5/6` |
| Twelfths | `w-1/12` … `w-11/12` |

**When to use fractions:**
- ✅ Side-by-side layouts that don't need a full grid
- ✅ Asymmetric splits (`w-1/3` + `w-2/3`)
- ❌ More than 2–3 children — use Flex/Grid + `gap-*` instead

---

## Max-width scale

Named max-widths cover the typical "constrained surface" range, from compact dialogs to full-page wrappers.

| Utility | rem | px | When to use |
|---|---|---|---|
| `max-w-xs` | 20rem | 320 | Small constrained surface (narrow popover) |
| `max-w-sm` | 24rem | 384 | Compact dialog |
| `max-w-md` | 28rem | 448 | Medium dialog |
| `max-w-lg` | 32rem | 512 | Larger dialog |
| `max-w-xl` | 36rem | 576 | Large dialog, focused content |
| `max-w-2xl` | 42rem | 672 | Constrained reading width (wider than prose) |
| `max-w-3xl` | 48rem | 768 | Medium content section |
| `max-w-4xl` | 56rem | 896 | Wider content section |
| `max-w-5xl` | 64rem | 1024 | Large content section |
| `max-w-6xl` | 72rem | 1152 | Very wide content |
| `max-w-7xl` | 80rem | 1280 | Page-level wide layout |
| `max-w-prose` | — | ~65ch | **Optimal reading width** for paragraphs |

**Keywords:** `max-w-full` (100%, common safety override), `max-w-none` (remove a constraint), `max-w-screen` (100vw, rare).

> **For prose, use `max-w-prose`** (see [`typography.md`](./typography.md)) — it scales with font-size and respects the eye's reading-width preferences. Don't reach for `max-w-2xl` or arbitrary `max-w-[Npx]` for paragraphs.

---

## Aspect ratios

When an element must preserve a fixed proportion (video embeds, hero media, card thumbnails).

### Named ratios

| Utility | Value | When to use |
|---|---|---|
| `aspect-auto` | `auto` | Default — no constraint |
| `aspect-square` | `1 / 1` | Avatars, icon thumbnails, symmetric tiles |
| `aspect-video` | `16 / 9` | Video embeds, hero media |

### Arbitrary aspect ratios

Use bracket syntax for custom ratios:

```html
<div class="aspect-9/16">…</div>   <!-- vertical video / mobile-first media -->
<div class="aspect-4/3">…</div>    <!-- classic photo -->
<div class="aspect-21/9">…</div>   <!-- cinemascope -->
```

In omr-js, the following arbitrary ratios appear: `aspect-9/16`, `aspect-4/3`, `aspect-16/9`. **Arbitrary aspect-ratio syntax is explicitly allowed** — there's no "scale" for aspect ratios to violate.

### Pairing with `object-fit`

When the content (image, video) doesn't naturally match the aspect ratio, `object-fit` controls behavior — see next section.

---

## Object-fit (image / video behavior)

When an element with fixed dimensions or aspect ratio contains media, `object-fit` controls how the media scales:

| Utility | Behavior | When to use |
|---|---|---|
| `object-cover` | Scale to fill, preserving aspect — content may crop | Hero images, card thumbnails (most common) |
| `object-contain` | Scale to fit, preserving aspect — letterboxing possible | Logos, illustrations (full-image reveal) |
| `object-fill` | Stretch to fill — aspect not preserved | Rarely the right choice |
| `object-none` | Original size; position via `object-position` | Sprite images, pixel-perfect content |
| `object-scale-down` | Smaller of `contain` or `none` | Don't enlarge small images |

Pair with `object-{position}` utilities (`object-center` is default) for placement.

> **Why this is in sizing.md:** object-fit doesn't make sense without explicit dimensions on the element. The two concepts are inseparable in practice.

---

## Icon sizes (OMR-custom)

Five semantic icon-size utilities that map to fixed pixel dimensions. Defined in `packages/config-tailwind/styles/lucide-icons.css`.

| Utility | Composes | px | When to use | Uses in code |
|---|---|---|---|---|
| `lucide-icon-xs` | `h-3 w-3` | 12 | Dense UI, badges, inline meta | 12× |
| `lucide-icon-s` | `h-4 w-4` | 16 | **Default inline icons** — most common | 81× |
| `lucide-icon-m` | `h-6 w-6` | 24 | Primary actions, prominent UI | 37× |
| `lucide-icon-l` | `h-8 w-8` | 32 | Standout icons, larger buttons | 6× |
| `lucide-icon-xl` | `h-12 w-12` | 48 | Hero illustrations, marketing | 7× |

### Decision rule — which icon size when

- **`lucide-icon-s` is the default.** When unsure, pick this.
- **Step up to `lucide-icon-m`** for primary CTAs, navigation items, or when the icon is the main affordance.
- **Step down to `lucide-icon-xs`** for badges, dense tables, or meta lines.
- **Use `-l` / `-xl` only for hero / marketing contexts** — these are rare (6 + 7 uses across the entire codebase combined).

---

## `full-bleed` composite (OMR-custom)

Source: `packages/config-tailwind/styles/utilities.css`

```css
@utility full-bleed {
  @apply relative left-1/2 -translate-x-1/2;
  width: calc(100vw - var(--scrollbar-width, 0px));
}
```

**Use case:** A child element that should span the full viewport width even though its parent is constrained (e.g., a full-bleed image inside a `responsive-container`).

### Runtime dependency on `--scrollbar-width`

The `--scrollbar-width` CSS variable used in the `calc()` is **not a static design token** — it's measured at runtime by `packages/core-ui/src/components/HorizontalSlider/FullBleed.vue`:

```js
document.documentElement.style.setProperty('--scrollbar-width', `${scrollbarWidth}px`)
```

If `--scrollbar-width` is unset (no Vue runtime present, SSR, isolated tests), the `0px` fallback applies — meaning `100vw` includes the scrollbar area on Windows/Linux. Generally safe, but worth knowing for testing contexts.

---

## Decision rules ("Spielregeln")

### `size-*` vs separate `h-*` `w-*`

- **Use `size-N` shorthand** when both dimensions are equal (icons, avatars, square buttons).
- **Use separate `h-*` `w-*`** when dimensions differ.
- Don't mix them in one component (`size-10 h-12`) — pick one model.

### `min-h-*` vs `h-*`

- **Use `min-h-*`** for a baseline height that lets content overflow grow the element.
- **Use `h-*`** for fixed-height elements where overflow should clip (`overflow-hidden`) or scroll.
- For full-page layouts, prefer `min-h-screen` over `h-screen` — content that exceeds the viewport should be scrollable, not clipped.

### `max-w-*` selection

- **For prose** (paragraphs, long body copy): `max-w-prose` (~65ch). See [`typography.md`](./typography.md).
- **For dialogs / modals**: `max-w-md` (448) / `max-w-lg` (512) / `max-w-xl` (576) depending on content density.
- **For page-level containers**: `max-w-7xl` (1280) is common; otherwise use `responsive-container` for the canonical pattern (see [`breakpoints.md`](./breakpoints.md)).
- **Avoid arbitrary `max-w-[Npx]`** unless documented — the named scale almost always has a fitting step.

### Touch target baseline

Any interactive element should reserve at least **44 × 44 px** of hit area — either `size-11` (44px) explicitly, or a smaller visual size with invisible padding extending the click area. WCAG 2.5.5 requirement.

This rule cross-cuts color/accessibility — the full normative version belongs in [`concepts/accessibility.md`](../concepts/accessibility.md) (todo). Cited here as a sizing-relevant reminder.

---

## Anti-patterns

- ❌ `width: 100px` or `style="width: 100px"` — raw CSS. **Use** a Tailwind utility.
- ❌ `w-[100px]`, `max-w-[1440px]`, `h-[300px]` — arbitrary values when an on-scale equivalent exists. (`w-24` = 96px or `w-28` = 112px; `max-w-7xl` ≈ 1280; `h-72` = 288 or `h-80` = 320.)
- ❌ `w-[160px]` — exists on-scale as `w-40` (160px). Trivial fix.
- ❌ Mixing `size-N` with separate `h-N w-M` in the same component — confusing intent.
- ❌ Using `h-screen` when `min-h-screen` is meant — `h-screen` clips content; `min-h-screen` lets content grow past the viewport.
- ❌ Using `w-screen` inside a container — produces overflow nightmares. Use `full-bleed` when you genuinely need viewport-width content.
- ❌ Setting a pixel-fixed dimension on something that holds variable text (button labels, badge counts) — breaks when text changes. Use `min-w-*` plus content sizing.
- ❌ Reaching for arbitrary `aspect-[24/9]` when `aspect-video` (16/9) or another sanctioned ratio works — exception: vertical (`9/16`) and cinemascope (`21/9`) are rare enough to allow.

---

## Known drifts

A non-trivial number of arbitrary sizing values appear in omr-js code. Documented for transparency; a separate code-side audit ticket can close most.

### Off-scale widths

| Pattern | Count | Action |
|---|---|---|
| `w-[100px]` | 31× | **Off-scale.** Mostly button min-widths. Nearest: `w-24` (96) or `w-28` (112). Needs design review. |
| `w-[160px]` | 34× | **On-scale** = `w-40`. Trivial fix. |
| `w-[300px]` | 15× | Off-scale; nearest `w-72` (288) or `w-80` (320). Design review. |
| `w-[500px]` | 9× | Off-scale; design review. |
| `w-[250px]` | 8× | Off-scale; nearest `w-60` (240) or `w-64` (256). Design review. |
| `w-[220px]` | 3× | Off-scale; design review. |

### Off-scale heights

| Pattern | Count | Action |
|---|---|---|
| `h-[70px]` | 6× | Off-scale. `h-16` (64) or `h-20` (80) probably intended. |
| `h-[300px]` | 6× | Off-scale; `h-72` (288) or `h-80` (320) nearest. |
| `h-[96px]` | 5× | **On-scale** = `h-24`. Trivial fix. |
| `min-h-[420px]` | 3× | Off-scale; design call (`min-h-96` = 384 or arbitrary rem). |

### Off-scale max-widths

| Pattern | Count | Action |
|---|---|---|
| `max-w-[500px]` | 8× | **Fix to `max-w-lg`** (512 px, 12 px drift). Dev-confirmed: drift, not intentional design. Mostly in `SectionStyledHero` variants. |
| `max-w-[1440px]` | 4× | Use `max-w-content` token (1440 px) — see [`spacing.md`](./spacing.md#page-level-content-width--max-w-content). |
| `max-w-[1096px]` | 3× | **Fix to `max-w-6xl`** (1152 px, 56 px drift). Dev-confirmed: drift, not intentional design. In `SectionCta`, `SectionFeaturesTable`. Visual spot-check recommended for the 56 px diff. |
| `max-w-[300px]` | 2× | Off-scale. |
| `max-w-[288px]` | 2× | **On-scale** = `max-w-72` (288 on the spacing scale). Trivial fix. |
| `max-w-[220px]` | 3× | Off-scale. |
| `max-w-[250px]` | 3× | Off-scale; near `max-w-60` (240). |
| `max-w-[70%]` | 2× | Edge case; percentages aren't on the spacing scale but can be correct. Investigate. |

> **Action:** the on-scale-equivalent fixes (`w-[160px]` → `w-40`, `h-[96px]` → `h-24`, `max-w-[288px]` → `max-w-72`, `max-w-[1440px]` → reference `--width-desktop`) can be done mechanically. The genuinely off-scale ones need a design conversation.

---

## Cross-references

- [`spacing.md`](./spacing.md) — shared 4px-based scale (`h-*`, `w-*`, `size-*` use the same steps)
- [`breakpoints.md`](./breakpoints.md) — `--width-tablet/laptop/desktop/wide` tokens and `responsive-container` composite
- [`typography.md`](./typography.md) — `max-w-prose` is the canonical prose-width helper
- [`color.md`](./color.md) — borders and backgrounds pair with size to define surfaces
- [`radius.md`](./radius.md) — radius scales independently; nested-radius rule applies when sized containers nest
- [`../concepts/component-padding.md`](../concepts/component-padding.md) — component-level padding tokens
- [`../concepts/component-sizing.md`](../concepts/component-sizing.md) (todo) — component-specific heights/widths (Button `h-8/10/12/16`, IconButton `size-8/10/12/16`, InputField `h-8/10/12`, Modal/Avatar widths, etc.)
- [`../concepts/accessibility.md`](../concepts/accessibility.md) (todo) — touch-target normative rule (44 × 44 px) and related guidance
- [`../CLAUDE.md`](../CLAUDE.md) — agent rules
