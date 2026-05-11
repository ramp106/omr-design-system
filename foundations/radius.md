---
title: Radius
type: foundation
status: stable
last_updated: 2026-05-11
related: [spacing.md, color.md, breakpoints.md]

tokens:
  base-unit:
    css_var: "--radius"
    rem: "0.25rem"
    px: 4
    source: "Tailwind v4 default — explicitly re-set in OMR's theme.css for clarity"
    note: "Sets the default value used by the unsuffixed `rounded` class. Identical to the Tailwind default."

  # === Radius scale (Tailwind v4 defaults — no OMR-custom layer) ===
  scale:
    none:    { tailwind: "rounded-none", css_var: null,            rem: "0",        px: 0,    usage: "Explicitly no rounding — sharp corners" }
    xs:      { tailwind: "rounded-xs",   css_var: "--radius-xs",   rem: "0.125rem", px: 2,    usage: "Very subtle rounding — inline tags, code pills" }
    sm:      { tailwind: "rounded-sm",   css_var: "--radius-sm",   rem: "0.25rem",  px: 4,    usage: "Default UI radius — buttons, inputs, chips, badges" }
    default: { tailwind: "rounded",      css_var: "--radius",      rem: "0.25rem",  px: 4,    usage: "Same value as rounded-sm via the --radius variable. Prefer `rounded-sm` for explicitness." }
    md:      { tailwind: "rounded-md",   css_var: "--radius-md",   rem: "0.375rem", px: 6,    usage: "Slightly more rounded — secondary surfaces" }
    lg:      { tailwind: "rounded-lg",   css_var: "--radius-lg",   rem: "0.5rem",   px: 8,    usage: "Standard floating-surface radius — cards, dropdowns, popovers, modals, toasts, banners, tooltips" }
    xl:      { tailwind: "rounded-xl",   css_var: "--radius-xl",   rem: "0.75rem",  px: 12,   usage: "Available; rarely used in product UI" }
    "2xl":   { tailwind: "rounded-2xl",  css_var: "--radius-2xl",  rem: "1rem",     px: 16,   usage: "Tiles, very large panels — rare" }
    "3xl":   { tailwind: "rounded-3xl",  css_var: "--radius-3xl",  rem: "1.5rem",   px: 24,   usage: "Hero cards, marketing surfaces" }
    "4xl":   { tailwind: "rounded-4xl",  css_var: "--radius-4xl",  rem: "2rem",     px: 32,   usage: "Very large editorial surfaces — rare" }
    full:    { tailwind: "rounded-full", css_var: null,            rem: "calc(infinity * 1px)", px: 9999, usage: "Pills, avatars, circular buttons" }

  utility-families:
    all-corners:    ["rounded-*"]
    per-side:       ["rounded-t-*", "rounded-r-*", "rounded-b-*", "rounded-l-*"]
    per-corner:     ["rounded-tl-*", "rounded-tr-*", "rounded-br-*", "rounded-bl-*"]
    logical-sides:  ["rounded-s-*", "rounded-e-*"]
    logical-corner: ["rounded-ss-*", "rounded-se-*", "rounded-es-*", "rounded-ee-*"]

  known-drifts:
    claude-md-spec:
      claim: "CLAUDE.md lists `rounded-s, rounded-m, rounded-l` as canonical OMR tokens"
      reality: "These names do not exist as defined tokens in omr-js. `rounded-s-*` and `rounded-e-*` are Tailwind logical-side utilities (start/end), not size variants."
      action: "Follow-up — update CLAUDE.md to reflect actual scale"
    figma-naming:
      claim: "Figma `Radius` collection uses `rounded-sm = 2px` and `rounded = 4px`"
      reality: "Tailwind v4 has `rounded-xs = 2px` and `rounded-sm = 4px`. Figma's `rounded-sm` collides with Tailwind's. Several Figma tokens carry `_` prefix (likely deprecated)."
      action: "Follow-up — sync Figma to Tailwind v4 naming"
    arbitrary-values-in-code:
      examples: ["rounded-[4px]", "rounded-[8px]", "rounded-[16px]", "rounded-[40px]", "rounded-[3rem]", "rounded-[1.4px]"]
      reality: "Found 7 arbitrary-value instances in omr-js. Most have on-scale equivalents."
      action: "Follow-up — fix in code"
---

# Radius

## TL;DR

OMR uses **Tailwind v4 default radius tokens** as the canonical scale. No custom
OMR layer exists. Use `rounded-sm` (4px) for most UI (buttons, inputs, chips),
`rounded-lg` (8px) for cards, `rounded-full` for pills/avatars. Never use
arbitrary values (`rounded-[16px]`) — every common value is on the scale.

---

## Architecture

| Layer | What it is | Where it lives |
|---|---|---|
| **Base radius** | `--radius: 4px` (the default for the unsuffixed `rounded` class) | `theme.css` `@theme` block |
| **Tailwind v4 scale** | `--radius-xs` … `--radius-4xl` + `rounded-none` + `rounded-full` | Tailwind v4 defaults (not redeclared in OMR theme) |
| **Utilities** | `rounded-*` plus per-side, per-corner, and logical-side variants | Tailwind v4 defaults |

> **No OMR-custom radius layer.** Unlike colors (which have a full semantic
> token layer) or spacing (which has composite utilities), radius is consumed
> straight from Tailwind's defaults. The only OMR-side declaration is the
> explicit `--radius: 4px` in `theme.css`, which matches the Tailwind default
> anyway — kept as a guard against future Tailwind upstream changes.

---

## Radius scale

Tailwind v4 default scale. **This is the full list — use these and nothing else.**

| Tailwind class | CSS variable | rem | px | When to use |
|---|---|---|---|---|
| `rounded-none` | — | 0 | 0 | Explicitly no rounding — sharp corners |
| `rounded-xs` | `--radius-xs` | 0.125rem | 2 | Very subtle rounding — inline tags, code pills |
| `rounded-sm` | `--radius-sm` | 0.25rem | 4 | **Default UI radius** — buttons, inputs, chips, badges |
| `rounded` | `--radius` | 0.25rem | 4 | Same value as `rounded-sm` (via the `--radius` variable). Prefer `rounded-sm` for explicitness. |
| `rounded-md` | `--radius-md` | 0.375rem | 6 | Slightly more rounded — secondary surfaces |
| `rounded-lg` | `--radius-lg` | 0.5rem | 8 | Cards, dropdowns, popovers |
| `rounded-xl` | `--radius-xl` | 0.75rem | 12 | Larger panels, dialogs |
| `rounded-2xl` | `--radius-2xl` | 1rem | 16 | Tiles, large panels |
| `rounded-3xl` | `--radius-3xl` | 1.5rem | 24 | Hero cards, marketing surfaces |
| `rounded-4xl` | `--radius-4xl` | 2rem | 32 | Very large editorial surfaces — rare |
| `rounded-full` | — | `calc(infinity * 1px)` | 9999 | Pills, avatars, circular buttons |

### Directional utilities

The same scale applies to per-side, per-corner, and logical-side variants:

| Family | Utilities | Example |
|---|---|---|
| All corners | `rounded-*` | `rounded-lg` |
| Per side | `rounded-t-*`, `rounded-r-*`, `rounded-b-*`, `rounded-l-*` | `rounded-t-lg` (top only) |
| Per corner | `rounded-tl-*`, `rounded-tr-*`, `rounded-br-*`, `rounded-bl-*` | `rounded-bl-2xl` (bottom-left only) |
| Logical sides | `rounded-s-*` (start), `rounded-e-*` (end) | `rounded-s-md` (start side — left in LTR, right in RTL) |
| Logical corners | `rounded-ss-*`, `rounded-se-*`, `rounded-es-*`, `rounded-ee-*` | `rounded-ss-lg` (start-start corner) |

> **Watch out — `rounded-s-*` is logical-side, not "small size".** Tailwind's
> `rounded-s-md` means *round the start side at md*, not *round all corners
> at size s*. There is no "size-s/m/l" radius scale in OMR (despite an old
> reference in `CLAUDE.md` — see Known drifts).

---

## Decision rules ("Spielregeln")

### Picking a radius

```
What am I rounding?
├─ Pill, avatar, circular button         → rounded-full
├─ Button, input, chip, badge            → rounded-sm (4px) — the default
├─ Floating surface — card, dropdown,
│  popover, modal, toast, banner,
│  tooltip                               → rounded-lg (8px) — the standard surface radius
├─ Small thumbnail image, code pill,
│  tag-inside-text                       → rounded-xs (2px)
├─ Hero / marketing surface              → rounded-3xl (24px)
├─ Nested element inside a rounded
│  container                             → see Nested radius rule below
├─ Image inside a rounded container      → no radius on image; container handles via overflow-hidden
└─ Explicit sharp corners                → rounded-none
```

> **Most-used tokens in practice.** `rounded-full` (61×), `rounded-sm` (54×),
> `rounded-lg` (25×), `rounded-md` (13×), `rounded-xs` (11×) account for
> ~95% of all radius usage in omr-js. The other scale steps (`rounded-md`,
> `rounded-xl`, `rounded-2xl`, `rounded-3xl`, `rounded-4xl`) are available
> when needed but don't appear in the decision tree above — reach for them
> only when the standard archetypes genuinely don't fit.

### Default-to-`rounded-sm`

- **`rounded-sm` (4px) is the standard UI radius.** When unsure, pick this.
- Don't reach for `rounded` (no suffix) — it resolves to the same value via the
  `--radius` variable but is less explicit. Prefer the named token.

### Per-side and per-corner

- **Use per-side / per-corner variants** when an element is visually fused with
  another (e.g. a button group, a tab attached to a panel).
- **Mixing radii on adjacent elements** that should look connected is the
  primary legit use case — otherwise stick to all-corners.

### Logical-side (RTL/LTR-aware)

- **Use `rounded-s-*` / `rounded-e-*`** instead of `rounded-l-*` / `rounded-r-*`
  whenever the rounding has semantic meaning (start vs end), so RTL locales
  flip automatically.
- For purely visual choices (e.g. a card with rounded top corners regardless
  of writing direction) the physical `-t/-r/-b/-l` variants are fine.

### Mixing radii in a single component

- **Avoid more than one radius size in a single component** unless there's a
  clear hierarchy (e.g. a card with `rounded-lg` containing a button with
  `rounded-sm` — fine, different elements). Two radii on the same shape is
  almost always a sign something's off.

---

## Image surfaces

Images don't carry their own radius — they take the shape of their container.
Three patterns:

| Pattern | What to do | Example |
|---|---|---|
| **Image fills a rounded container** | Apply `overflow-hidden` to the container; do not set radius on the image | `<div class="rounded-lg overflow-hidden"><img …/></div>` — image is clipped by container |
| **Small standalone thumbnail** (logo grid, list-row thumbnail) | `rounded-xs` (2px) | `<img class="rounded-xs h-10 w-10" …/>` — barely-rounded, editorial |
| **Avatar (circular)** | `rounded-full` on the image | `<img class="rounded-full h-10 w-10" …/>` |

> **Don't apply a radius directly to an image inside a card.** If the image
> needs to match the card's rounded corners, the card uses `overflow-hidden`
> and the image stays flat. Setting a radius on the image as well risks
> double-rounding artifacts.

> **Avatars are always `rounded-full`** — square avatars use `rounded-xs`
> only as an exception (e.g. company logos that read better as squares).

---

## Nested radius rule

When a rounded element is **inside** another rounded element, the inner radius
must be ≤ the outer radius.

```
✅ Card (rounded-lg, 8px) → Button inside (rounded-sm, 4px)        inner < outer
✅ Card (rounded-lg, 8px) → Badge inside (rounded-md, 6px)         inner < outer
❌ Card (rounded-sm, 4px) → Button inside (rounded-lg, 8px)        inner > outer — looks wrong
```

### Why

An inner element with a larger radius than its container has corners that
appear to "poke out" beyond the container's corner curve. The eye reads this
as broken alignment even when the geometry is technically correct.

### Strict tangent rule (for tight padding)

When the inner element sits close to the container edge, the optically correct
relationship is:

```
inner_radius = outer_radius - distance_to_outer_corner
```

So a `rounded-lg` (8px) card with `p-2` (8px padding) and an edge-hugging
button should use `rounded-none` on the button if you want strictly parallel
corners. In practice, **inner ≤ outer is sufficient** — strict tangency only
matters when nested elements visually touch their container's corner.

### Real example from omr-js

`HostCard.vue`:
```html
<div class="rounded-lg border …">       <!-- outer card: 8px -->
  <div class="absolute … rounded-md …"> <!-- inner badge: 6px -->
    <!-- … -->
  </div>
</div>
```
Inner badge (6px) < outer card (8px). ✅

---

## Context-aware radius (full-bleed surfaces)

When a surface stretches to a hard viewport edge (top/bottom/side), drop the
radius on **the side touching the edge**. Rounded corners against a flat
viewport edge read as broken.

| Surface position | Radius treatment |
|---|---|
| Floating (centred, away from edges) | Full `rounded-lg` (or whatever the surface calls for) |
| Stuck to top of viewport | `rounded-none` on top corners, keep bottom rounded if appropriate |
| Stuck to bottom of viewport | `rounded-none` on bottom corners, keep top rounded if appropriate |
| Full-bleed (edge to edge) | `rounded-none` entirely |

### Real example from omr-js

`MessageBanner.vue` toggles radius based on its `stuck-to` prop:
```html
<!-- floating -->
class="rounded-lg"

<!-- stuck top: drop radius on top corners -->
class="rounded-none border-x-0 border-t-0"

<!-- stuck bottom: drop radius on bottom corners -->
class="rounded-none border-x-0 border-b-0"
```

The same logic applies to bottom sheets, top notification bars, side panels.

---

## Anti-patterns

- ❌ `border-radius: 8px` or `style="border-radius: 8px"` — raw CSS. **Use** `rounded-lg`.
- ❌ `rounded-[8px]`, `rounded-[16px]`, `rounded-[4px]` — arbitrary values that exist on the scale. **Use** `rounded-lg`, `rounded-2xl`, `rounded-sm`.
- ❌ `rounded-[3rem]`, `rounded-[40px]`, `rounded-[1.4px]` — genuinely off-scale arbitrary values. If the design really needs a non-scale radius, push back on the design first — almost always an on-scale step works.
- ❌ `rounded-s`, `rounded-m`, `rounded-l` as size names — **these are not OMR tokens.** `rounded-s-*` and `rounded-e-*` exist in Tailwind but mean *logical start/end*, not size. See Known drifts.
- ❌ Mixing `rounded` and `rounded-sm` in the same component — they resolve to the same value, but the inconsistency suggests confusion. Pick one.
- ❌ Using `rounded-full` on rectangular elements that aren't pill-shaped — produces unexpected stadium shapes. `rounded-full` is for circles and pills only.
- ❌ Stacking arbitrary radii via per-corner variants (`rounded-tl-[7px] rounded-tr-[5px]`) — almost always wrong; design probably wants a single radius.

---

## Tailwind config reference

```css
/* theme.css — the only OMR-side radius declaration */
@theme {
  --radius: 4px;
}
```

```css
/* Tailwind v4 defaults — not redeclared in OMR's theme.css */
@theme {
  --radius-xs:  0.125rem; /* 2px */
  --radius-sm:  0.25rem;  /* 4px */
  --radius-md:  0.375rem; /* 6px */
  --radius-lg:  0.5rem;   /* 8px */
  --radius-xl:  0.75rem;  /* 12px */
  --radius-2xl: 1rem;     /* 16px */
  --radius-3xl: 1.5rem;   /* 24px */
  --radius-4xl: 2rem;     /* 32px */
}
```

> If we ever need an OMR-specific radius variant (e.g. for a component family
> with its own canonical radius), declare it as a **new token** (e.g.
> `--radius-card: 8px`) in `theme.css` — don't override the Tailwind defaults.
> That keeps the Tailwind scale predictable for everyone.

---

## Examples

### Do — standard button with default radius

```html
<button class="rounded-sm bg-primary-main text-inverse px-4 py-2 txt-label-m-bold">
  Click me
</button>
```

### Do — card with surface + content

```html
<div class="rounded-lg bg-surface-elevation-2 p-6">
  <h3 class="txt-headline-l-bold text-main">Card title</h3>
  <p class="txt-body-m-regular text-subtle mt-2">Body…</p>
</div>
```

### Do — circular avatar

```html
<img src="avatar.jpg" class="rounded-full h-10 w-10" alt="…" />
```

### Do — pill-shaped badge

```html
<span class="rounded-full bg-badge-filled-success text-badge-filled-success px-3 py-1 txt-label-s-bold-uppercase">
  Active
</span>
```

### Do — connected button + panel (per-corner)

```html
<div class="flex flex-col">
  <button class="rounded-t-lg bg-primary-main text-inverse p-3">Header button</button>
  <div class="rounded-b-lg bg-surface-elevation-2 p-4">Panel body</div>
</div>
```

### Don't — arbitrary value when scale step exists

```html
<div class="rounded-[8px] …">…</div>
```
**Why wrong:** `rounded-lg` is exactly 8px and on-scale. **Use** `rounded-lg`.

### Don't — `rounded-s` as a "small radius"

```html
<button class="rounded-s …">Submit</button>
```
**Why wrong:** `rounded-s-*` in Tailwind v4 is *logical start side*, not "small size".
Bare `rounded-s` without a size suffix doesn't render meaningful styling. **Use** `rounded-sm`.

### Don't — off-scale optical-tweak radius

```html
<div class="rounded-[1.4px]">…</div>
```
**Why wrong:** sub-pixel optical-alignment hacks don't scale across devices or
zoom levels, and they break the rhythm. **Use** `rounded-none` (sharp) or
`rounded-xs` (2px) — pick the visual intent, not a magic number.

---

## Known drifts

Documented for transparency; each has a follow-up.

### Drift 1 — `CLAUDE.md` claims `rounded-s/m/l` are canonical

The current top-level `CLAUDE.md` lists `rounded, rounded-s, rounded-m, rounded-l, rounded-full`
as the allowed radius tokens. **Those size variants do not exist in code.** The
real scale is the Tailwind v4 defaults documented above. `rounded-s-*` and
`rounded-e-*` exist as logical-side utilities (start/end), but never as size names.

**Follow-up:** update `CLAUDE.md` to reflect the actual scale.

### Drift 2 — Figma naming collides with Tailwind v4

The Figma `Radius` collection defines:
- `rounded-sm` = 2px (collides with Tailwind v4, where `rounded-sm` = 4px and `rounded-xs` = 2px)
- `rounded` = 4px (matches)
- `rounded-lg` = 8px (matches)
- Several tokens carry `_` prefix (`_rounded-md`, `_rounded-xl`, `_rounded-3xl`, `_rounded-full`) — likely marked deprecated/internal

**Follow-up:** sync the Figma collection to Tailwind v4 naming so designer-to-dev handoff uses one vocabulary.

### Drift 3 — Arbitrary values in code

Found in `omr-js`:
- `rounded-[4px]` (×2) → use `rounded-sm`
- `rounded-[8px]` (×1) → use `rounded-lg`
- `rounded-[16px]` (×1) → use `rounded-2xl`
- `rounded-[40px]` (×1) → off-scale; investigate intent (probably a near-pill shape)
- `rounded-[3rem]` (×1) → 48px, off-scale; same
- `rounded-[1.4px]` (×1) → sub-pixel hack; investigate

**Follow-up:** clean up in code as a single pass — three are trivial swaps, three need a design conversation.

---

## Cross-references

- [`spacing.md`](./spacing.md) — spacing scale (separate from radius but uses the same 4px base unit)
- [`color.md`](./color.md) — borders and backgrounds that pair with radius for surface definition
- [`../concepts/component-padding.md`](../concepts/component-padding.md) — component-level decisions that combine padding + radius (e.g. cards use `rounded-lg` + `padding-card`)
- [`../concepts/elevation-system.md`](../concepts/elevation-system.md) (todo) — how radius pairs with shadow/border for surface hierarchy
- [`../CLAUDE.md`](../CLAUDE.md) — agent rules (note: radius section there is currently inaccurate — see Known drifts above)
