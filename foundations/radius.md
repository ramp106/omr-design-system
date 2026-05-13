---
title: Radius
type: foundation
status: stable
last_updated: 2026-05-11
related: [spacing.md, color.md, breakpoints.md]

tokens:
  base-unit:
    css_var: "--radius"
    rem: "0.375rem"
    px: 6
    source: "OMR override of Tailwind v4 default. Shifted from 4px → 6px as part of the system-wide rounder direction (see known-drifts.rounder-direction-not-in-code)."
    note: "Sets the value of the unsuffixed `rounded` Tailwind class. Resolves to the same 6px as `rounded-sm` post-shift. Documented as a CSS variable for transparency, but **bare `rounded` is NOT canonical** — always use the explicit `rounded-sm` form in code. See `known-drifts.bare-rounded-in-code`."

  # === Radius scale — OMR-shifted (canonical, overrides Tailwind v4 defaults) ===
  # Every value shifted one step upward to make the entire product visually rounder.
  # See known-drifts.rounder-direction-not-in-code for the gap to current omr-js code.
  scale:
    none:    { tailwind: "rounded-none", css_var: null,            rem: "0",        px: 0,    usage: "Explicitly no rounding — sharp corners" }
    xs:      { tailwind: "rounded-xs",   css_var: "--radius-xs",   rem: "0.25rem",  px: 4,    usage: "Very subtle rounding — inline tags, code pills" }
    sm:      { tailwind: "rounded-sm",   css_var: "--radius-sm",   rem: "0.375rem", px: 6,    usage: "Default UI radius — buttons, inputs, chips, badges. **Canonical 6px token.**" }
    md:      { tailwind: "rounded-md",   css_var: "--radius-md",   rem: "0.5rem",   px: 8,    usage: "Slightly more rounded — secondary surfaces" }
    lg:      { tailwind: "rounded-lg",   css_var: "--radius-lg",   rem: "0.75rem",  px: 12,   usage: "Standard floating-surface radius — cards, dropdowns, popovers, modals, toasts, banners, tooltips" }
    xl:      { tailwind: "rounded-xl",   css_var: "--radius-xl",   rem: "1rem",     px: 16,   usage: "Larger panels, dialogs" }
    "2xl":   { tailwind: "rounded-2xl",  css_var: "--radius-2xl",  rem: "1.5rem",   px: 24,   usage: "Tiles, very large panels" }
    "3xl":   { tailwind: "rounded-3xl",  css_var: "--radius-3xl",  rem: "2rem",     px: 32,   usage: "Hero cards, marketing surfaces, top of the scale" }
    full:    { tailwind: "rounded-full", css_var: null,            rem: "calc(infinity * 1px)", px: 9999, usage: "Pills, avatars, circular buttons" }

  utility-families:
    all-corners:    ["rounded-*"]
    per-side:       ["rounded-t-*", "rounded-r-*", "rounded-b-*", "rounded-l-*"]
    per-corner:     ["rounded-tl-*", "rounded-tr-*", "rounded-br-*", "rounded-bl-*"]
    logical-sides:  ["rounded-s-*", "rounded-e-*"]
    logical-corner: ["rounded-ss-*", "rounded-se-*", "rounded-es-*", "rounded-ee-*"]

  known-drifts:
    rounder-direction-not-in-code:
      claim: "Doc reflects the system-wide rounder-direction scale (rounded-sm=6, rounded-lg=12, etc.). Current omr-js code still uses Tailwind v4 defaults (rounded-sm=4, rounded-lg=8, etc.)."
      reality: "The full migration requires overriding --radius-{xs,sm,md,lg,xl,2xl,3xl} in theme.css. Every rounded-* utility renders the OLD value until that override lands."
      action: "Tracked in omr-js code drift cleanup ticket. Visual regression sweep across Storybook + Pages required before merge. Communicate to broader team before code change (system-wide visual shift)."
      scale-shift-summary: "xs: 2→4, sm: 4→6, md: 6→8, lg: 8→12, xl: 12→16, 2xl: 16→24, 3xl: 24→32. rounded-4xl removed (was 32, absorbed by new 3xl)."
    claude-md-spec:
      claim: "CLAUDE.md lists `rounded-s, rounded-m, rounded-l` as canonical OMR tokens"
      reality: "These names do not exist as defined tokens in omr-js. `rounded-s-*` and `rounded-e-*` are Tailwind logical-side utilities (start/end), not size variants."
      action: "Follow-up — update CLAUDE.md to reflect actual scale"
    figma-values-out-of-sync:
      claim: "Figma `Radius` collection uses pre-shift values (sm = 2, rounded = 4, lg = 8, 2xl = 16, …) which match neither Tailwind v4 defaults nor OMR's new post-shift canonical."
      reality: "Every Figma value needs to be shifted up to match OMR canonical: sm 2→6, rounded 4→6, _md 6→8, lg 8→12, _xl 12→16, 2xl 16→24, _3xl 24→32. Several Figma tokens carry `_` prefix (likely marked deprecated/internal). The OMR canonical scale also drops rounded-4xl entirely."
      action: "Follow-up — reconcile Figma to OMR canonical scale. Bundle with the omr-js code drift cleanup ticket (same migration applied in both places)."
    arbitrary-values-in-code:
      examples: ["rounded-[4px]", "rounded-[8px]", "rounded-[16px]", "rounded-[40px]", "rounded-[3rem]", "rounded-[1.4px]"]
      reality: "Found 7 arbitrary-value instances in omr-js. Migration is ambiguous post-shift: rounded-[4px] could become rounded-xs (preserve px value = 4) or rounded-sm (preserve semantic intent = 'default UI radius', now 6). Same ambiguity for rounded-[8px] (xs/sm at old values → md/lg at new) and rounded-[16px] (lg at old → xl at new). Off-scale values (40, 3rem, 1.4px) need design review independent of the shift."
      action: "Follow-up — each instance needs per-case review: did the original author want a specific px value (snap to nearest post-shift token) OR a specific semantic level (use same name, accept new px value)? Bundle with omr-js code drift cleanup ticket."
    bare-rounded-in-code:
      claim: "Code uses bare `rounded` (no suffix) 140 times across 79 files"
      reality: "`rounded` and `rounded-sm` resolve to the same 4px value in OMR's theme (via `--radius: 4px`). Two ways to express the same value creates ambiguity for code reviews, AI agents, and future contributors."
      action: "Mechanical search/replace `rounded` → `rounded-sm` across 79 files. Visual no-op (both compile to identical CSS). Tracked in omr-js code drift cleanup ticket."
---

# Radius

## TL;DR

OMR uses a **rounder-than-Tailwind canonical radius scale** that overrides Tailwind v4
defaults via `theme.css`. Use `rounded-sm` (6px) for most UI (buttons, inputs, chips),
`rounded-lg` (12px) for cards, `rounded-full` for pills/avatars. Never use
arbitrary values (`rounded-[16px]`) — every common value is on the scale.

> **⚠️ Doc-code drift:** This scale is the **aspirational canonical state**. Current
> omr-js code still renders Tailwind v4 default values (rounded-sm = 4px, rounded-lg = 8px,
> …) until the `theme.css` override is merged. See [Drift 5 — Rounder direction not yet in code](#drift-5--rounder-direction-not-yet-in-code).

---

## Architecture

| Layer | What it is | Where it lives |
|---|---|---|
| **Base radius CSS variable** | `--radius: 6px` (resolves the unsuffixed `rounded` Tailwind class to 6px — same as the new `rounded-sm`). Safety fallback only; bare `rounded` is **not canonical** — see scale below. | `theme.css` `@theme` block |
| **OMR-shifted scale** | `--radius-xs` … `--radius-3xl` (overrides Tailwind v4 defaults — see scale + Drift 5) | `theme.css` `@theme` block |
| **Utilities** | `rounded-*` plus per-side, per-corner, and logical-side variants | Tailwind v4 utility generator (consumes our CSS vars) |

> **OMR overrides the Tailwind v4 defaults.** Earlier the scale was identical
> to Tailwind v4, with only `--radius` redeclared. The "rounder direction" decision
> shifts every step upward (xs: 2→4, sm: 4→6, md: 6→8, lg: 8→12, xl: 12→16,
> 2xl: 16→24, 3xl: 24→32). `rounded-4xl` is dropped — the old `4xl` value (32 px)
> is absorbed by the new `rounded-3xl`. Implemented via `@theme` overrides in
> `theme.css` (see [Tailwind config reference](#tailwind-config-reference)).

---

## Radius scale

Tailwind v4 default scale. **This is the full list — use these and nothing else.**

| Tailwind class | CSS variable | rem | px | When to use |
|---|---|---|---|---|
| `rounded-none` | — | 0 | 0 | Explicitly no rounding — sharp corners |
| `rounded-xs` | `--radius-xs` | 0.25rem | 4 | Very subtle rounding — inline tags, code pills |
| `rounded-sm` | `--radius-sm` | 0.375rem | 6 | **Default UI radius** — buttons, inputs, chips, badges. **Canonical 6px token.** |
| `rounded-md` | `--radius-md` | 0.5rem | 8 | Slightly more rounded — secondary surfaces |
| `rounded-lg` | `--radius-lg` | 0.75rem | 12 | Cards, dropdowns, popovers, modals, toasts, banners, tooltips |
| `rounded-xl` | `--radius-xl` | 1rem | 16 | Larger panels, dialogs |
| `rounded-2xl` | `--radius-2xl` | 1.5rem | 24 | Tiles, large panels |
| `rounded-3xl` | `--radius-3xl` | 2rem | 32 | Hero cards, marketing surfaces — top of the scale |
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

### Picking a radius — canonical component mapping

The authoritative table. When you need a radius for a specific component, look here first.

| Radius | px | Components |
|---|---|---|
| `rounded-none` | 0 | Explicit sharp-corner override (rare) |
| `rounded-xs` | 4 | Inline `<code>`, `<pre>` code blocks |
| `rounded-sm` | 6 | **UI controls & tiles:** Button (all sizes/variants), Icon Button (square), Input/Select/Date/Autocomplete Field, Tag, Label Chip, Card (all `*Card` + the `card` utility), Tooltip, Dropdown, Popover, Checkbox |
| `rounded-md` | 8 | **Notification surfaces:** Toast, Message Banner |
| `rounded-lg` | 12 | **Overlay surface:** Modal / Dialog |
| `rounded-xl` | 16 | **Larger overlay surface:** Drawer / Side Modal / Large Panel |
| `rounded-2xl` | 24 | **Marketing / editorial:** Feature surface (CTA / Value-Prop / Pricing section) |
| `rounded-3xl` | 32 | **Hero:** Top-of-page marketing surface |
| `rounded-full` | — | **Pill-shaped / circular:** Badge, Chip Badge, Tag Chip, Icon Button (circular), Avatar, Radio Button, Switch / Toggle, Stepper indicator dots |

> **Hierarchy logic:** smaller / embedded UI gets the smaller radius; importance and physical size of overlays scale the radius up. A Toast looks slightly rounder than a Button, a Modal slightly rounder than a Toast, a Hero clearly rounder than a Modal. This visual cue helps users distinguish embedded controls from overlay surfaces from marketing surfaces.

### Quick reference (by visual archetype)

```
Component category                       → Radius
├─ Circular / pill (badge, avatar, …)    → rounded-full
├─ UI control or tile (button, input,
│  card, tag, tooltip, dropdown, …)      → rounded-sm   (6 px)
├─ Notification surface (toast, banner)  → rounded-md   (8 px)
├─ Modal / Dialog                        → rounded-lg   (12 px)
├─ Drawer / Side Modal                   → rounded-xl   (16 px)
├─ Marketing feature surface
│  (CTA, value-prop, pricing section)    → rounded-2xl  (24 px)
├─ Hero / top-of-page marketing          → rounded-3xl  (32 px)
├─ Inline code / pre                     → rounded-xs   (4 px)
└─ Explicit sharp corner                 → rounded-none
```

> **Most-used tokens in practice** (pre-shift, omr-js code as of today).
> `rounded-full` (61×), `rounded-sm` (54×), `rounded-lg` (25×), `rounded-md` (13×),
> `rounded-xs` (11×) account for ~95% of all radius usage. With the new mapping,
> `rounded-xl` / `rounded-2xl` / `rounded-3xl` get explicit homes (Drawer / Feature /
> Hero) — previously these tiers had no canonical use case. Every existing usage
> will render rounder automatically once the `theme.css` override lands
> (see [Drift 5](#drift-5--rounder-direction-not-yet-in-code)).

### Fallback when the component isn't in the table

- **Default to `rounded-sm` (6 px) for typical UI controls and tiles.** Most product UI lives here.
- **For overlay/floating surfaces, scale by component size + importance:**
  - Small annotation (tooltip-like) → `rounded-sm` (6 px)
  - Notification (toast-like) → `rounded-md` (8 px)
  - Modal / dialog → `rounded-lg` (12 px)
  - Larger panel / drawer → `rounded-xl` (16 px)
- **For marketing / editorial,** start at `rounded-2xl` (24 px). Only reach for `rounded-3xl` (32 px) when the surface is a top-of-page hero.
- **For circular / pill-shaped elements,** `rounded-full` (avatars, badges, switches, circular icon buttons).
- **Never use bare `rounded` (no suffix).** It resolves to the same 6 px as `rounded-sm` via the `--radius` variable but is **not part of OMR's canonical scale**. Always use the explicit `rounded-sm` form — see [Drift 4 — Bare `rounded` in code](#drift-4--bare-rounded-in-code).

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
| **Small standalone thumbnail** (logo grid, list-row thumbnail) | `rounded-xs` (4px) | `<img class="rounded-xs h-10 w-10" …/>` — barely-rounded, editorial |
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
✅ Card (rounded-lg, 12px) → Button inside (rounded-sm, 6px)        inner < outer
✅ Card (rounded-lg, 12px) → Badge inside (rounded-md, 8px)         inner < outer
❌ Card (rounded-sm, 6px)  → Button inside (rounded-lg, 12px)       inner > outer — looks wrong
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

So a `rounded-lg` (12px) card with `p-2` (8px padding) and an edge-hugging
button should use `rounded-xs` (4px) on the button if you want strictly parallel
corners (12 − 8 = 4). In practice, **inner ≤ outer is sufficient** — strict
tangency only matters when nested elements visually touch their container's corner.

### Real example from omr-js

`HostCard.vue` (pre-shift; will render rounder post-migration):
```html
<div class="rounded-lg border …">       <!-- outer card: post-shift 12px -->
  <div class="absolute … rounded-md …"> <!-- inner badge: post-shift 8px -->
    <!-- … -->
  </div>
</div>
```
Inner badge (8px) < outer card (12px). ✅ Relationship preserved through the shift.

---

## Context-aware radius (full-bleed surfaces)

When a surface stretches to a hard viewport edge (top/bottom/side), drop the
radius on **the side touching the edge**. Rounded corners against a flat
viewport edge read as broken.

| Surface position | Radius treatment |
|---|---|
| Floating (centred, away from edges) | Full `rounded-lg` (12px, or whatever the surface calls for) |
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

- ❌ `border-radius: 12px` or `style="border-radius: 12px"` — raw CSS. **Use** `rounded-lg`.
- ❌ `rounded-[8px]`, `rounded-[12px]`, `rounded-[4px]` — arbitrary values that exist on the scale. **Use** the named token (`rounded-md`, `rounded-lg`, `rounded-xs`).
- ❌ `rounded-[3rem]`, `rounded-[40px]`, `rounded-[1.4px]` — genuinely off-scale arbitrary values. If the design really needs a non-scale radius, push back on the design first — almost always an on-scale step works.
- ❌ Picking radii by Tailwind-v4-default values rather than OMR-canonical values. **Tailwind v4 defaults are NOT canonical OMR values** post-shift. AI agents and devs should consult this doc's scale, not Tailwind's documentation, for canonical px values.
- ❌ `rounded-s`, `rounded-m`, `rounded-l` as size names — **these are not OMR tokens.** `rounded-s-*` and `rounded-e-*` exist in Tailwind but mean *logical start/end*, not size. See Known drifts.
- ❌ Bare `rounded` (no suffix) — **always use `rounded-sm` instead.** They produce identical visual output (both 6px post-shift), but only `rounded-sm` is part of OMR's canonical scale. Bare `rounded` reads as ambiguous for code reviews, AI agents, and is fragile against future Tailwind upstream changes.
- ❌ Using `rounded-full` on rectangular elements that aren't pill-shaped — produces unexpected stadium shapes. `rounded-full` is for circles and pills only.
- ❌ Stacking arbitrary radii via per-corner variants (`rounded-tl-[7px] rounded-tr-[5px]`) — almost always wrong; design probably wants a single radius.

---

## Tailwind config reference

```css
/* theme.css — OMR radius overrides (canonical post-shift scale) */
@theme {
  /* Bare `rounded` falls back to this (matches new rounded-sm).
     Safety fallback only — devs should always use the explicit `rounded-sm`
     form. See "Anti-patterns" above. */
  --radius:     0.375rem;  /* 6px,  was 4px */

  /* Full scale — overrides Tailwind v4 defaults */
  --radius-xs:  0.25rem;   /* 4px,  was 2px */
  --radius-sm:  0.375rem;  /* 6px,  was 4px */
  --radius-md:  0.5rem;    /* 8px,  was 6px */
  --radius-lg:  0.75rem;   /* 12px, was 8px */
  --radius-xl:  1rem;      /* 16px, was 12px */
  --radius-2xl: 1.5rem;    /* 24px, was 16px */
  --radius-3xl: 2rem;      /* 32px, was 24px */
  /* --radius-4xl: removed (old 32px absorbed by new 3xl) */
}
```

> **This @theme block replaces the Tailwind v4 default scale.** Every consumer
> of omr-js will see the OMR-canonical (rounder) values. The override is the
> single source of truth — no individual component should set its own radius
> via arbitrary values.

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
<div class="rounded-[12px] …">…</div>
```
**Why wrong:** `rounded-lg` is exactly 12px (post-shift) and on-scale. **Use** `rounded-lg`.

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
`rounded-xs` (4px) — pick the visual intent, not a magic number.

---

## Known drifts

Documented for transparency; each has a follow-up.

### Drift 5 — Rounder direction not yet in code

This is the **biggest active drift** in the radius foundation. The OMR design system has chosen a system-wide rounder direction, shifting every named radius token one step up:

| Token | New canonical px (this doc) | Currently rendered px (omr-js code) | Δ |
|---|---|---|---|
| `rounded-xs` | **4** | 2 (Tailwind v4 default) | +2 |
| `rounded-sm` | **6** | 4 (`--radius` override = old default) | +2 |
| `rounded-md` | **8** | 6 (Tailwind v4 default) | +2 |
| `rounded-lg` | **12** | 8 (Tailwind v4 default) | +4 |
| `rounded-xl` | **16** | 12 (Tailwind v4 default) | +4 |
| `rounded-2xl` | **24** | 16 (Tailwind v4 default) | +8 |
| `rounded-3xl` | **32** | 24 (Tailwind v4 default) | +8 |

**What this means:**
- The scale documented above is the **aspirational canonical state**.
- Current omr-js code renders the OLD (Tailwind v4 default) values until the `theme.css` override lands.
- Once the override is merged, every `rounded-*` class across the product renders +2 to +8 px rounder automatically. No code changes per component needed.

**Follow-up:** Tracked in the omr-js code drift cleanup ticket. Visual regression sweep across Storybook + Pages required before merge. Communicate to broader team before code change — this is a system-wide visual shift.

### Drift 1 — `CLAUDE.md` claims `rounded-s/m/l` are canonical

The current top-level `CLAUDE.md` lists `rounded, rounded-s, rounded-m, rounded-l, rounded-full`
as the allowed radius tokens. **Those size variants do not exist in code.** The
real scale is the Tailwind v4 defaults documented above. `rounded-s-*` and
`rounded-e-*` exist as logical-side utilities (start/end), but never as size names.

**Follow-up:** update `CLAUDE.md` to reflect the actual scale.

### Drift 2 — Figma values out of sync with OMR canonical

The Figma `Radius` collection currently uses **pre-shift** values that match neither Tailwind v4 defaults nor OMR's new post-shift canonical:

| Figma token | Figma value | OMR canonical (post-shift) | Drift |
|---|---|---|---|
| `rounded-sm` | 2 px | 6 px | -4 |
| `rounded` (unsuffixed) | 4 px | 6 px (`--radius`) | -2 |
| `_rounded-md` | 6 px | 8 px | -2 |
| `rounded-lg` | 8 px | 12 px | -4 |
| `_rounded-xl` | 12 px | 16 px | -4 |
| `rounded-2xl` | 16 px | 24 px | -8 |
| `_rounded-3xl` | 24 px | 32 px | -8 |
| `_rounded-full` | 9999 | 9999 | matches |

Several tokens carry `_` prefix (likely marked deprecated/internal). The OMR canonical scale also drops `rounded-4xl` entirely.

**Follow-up:** Reconcile Figma values to OMR canonical scale — same migration applied to omr-js code. Bundle with the omr-js drift cleanup ticket.

### Drift 4 — Bare `rounded` in code

omr-js code currently uses bare `rounded` (no suffix) **140 times across 79 files** (high concentration in `events-ui` Timetable and `hygraph-ui` Section components). Both `rounded` and `rounded-sm` resolve to the same 4px in OMR's theme — the bare form is **visually equivalent but not canonical**.

**Why fix:**
- Two ways to express the same value creates ambiguity for code reviews and AI agents
- Future Tailwind upstream changes could decouple `--radius` from `--radius-sm`
- Documentation should have one canonical answer per use case

**Follow-up:** Mechanical search/replace `rounded` → `rounded-sm` across all 79 files. **Visual no-op** (both compile to identical CSS, since `--radius` is set to 4px). Tracked in the omr-js code drift cleanup ticket — bundled with the other spacing/sizing drift fixes.

### Drift 3 — Arbitrary values in code

Found in `omr-js`:
- `rounded-[4px]` (×2) → **ambiguous**: snap to `rounded-xs` (4 px, preserves px) OR `rounded-sm` (6 px, preserves original semantic intent of "default UI radius"). Per-case review.
- `rounded-[8px]` (×1) → **ambiguous**: `rounded-md` (8 px, preserves px) OR `rounded-lg` (12 px, preserves original "card-surface" intent).
- `rounded-[16px]` (×1) → **ambiguous**: `rounded-xl` (16 px, preserves px) OR `rounded-2xl` (24 px, preserves original "large panel" intent).
- `rounded-[40px]` (×1) → off-scale; investigate intent (probably a near-pill shape).
- `rounded-[3rem]` (×1) → 48 px, off-scale; same.
- `rounded-[1.4px]` (×1) → sub-pixel hack; investigate.

> **Why these are now ambiguous:** before the rounder-direction shift, arbitrary px values aligned cleanly with named tokens (`rounded-[4px]` ≈ `rounded-sm` at 4 px). After the shift, the named tokens carry NEW px values — so each arbitrary value could resolve either by keeping the exact pixel value (snap to whichever token matches the new px) or by preserving the original semantic intent (use the same named token at its new larger px).

**Follow-up:** Each arbitrary-value instance needs per-case review. Bundle with omr-js code drift cleanup ticket.

---

## Cross-references

- [`spacing.md`](./spacing.md) — spacing scale (separate from radius but uses the same 4px base unit)
- [`color.md`](./color.md) — borders and backgrounds that pair with radius for surface definition
- [`../concepts/component-padding.md`](../concepts/component-padding.md) — component-level decisions that combine padding + radius (e.g. cards use `rounded-lg` + `padding-card`)
- [`../concepts/elevation-system.md`](../concepts/elevation-system.md) (todo) — how radius pairs with shadow/border for surface hierarchy
- [`../CLAUDE.md`](../CLAUDE.md) — agent rules (note: radius section there is currently inaccurate — see Known drifts above)
