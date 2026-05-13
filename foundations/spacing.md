---
title: Spacing
type: foundation
status: stable
last_updated: 2026-05-12
related: [typography.md, breakpoints.md, sizing.md, radius.md]

tokens:
  base-unit:
    css_var: "--spacing"
    rem: "0.25rem"
    px: 4
    source: "Tailwind v4 default (not redefined in OMR's theme.css)"

  # === Standard range (0–64px) — component + section-level spacing ===
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
    "9":   { rem: "2.25rem",  px: 36, tailwind: "p-9" }
    "10":  { rem: "2.5rem",   px: 40, tailwind: "p-10" }
    "11":  { rem: "2.75rem",  px: 44, tailwind: "p-11" }
    "12":  { rem: "3rem",     px: 48, tailwind: "p-12" }
    "14":  { rem: "3.5rem",   px: 56, tailwind: "p-14" }
    "16":  { rem: "4rem",     px: 64, tailwind: "p-16" }

  # === Extended range (80–384px) — section padding, marketing, hero ===
  scale-extended:
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

  # === Responsive page padding (OMR-custom layout tokens) ===
  # Descriptive concept: "responsive page padding" / "page gutters"
  # Use case: page-level + section-level horizontal padding.
  # NOT for component internals (use padding-{component} tokens instead).
  hspace:
    hspace-sm:
      mobile: 8
      tablet: 12
      laptop: 16
      desktop: 32
      wide: 32
      tailwind: "px-2 tablet:px-3 laptop:px-4 desktop:px-8"
      usage: "Tight gutters — dense pages (dashboards, list-heavy views)"
    hspace-md:
      mobile: 16
      tablet: 24
      laptop: 32
      desktop: 64
      wide: 64
      tailwind: "px-4 tablet:px-6 laptop:px-8 desktop:px-16"
      usage: "Standard page gutters — default for most pages. responsive-container composes this."
    hspace-lg:
      mobile: 24
      tablet: 32
      laptop: 48
      desktop: 96
      wide: 96
      tailwind: "px-6 tablet:px-8 laptop:px-12 desktop:px-24"
      usage: "Generous gutters — feature pages, hero sections"
    hspace-xl:
      mobile: 32
      tablet: 48
      laptop: 64
      desktop: 176
      wide: 176
      tailwind: "px-8 tablet:px-12 laptop:px-16 desktop:px-44"
      usage: "Editorial-extreme gutters — brand pages, narrow-focused content"

  # === Responsive section padding (OMR-custom layout tokens) ===
  # Descriptive concept: "responsive section padding" / "vertical section rhythm"
  # Use case: vertical padding between/within sections at page level.
  # NOT for component internals.
  vspace:
    vspace-none:
      mobile: 0
      laptop: 0
      desktop: 0
      tailwind: "py-0"
      usage: "Explicit zero — sections that abut without gap"
    vspace-xs:
      mobile: 16
      tablet: 16
      laptop: 24
      desktop: 24
      wide: 24
      tailwind: "py-4 laptop:py-6"
      usage: "Tight section separator"
    vspace-sm:
      mobile: 24
      tablet: 24
      laptop: 24
      desktop: 48
      wide: 48
      tailwind: "py-6 desktop:py-12"
      usage: "Standard section padding"
    vspace-md:
      mobile: 48
      tablet: 48
      laptop: 48
      desktop: 80
      wide: 80
      tailwind: "py-12 desktop:py-20"
      usage: "Medium section padding (rounded up from Figma 72 to Tailwind step 20 / 80px)"
    vspace-lg:
      mobile: 80
      tablet: 80
      laptop: 80
      desktop: 96
      wide: 96
      tailwind: "py-20 desktop:py-24"
      usage: "Large section padding (mobile/tablet/laptop rounded up from Figma 72)"
    vspace-xl:
      mobile: 128
      tablet: 128
      laptop: 128
      desktop: 144
      wide: 144
      tailwind: "py-32 desktop:py-36"
      usage: "Hero / generous-marketing section (mobile/tablet/laptop rounded up from Figma 120)"
    vspace-2xl:
      mobile: 208
      tablet: 208
      laptop: 208
      desktop: 240
      wide: 240
      tailwind: "py-52 desktop:py-60"
      usage: "Big marketing section (mobile/tablet/laptop rounded up from Figma 200)"
    vspace-3xl:
      mobile: 384
      tablet: 384
      laptop: 384
      desktop: 384
      wide: 384
      tailwind: "py-96"
      usage: "Maximum section padding — capped at Tailwind max. Non-responsive (Figma 400/480 reduced to 384)."
      note: "Figma defines 400 (mobile/tablet/laptop) and 480 (desktop+); both are beyond Tailwind's max scale step (96 = 384px). Both capped at 384, losing the responsive jump. Currently 0 uses in omr-js code."

  # === Page-level content width cap (OMR-custom token) ===
  max-w-content:
    css_var: "--max-w-content"
    value: "1440px"
    tailwind: "max-w-content"
    source: "to be defined in theme.css @theme block (separate code-side ticket)"
    usage: "Page-level content width cap — used by responsive-container to keep content from stretching beyond 1440px on wide viewports"
    figma-drift: "Figma container-max-width measures inner-content-width (336/616/976/1320/1320 px) — our max-w-content is the outer wrapper max-width (1440px). Inner content = max-w-content − 2 × hspace-md desktop padding (= 1312px). 8–24 px informational drift to Figma's responsive container-max-width values."

  # === Figma-only tokens (informational — not implemented in code) ===
  figma-only-tokens:
    gap-aliases:
      figma-tokens: ["gap-xs (4px)", "gap-sm (8px)", "gap-md (12px)", "gap-lg (16px)", "gap-xl (24px)", "gap-2xl (40px)"]
      reason-not-implemented: "Pure non-responsive semantic aliases over Tailwind's existing gap-N scale. No new pixel values. Implementing would create two ways to express the same value (gap-md ↔ gap-3) — friction for code reviews, AI agents, devs."
      code-equivalent: "Use Tailwind gap-N (gap-1 / gap-2 / gap-3 / gap-4 / gap-6 / gap-10) directly. Responsive layout gap use case is covered by the existing grid-gap composite (gap-4 desktop:gap-6)."
    paragraph-max-width:
      figma-token: "paragraph-max-width (352/632/768/768/768 px responsive)"
      reason-not-implemented: "Figma uses pixel-based width. OMR's canonical implementation is `max-w-prose` (typography.md) — ch-based, font-size-relative, typographically correct (45–75 chars per line), accessibility-friendly (scales with text zoom)."
      code-equivalent: "Use `max-w-prose` from typography.md. Both approaches aim at the same typographic goal; max-w-prose expresses it in font-relative terms."

  # === Figma drifts (consolidated inventory) ===
  figma-drifts:
    - { id: 1, drift: "hspace-md desktop value (Figma 64 vs current omr-js code 60)", direction: "code-side fix",  action: "Update responsive-container desktop:px-[60px] → desktop:px-16" }
    - { id: 2, drift: "hspace-lg desktop value (Figma 172 vs spec 96)",               direction: "figma-side fix", action: "Update Figma hspace-lg to ladder-consistent 96" }
    - { id: 3, drift: "hspace-xl new addition (not in Figma)",                       direction: "figma-side fix", action: "Add hspace-xl to Figma (32/48/64/176/176)" }
    - { id: 4, drift: "vspace-md desktop value (Figma 72 vs spec 80)",               direction: "figma-side fix", action: "Round Figma 72 → 80 (Tailwind step 20)" }
    - { id: 5, drift: "vspace-lg mobile/tablet/laptop value (Figma 72 vs spec 80)",  direction: "figma-side fix", action: "Round Figma 72 → 80" }
    - { id: 6, drift: "vspace-xl mobile/tablet/laptop value (Figma 120 vs spec 128)", direction: "figma-side fix", action: "Round Figma 120 → 128 (Tailwind step 32)" }
    - { id: 7, drift: "vspace-2xl mobile/tablet/laptop value (Figma 200 vs spec 208)", direction: "figma-side fix", action: "Round Figma 200 → 208 (Tailwind step 52)" }
    - { id: 8, drift: "vspace-3xl values (Figma 400/480 vs spec 384/384, non-responsive cap)", direction: "figma-side fix", action: "Cap at Tailwind max 384; document loss of responsive jump" }
    - { id: 9, drift: "Figma scopes for hspace-*/vspace-* are [GAP] only",            direction: "figma-side fix", action: "Update Figma scopes — hspace-* should be [LEFT_PADDING, RIGHT_PADDING]; vspace-* should be [TOP_PADDING, BOTTOM_PADDING]" }

  composite-utilities:
    responsive-container:
      source: "packages/config-tailwind/styles/utilities.css"
      canonical-composition: "hspace-md + desktop:max-w-content + mx-auto"
      values:
        mobile:  "px-4"
        tablet:  "px-6"
        laptop:  "px-8"
        desktop: "px-16 max-w-content mx-auto"
      code_drift: "current code ships `desktop:px-[60px]` and `desktop:max-w-[1440px]` — canonical is `desktop:px-16` (= hspace-md) + `desktop:max-w-content` (= 1440px via new token). Pending code-side refactor."
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
| **Responsive layout tokens (OMR-custom)** | `hspace-{sm,md,lg,xl}` (page padding), `vspace-{none,xs,sm,md,lg,xl,2xl,3xl}` (section padding), `max-w-content` (content cap) | `utilities.css` + `theme.css` |
| **Composite utilities** | `responsive-container`, `grid-container`, `grid-gap`, `card`, `separate-rows` | `utilities.css` |
| **Element defaults** | Vertical rhythm for `h1`–`h5`, `p`, `ul`, `ol`, `li`, `table`, `blockquote` | `text-common-styles` in `utilities.css`, `@layer base` in `theme.css` |

> **Foundation reuses Tailwind's default scale.** Unlike colors or typography,
> the base spacing scale has no OMR-specific token layer — it's Tailwind's
> default 4 px scale. The OMR layer sits *above* the scale: composite utilities,
> responsive layout tokens (`hspace-*` / `vspace-*` / `max-w-content`), and
> element rhythm.

> **Responsive layout spacing tokens are included.** Earlier drafts of this doc
> excluded the Figma `Custom.Website` tokens. That decision was reversed —
> the responsive `hspace-*`, `vspace-*`, and `max-w-content` are now part of
> OMR's product UI token system (see sections below). Two Figma tokens remain
> informational-only: `gap-*` aliases and `paragraph-max-width` — see
> [Figma-only tokens](#figma-only-tokens) below.

---

## Spacing scale

Tailwind's default 4px-based scale. Each step multiplies the base unit (`0.25rem` / 4px).
The full scale is split into two ranges below — the **standard range** covers
~80% of product-UI work; the **extended range** is reserved for section padding,
large vertical rhythm, and marketing/hero contexts.

### Standard range (0–64px)

The everyday vocabulary — covers both component-level spacing (`1`–`8`) and
section-level rhythm (`9`–`16`). If a value isn't here, you're probably in the
wrong range.

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
| `9` | 2.25rem | 36px | `p-9` |
| `10` | 2.5rem | 40px | `p-10` |
| `11` | 2.75rem | 44px | `p-11` |
| `12` | 3rem | 48px | `p-12` |
| `14` | 3.5rem | 56px | `p-14` |
| `16` | 4rem | 64px | `p-16` |

### Extended range (80–384px)

Larger steps for section-level padding on large screens, full-width hero
spacing, and marketing layouts. Anything starting at step `20` (80px) signals
a section, not a component.

| Step | rem | px | Tailwind class |
|---|---|---|---|
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
> Steps `9`–`16` cover section-level padding and large vertical rhythm. The
> extended range (`20` and above) is rare and usually marketing/hero context only.

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

## Responsive page padding — `hspace-*`

**Concept:** "Responsive page padding" (also called "page gutters") — horizontal padding that scales with viewport size. Use for **page-level** wrappers and section-level horizontal layouts. **Never** for component internals — components have their own non-responsive `padding-{component}` tokens (see [`concepts/component-padding.md`](../concepts/component-padding.md)).

The family has four sizes, all on Tailwind scale. **Use `hspace-md` by default** — it's what `responsive-container` composes internally.

| Token | Mobile | Tablet | Laptop | Desktop | Wide | Tailwind classes | When to use |
|---|---|---|---|---|---|---|---|
| `hspace-sm` | 8 | 12 | 16 | 32 | 32 | `px-2 tablet:px-3 laptop:px-4 desktop:px-8` | Tight gutters — dense pages (dashboards, list-heavy views) |
| `hspace-md` | 16 | 24 | 32 | 64 | 64 | `px-4 tablet:px-6 laptop:px-8 desktop:px-16` | **Standard page gutters** — default for most pages |
| `hspace-lg` | 24 | 32 | 48 | 96 | 96 | `px-6 tablet:px-8 laptop:px-12 desktop:px-24` | Generous gutters — feature pages, hero sections |
| `hspace-xl` | 32 | 48 | 64 | 176 | 176 | `px-8 tablet:px-12 laptop:px-16 desktop:px-44` | Editorial-extreme — brand pages, narrow-focused content |

```css
/* utilities.css — canonical post-refactor form */
@utility hspace-sm {
  @apply px-2 tablet:px-3 laptop:px-4 desktop:px-8;
}
@utility hspace-md {
  @apply px-4 tablet:px-6 laptop:px-8 desktop:px-16;
}
@utility hspace-lg {
  @apply px-6 tablet:px-8 laptop:px-12 desktop:px-24;
}
@utility hspace-xl {
  @apply px-8 tablet:px-12 laptop:px-16 desktop:px-44;
}
```

### Why a linear 4-step ladder

Figma originally exposed only three sizes (`hspace-sm` / `md` / `lg`) with the largest jumping to `172` px on desktop — a 7.2× mobile-to-desktop multiplier that broke the smooth scaling pattern. OMR's spec smooths the family to a consistent 4× ladder and parks the editorial-extreme magnitude in a new `hspace-xl` (Desktop `176` ≈ Figma's original `172`, but on Tailwind scale).

### Decision rule

```
Which hspace token?
├─ Tight page (dense data, lots of content)        → hspace-sm
├─ Default page                                    → hspace-md  (compose via responsive-container)
├─ Feature / hero / generous content               → hspace-lg
└─ Brand / editorial / narrow-focused              → hspace-xl
```

---

## Responsive section padding — `vspace-*`

**Concept:** "Responsive section padding" (also called "vertical section rhythm") — vertical padding that scales with viewport size. Use for **section-level** vertical spacing (top/bottom of a `<section>`, between layout regions). **Never** for component internals.

The family has 8 sizes, all on Tailwind scale. **Use `vspace-sm` or `vspace-md` for most product sections.**

| Token | Mobile / Tablet / Laptop | Desktop+ | Tailwind classes | When to use |
|---|---|---|---|---|
| `vspace-none` | 0 | 0 | `py-0` | Explicit zero — sections that abut without gap |
| `vspace-xs` | 16 / 16 / 24 | 24 | `py-4 laptop:py-6` | Tight section separator |
| `vspace-sm` | 24 / 24 / 24 | 48 | `py-6 desktop:py-12` | Standard section padding |
| `vspace-md` | 48 / 48 / 48 | **80** | `py-12 desktop:py-20` | Medium section padding |
| `vspace-lg` | **80** / 80 / 80 | 96 | `py-20 desktop:py-24` | Large section padding |
| `vspace-xl` | **128** / 128 / 128 | 144 | `py-32 desktop:py-36` | Hero / generous marketing |
| `vspace-2xl` | **208** / 208 / 208 | 240 | `py-52 desktop:py-60` | Big marketing section |
| `vspace-3xl` | **384** | **384** | `py-96` | Maximum section padding (non-responsive, capped at Tailwind max) |

Bold values are **adjusted from Figma** — see [Known drifts](#known-drifts) below.

```css
/* utilities.css — canonical post-refactor form */
@utility vspace-none { @apply py-0; }
@utility vspace-xs   { @apply py-4 laptop:py-6; }
@utility vspace-sm   { @apply py-6 desktop:py-12; }
@utility vspace-md   { @apply py-12 desktop:py-20; }
@utility vspace-lg   { @apply py-20 desktop:py-24; }
@utility vspace-xl   { @apply py-32 desktop:py-36; }
@utility vspace-2xl  { @apply py-52 desktop:py-60; }
@utility vspace-3xl  { @apply py-96; }
```

### Why this solves the "27 Sections, 27 Patterns" problem

The omr-js `hygraph-ui` package contains 27 `Section*` components. An audit showed each picks its own vertical padding hardcoded: `pb-8 tablet:pb-14`, `pb-14 laptop:pb-28`, `pb-60 laptop:pt-60`, `p-2 tablet:p-3`, …. No shared vocabulary, no consistency.

With `vspace-*` tokens, Section components consume **one of 8 well-defined steps** instead of inventing their own padding pattern. Future page-level vertical rhythm becomes a curated dropdown of choices, not a one-off decision each time.

### Decision rule

```
Which vspace token?
├─ No padding (abutting sections)        → vspace-none
├─ Tight separator                       → vspace-xs / vspace-sm
├─ Standard product section              → vspace-sm / vspace-md  (default range)
├─ Feature / hero                        → vspace-lg / vspace-xl
├─ Marketing big                         → vspace-2xl
└─ Extreme (very rare)                   → vspace-3xl
```

---

## Page-level content width — `max-w-content`

**Concept:** "Page-level content width cap" — a single max-width that constrains content from stretching beyond the canonical readable/scannable width on very wide viewports.

| Token | Value | Tailwind utility | Where it's defined |
|---|---|---|---|
| `max-w-content` | 1440 px | `max-w-content` | `--max-w-content` in `theme.css` `@theme` block |

```css
/* theme.css — canonical post-refactor form */
@theme {
  --max-w-content: 1440px;
}
```

Once defined as a `@theme` token, `max-w-content` becomes a valid Tailwind utility automatically. Anyone needing to cap a layout at the canonical content width can `<div class="max-w-content mx-auto">` without writing arbitrary values like `max-w-[1440px]`.

### Why not responsive

Figma's `container-max-width` is responsive (336 / 616 / 976 / 1320 / 1320 px). We don't mirror that responsive structure because:

1. **It's mostly derivable** from `viewport − 2 × hspace-md` (the math works out modulo 8–24 px informational drift).
2. **Implementing all 5 responsive values would require 4 arbitrary Tailwind values** (336, 616, 976, 1320 are not on Tailwind's max-w scale).
3. **The only non-derivable value is the cap on Desktop+** — and that's exactly what `max-w-content` captures.

### Relationship to `responsive-container`

`responsive-container` composes `hspace-md` (page gutters) + `max-w-content` (content cap) + `mx-auto` (centering). The canonical post-refactor form:

```css
@utility responsive-container {
  @apply hspace-md desktop:max-w-content desktop:mx-auto;
}
```

---

## Composite spacing utilities

Pre-built utilities that bundle canonical spacing patterns. Use these instead
of re-assembling the same paddings/gaps in every component.

### `responsive-container`

Page-level wrapper composed of `hspace-md` + `max-w-content` + `mx-auto`.
**Use this on any top-level page or section instead of writing manual
responsive padding.**

```css
/* utilities.css — canonical post-refactor form */
@utility responsive-container {
  @apply hspace-md desktop:max-w-content desktop:mx-auto;
}
```

Expands to:

| Breakpoint | Horizontal padding | Content cap |
|---|---|---|
| mobile (< 640px) | `px-4` (16px, from `hspace-md`) | — |
| tablet (≥ 640px) | `px-6` (24px) | — |
| laptop (≥ 1024px) | `px-8` (32px) | — |
| desktop (≥ 1440px) | `px-16` (64px) | `max-w-content` (1440px) + `mx-auto` |

> **⚠️ Code drift — pending refactor.** The current `utilities.css` in `omr-js`
> still ships the pre-token form: `desktop:px-[60px]` + `desktop:max-w-[1440px]`
> (two arbitrary values). The canonical spec uses the new `hspace-md` + `max-w-content`
> tokens, which produces `desktop:px-16` (64px) for padding and resolves
> `max-w-content` to 1440px via the `--max-w-content` theme variable. Refactor
> tracked as a separate code-side ticket. **Until merged, generate UI against
> the canonical token form** — don't propagate the 60px drift or the arbitrary
> `max-w-[1440px]`.

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

## Figma-only tokens

Two Figma token families are **deliberately not implemented** in code. They live in Figma for designer convenience but the corresponding implementations are different — see each entry.

### `gap-*` semantic aliases

Figma defines: `gap-xs` (4 px) / `gap-sm` (8) / `gap-md` (12) / `gap-lg` (16) / `gap-xl` (24) / `gap-2xl` (40).

These are **non-responsive semantic aliases** over Tailwind's existing `gap-N` scale. No new pixel values. Implementing them in code would create two ways to express the same value (`gap-md` ↔ `gap-3`), introducing friction for code reviews, AI agents, and devs.

**In code:** use Tailwind's numeric `gap-N` directly (`gap-1` / `gap-2` / `gap-3` / `gap-4` / `gap-6` / `gap-10`). The responsive layout-gap use case is covered by the existing `grid-gap` composite (`gap-4 desktop:gap-6`); if more responsive-gap variants are needed later, extend `grid-gap` into `grid-gap-{sm,md,lg}` rather than add a non-responsive layer.

### `paragraph-max-width`

Figma defines: `paragraph-max-width` 352 → 632 → 768 → 768 → 768 px (responsive).

Figma expresses paragraph width in pixels. OMR's canonical implementation is **`max-w-prose`** (Tailwind built-in, ch-based, font-size-relative). The two approaches aim at the same typographic goal (45–75 chars per line); `max-w-prose` expresses it in font-relative terms, which:

- Is the typography tradition (45–75 chars/line — Bringhurst et al.)
- Scales correctly with font-size — important for accessibility (text zoom respected)
- Needs no arbitrary values

**In code:** use `max-w-prose` for paragraph constraints — see [`typography.md`](./typography.md). The Figma pixel value is a designer-side approximation; both worlds converge on the same readable column width when default fonts apply.

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
/* theme.css — OMR additions */
@theme {
  /* Tailwind v4 default, redocumented for visibility — not redefined */
  /* --spacing: 0.25rem; */

  /* OMR-custom layout token */
  --max-w-content: 1440px;
}
```

```css
/* utilities.css — OMR custom + composite spacing utilities */

/* Responsive page padding (hspace-*) */
@utility hspace-sm  { @apply px-2 tablet:px-3 laptop:px-4 desktop:px-8;  }
@utility hspace-md  { @apply px-4 tablet:px-6 laptop:px-8 desktop:px-16; }
@utility hspace-lg  { @apply px-6 tablet:px-8 laptop:px-12 desktop:px-24; }
@utility hspace-xl  { @apply px-8 tablet:px-12 laptop:px-16 desktop:px-44; }

/* Responsive section padding (vspace-*) */
@utility vspace-none { @apply py-0; }
@utility vspace-xs   { @apply py-4 laptop:py-6; }
@utility vspace-sm   { @apply py-6 desktop:py-12; }
@utility vspace-md   { @apply py-12 desktop:py-20; }
@utility vspace-lg   { @apply py-20 desktop:py-24; }
@utility vspace-xl   { @apply py-32 desktop:py-36; }
@utility vspace-2xl  { @apply py-52 desktop:py-60; }
@utility vspace-3xl  { @apply py-96; }

/* Composite utilities */
@utility responsive-container { @apply hspace-md desktop:max-w-content desktop:mx-auto; }
@utility grid-gap { … }
@utility grid-container { … }
@utility card { … }
@utility separate-rows { … }
```

> The base unit (`--spacing`) is **inherited from Tailwind v4** and not declared
> in OMR's `@theme` block. The only OMR-side `@theme` addition for spacing is
> `--max-w-content: 1440px`, which exposes `max-w-content` as a Tailwind utility.

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

## Known drifts

Consolidated inventory of drifts between Figma tokens, omr-js code, and this spec. Each entry has a direction (which side needs the fix) and a tracked action. None of these block usage of the spec — generate UI against the canonical values documented above.

| # | Drift | Direction | Action |
|---|---|---|---|
| 1 | `hspace-md` desktop value: Figma 64 vs current omr-js code 60 | code-side | Update `responsive-container` `desktop:px-[60px]` → `desktop:px-16` (part of the responsive-container refactor) |
| 2 | `hspace-lg` desktop value: Figma 172 vs spec 96 | Figma-side | Update Figma `hspace-lg` to ladder-consistent 96 |
| 3 | `hspace-xl` is a new addition not in Figma | Figma-side | Add `hspace-xl` to Figma (32 / 48 / 64 / 176 / 176) |
| 4 | `vspace-md` desktop value: Figma 72 vs spec 80 | Figma-side | Round Figma 72 → 80 (Tailwind step 20) |
| 5 | `vspace-lg` mobile/tablet/laptop value: Figma 72 vs spec 80 | Figma-side | Round Figma 72 → 80 |
| 6 | `vspace-xl` mobile/tablet/laptop value: Figma 120 vs spec 128 | Figma-side | Round Figma 120 → 128 (Tailwind step 32) |
| 7 | `vspace-2xl` mobile/tablet/laptop value: Figma 200 vs spec 208 | Figma-side | Round Figma 200 → 208 (Tailwind step 52) |
| 8 | `vspace-3xl`: Figma 400/480 vs spec 384/384 (non-responsive cap) | Figma-side | Both values beyond Tailwind max — cap at 384, document loss of responsive jump |
| 9 | Figma scopes for `hspace-*` / `vspace-*` are `[GAP]` only | Figma-side | Update scopes — `hspace-*` should be `[LEFT_PADDING, RIGHT_PADDING]`; `vspace-*` should be `[TOP_PADDING, BOTTOM_PADDING]` |

**Sub-action — separate tickets:**
- One omr-js code-side ticket to land all changes (refactor `responsive-container`, add `hspace-*` / `vspace-*` `@utility` blocks, add `--max-w-content` to `theme.css`).
- One Figma file ticket to reconcile drifts 2–9.

**Informational drift (no action):** Figma's `container-max-width` (responsive: 336/616/976/1320/1320) measures inner-content-width with 8–24 px deviation from `viewport − 2 × hspace-md`. We don't mirror Figma's responsive structure — `max-w-content: 1440px` is the outer-wrapper cap; inner content derives from the math.

---

## Cross-references

- [`breakpoints.md`](./breakpoints.md) — `responsive-container`, `grid-gap`,
  `grid-container` from the responsive-layout angle
- [`typography.md`](./typography.md) — `txt-*` baked-in line heights pair with
  vertical spacing for rhythm
- [`sizing.md`](./sizing.md) — component heights, container widths, icon
  sizes
- [`radius.md`](./radius.md) — border radius scale (separate from spacing)
- [`../concepts/component-padding.md`](../concepts/component-padding.md) —
  component-level padding token layer (e.g. `padding-card`, `padding-button-m-x`).
  Separate from this foundation's responsive layout tokens (`hspace-*` / `vspace-*`).
- [`../concepts/density-and-rhythm.md`](../concepts/density-and-rhythm.md) (todo) —
  how spacing combines with sizing and typography for density tiers
- [`../concepts/visual-hierarchy.md`](../concepts/visual-hierarchy.md) (todo) —
  how spacing reinforces emphasis alongside color and typography
- [`../concepts/accessibility.md`](../concepts/accessibility.md) (todo) — touch
  target spacing (≥ 44 px)
- [`../CLAUDE.md`](../CLAUDE.md) — agent rules
