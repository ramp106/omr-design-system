---
title: Component Padding
type: concept
status: draft
last_updated: 2026-05-10
related: [../foundations/spacing.md, ../foundations/sizing.md, ../foundations/typography.md]
---

# Component Padding

## TL;DR

Component-internal padding is **tokenised per component, not picked freshly per
instance**. Every component has a canonical padding token (e.g. `padding-card`,
`padding-button-m-x`) that maps to a value on the spacing scale. Use the
component-padding token in code and design — never an inline `p-*` choice
inside a component definition. This document is the **source of truth** for
those tokens.

---

## Status — MVP scope

This document is in **draft**. It currently covers three components as MVP:

| Component | Status | Source |
|---|---|---|
| Card | drafted from code | `card` utility in `utilities.css` |
| Button (semantic) | drafted from code | `semanticButtons.generated.css` |
| InputField | drafted from code | `useFormFieldClasses.ts` + `InputField.vue` |

All other components are listed in [§ TBD inventory](#tbd-inventory) below and
will be added in subsequent iterations.

---

## Foundations involved

| Foundation | What it contributes |
|---|---|
| [Spacing](../foundations/spacing.md) | The numeric scale (`p-1` … `p-96`) that every padding token aliases to |
| [Sizing](../foundations/sizing.md) (todo) | Component heights/widths — paired with padding to determine total visual size (e.g. button `h-10` + horizontal padding) |
| [Typography](../foundations/typography.md) | Internal vertical rhythm (line-height of body text affects effective padding-feel) |

---

## Why a token layer (and not just `p-*` utilities)

Three problems that raw Tailwind utilities don't solve:

1. **Inconsistency drift.** Every `<Card>` instance picking its own `p-6` vs `p-4`
   produces silent visual drift over time. A token freezes the decision once.
2. **Cross-channel parity.** A designer in Figma needs to bind a token to a
   component's padding field. With raw px values, design and code are unlinked
   — they can drift independently.
3. **Refactor cost.** Changing card padding system-wide is a multi-file find/replace
   if it's encoded as `p-6` in N components. With a token, it's a single value change.

This layer is the **bridge** between the primitive [Spacing](../foundations/spacing.md)
scale and the components that consume it.

---

## Naming convention

```
padding-{component}-{variant?}-{axis?}
gap-{component}-{variant?}
```

- **`{component}`** — the component name in kebab-case (`card`, `button`, `input`, `modal`)
- **`{variant?}`** — size or style modifier when the component has variants (`xs` / `s` / `m` / `l`, or `body` / `header`). Omit for components without variants.
- **`{axis?}`** — `x` (horizontal), `y` (vertical), or omitted (all sides). Omit when a single value covers all sides.
- **Internal gaps** between a component's children use `gap-{component}-{variant?}` — same naming, different prefix.

Examples:
- `padding-card` — single value, all sides
- `padding-button-m-x` — medium button, horizontal only
- `padding-input-y` — input vertical (no variant differentiation)
- `gap-button-l` — internal gap between icon and label in large button

---

## Master table — MVP components

### Card

The standard card surface (used by `card` utility, plus all `*Card` components).
One token, applied to all sides.

| Token | Value | Tailwind expression | Source |
|---|---|---|---|
| `padding-card` | 24px | `p-6` | `card` utility: `px-6 py-6` |

> **Currently in code:** `@utility card { @apply … px-6 py-6; }` —
> matches the canonical token. ✅

---

### Button (semantic buttons: `btn-{variant}-{intent}-{size}`)

Buttons have **horizontal padding only** (vertical sizing is determined by the
button height — `h-8` / `h-10` / `h-12` / `h-16`). Internal `gap` separates
icon from label.

| Token | Value | Tailwind expression | Source |
|---|---|---|---|
| `padding-button-xs-x` | 10px | `px-2.5` | `btn-*-xs`: `px-[10px]` ⚠️ |
| `padding-button-s-x` | 14px | `px-3.5` | `btn-*-s`: `px-[14px]` ⚠️ |
| `padding-button-m-x` | **18px** | `px-[18px]` ⚠️ off-scale | `btn-*-m`: `px-[18px]` ⚠️ |
| `padding-button-l-x` | 24px | `px-6` | `btn-*-l`: `px-[24px]` ⚠️ |
| `gap-button-xs` | 8px | `gap-2` | `btn-*-xs`: `gap-2` ✅ |
| `gap-button-s` | 8px | `gap-2` | `btn-*-s`: `gap-2` ✅ |
| `gap-button-m` | 12px | `gap-3` | `btn-*-m`: `gap-3` ✅ |
| `gap-button-l` | 20px | `gap-5` | `btn-*-l`: `gap-5` ✅ |

> **⚠️ Code drift — pending review (TBD with Michelle).** All button horizontal
> paddings are currently written as **arbitrary values** (`px-[10px]`, `px-[14px]`,
> `px-[18px]`, `px-[24px]`) in `semanticButtons.generated.css`. Three of the
> four values (10, 14, 24) are *on* the Tailwind scale but written off-scale —
> trivial fix. The fourth (`padding-button-m-x: 18px`) is genuinely off-scale —
> the nearest scale steps are `px-4` (16px) and `px-5` (20px). **Decision pending:**
> change the value to land on the scale, or accept the off-scale and document
> a single sanctioned exception. → TBD.

> **Heights are sizing tokens, not padding tokens.** `h-8` / `h-10` / `h-12` / `h-16`
> for the four button sizes will be documented in [`sizing.md`](../foundations/sizing.md) (todo).

---

### InputField

The form input surface. Container height comes from sizing; padding is split
between input element and prepend/append slots.

| Token | Value | Tailwind expression | Source |
|---|---|---|---|
| `padding-input-x-default` | 14px | `px-3.5` | `InputField.vue`: content slot `pl-3.5` (no prepend) |
| `padding-input-x-with-prepend` | 8px | `px-2` | `InputField.vue`: content slot `pl-2` (with prepend) |
| `padding-input-y` | 10px | `py-2.5` | `useFormFieldClasses.ts`: native input `py-2.5` |
| `padding-input-prepend` | 10px | `p-2.5` | `useFormFieldClasses.ts`: prepend `p-2.5` |
| `padding-input-prepend-l` | 14px | `pl-3.5` | `useFormFieldClasses.ts`: prepend `pl-3.5` |
| `padding-input-append` | 10px | `p-2.5` | `InputField.vue`: append wrapper `m-2.5 mr-3.5` |
| `padding-input-append-r` | 14px | `pr-3.5` | `InputField.vue`: append wrapper `mr-3.5` |

> **Heights** (`h-8` / `h-10` / `h-12` for sizes `s` / `m` / `default`)
> are sizing tokens — see [`sizing.md`](../foundations/sizing.md) (todo).

> **All values are on-scale** (10 = `p-2.5`, 14 = `p-3.5`, 8 = `p-2`) but currently
> written as the raw scale utilities. ✅ No drift, just verbose token coverage.

---

## TBD inventory

Components that need padding tokens but haven't been audited yet. Listed in
rough priority order. Each gets a row in the master table once audited.

| Component | Source (file) | Priority | Notes |
|---|---|---|---|
| `IconButton` | `core-ui/components/IconButton/IconButton.vue` | high | Square button, no x/y split — single padding token |
| `ChipBadge` | `core-ui/components/ChipBadge/ChipBadge.vue` | high | Chip-style padding, plus internal gap |
| `TagChip` | `core-ui/components/TagChip/` | high | Probably similar to ChipBadge — consider whether to merge |
| `LabelChip` | `core-ui/components/LabelChip/` | medium | |
| `ModalDialog` | `core-ui/components/ModalDialog/ModalDialog.vue` | high | Multi-region (header / body / footer) |
| `SideModal` | `core-ui/components/SideModal/` | medium | |
| `ToastMsg` | `core-ui/components/ToastMsg/ToastMsg.vue` | high | |
| `Tooltip` | `core-ui/components/Tooltip/` | medium | Small surface — likely tight padding |
| `MessageBanner` | `core-ui/components/MessageBanner/` | medium | |
| `DropDown` | `core-ui/components/DropDown/` | medium | Menu-item padding + container padding |
| `DropDownMultiSelect` | `core-ui/components/DropDownMultiSelect/` | low | |
| `TabBar` | `core-ui/components/TabBar/` | medium | Tab item padding |
| `Breadcrumbs` | `core-ui/components/Breadcrumbs/` | low | |
| `Carousel` | `core-ui/components/Carousel/` | low | |
| `Expandable` | `core-ui/components/Expandable/` | low | |
| `FilePicker` | `core-ui/components/FilePicker/` | low | |
| `FormElements/*` (others) | `core-ui/components/FormElements/` | medium | RadioButton, RadioCard, etc. |
| `*Card` (Article, Event, Job, etc.) | various | low | Probably reuse `padding-card` — confirm per-card |
| `Newsletter*` | `core-ui/components/Newsletter*/` | low | |
| `PaginationButtons` / `PaginationControl` | `core-ui/components/Pagination*/` | low | |

> **Migration note for `*Card` components.** Most card variants probably share
> the same `padding-card` value (24px). The audit should confirm or surface
> deviations — if AgencyCard has `p-4` but ProductCard has `p-6`, that's a
> drift to resolve.

---

## Decision rules

### Picking a component-padding token

- **Use the component's canonical token** — never override with a fresh `p-*`
  inside the component definition. If the canonical value is wrong, change the
  token (and update this doc), don't override locally.
- **Per-instance overrides** — when a single instance genuinely needs different
  padding (rare!), document why inline. If the override pattern repeats, it's a
  signal for a new variant token (e.g. `padding-card-compact`).
- **Cross-component reuse** — if Component A and Component B converge on the
  same padding value, give them separate tokens that *alias* to the same
  primitive. Don't share tokens — keeps each component independently tunable.
  *Exception:* the cards family probably shares `padding-card`.

### Adding a new component to this doc

1. Identify the component's padding values from its source file
2. Decide which axes need separate tokens (single value? x only? x + y?)
3. Decide which variants need separate tokens (size variants? state variants?)
4. Add a row to the master table with token name, value, Tailwind expression, source
5. Flag any off-scale values explicitly (`px-[18px]` etc.)
6. Move the component out of [TBD inventory](#tbd-inventory)

### When to introduce variants

Only when the design intent **differs** at the variant. A button's `xs` / `s` / `m` / `l`
have genuinely different paddings — variants belong. A card has one canonical
padding — no variants.

---

## Components explicitly out of scope

Some components have been considered and explicitly excluded from this concept,
either because they don't carry intrinsic padding or because their padding
belongs to a different concept entirely.

### `BtnLink` — routing wrapper, no own padding

`BtnLink` is a functional wrapper that switches between `<router-link>`, `<a>`,
or `<button>` depending on its props. It has **no styling and no intrinsic
padding**. When `BtnLink` is used as a styled button, padding comes from the
`btn-*` utility class applied to it (see [Button](#button-semantic-buttons-btn-variant-intent-size)).

→ No tokens needed. Not part of the master table.

### `PageSection` — section-rhythm, not component-padding

`PageSection`'s vertical padding (`pt-4 pb-8 tablet:pb-14`) is **section-level
vertical rhythm** — asymmetric, responsive, layout-driven. That's a different
concept (combines spacing + breakpoints + sizing), not component-internal padding.

→ Belongs in `concepts/section-rhythm.md` (todo). Not part of the master table.

---

## Margin handling — out of scope

Component-margin tokens are **deliberately not in this document**. Reasoning:

- **Components shouldn't dictate margin to their context.** A component with
  a fixed `mb-4` assumes there's a sibling to push away. Drop it elsewhere
  and the margin is wrong. Margin belongs to the *layout container*, not the
  component.
- **Tailwind's own guidance points the same way.** From the [Tailwind margin docs](https://tailwindcss.com/docs/margin)
  and [space utilities docs](https://tailwindcss.com/docs/space):
  > *"The space utilities are really just a shortcut for adding margin to
  > all-but-the-last-item in a group, and aren't designed to handle complex cases
  > like grids, layouts that wrap, or situations where the children are rendered
  > in a complex custom order rather than their natural DOM order. For those
  > situations, it's better to use the gap utilities when possible."*
- **Practically:** `flex flex-col gap-{token}` on the parent is the modern
  default for stack rhythm. Components stay context-free.

**What this means for this doc:**
- We tokenise **internal `gap`** (e.g. `gap-button-m` for icon-to-label spacing
  *inside* a button) — that's component-internal layout.
- We do **not** tokenise **external margin** (e.g. how much space below a
  button-in-a-form). That belongs in the parent's layout (`flex flex-col gap-4`),
  not in the button's tokens.

If a future use case actually requires component-owned external margin (rare —
typically isolated marketing components), we'll add a `margin-*` token family
then. Until then: leave margin to the consumer.

---

## Anti-patterns

- ❌ Using a raw `p-*` inside a component definition where a component-padding
  token exists. **Use** the token. If the token is missing, add it (and a TBD
  entry) — don't sidestep.
- ❌ Picking padding ad-hoc per Card instance: `<Card class="p-4" />` somewhere,
  `<Card class="p-6" />` elsewhere. **Use** `padding-card` consistently. If a
  variant is needed, add a variant token.
- ❌ Cross-component token reuse: applying `padding-card` directly to an Input.
  **Use** the input's own token (`padding-input-*`). They may resolve to the
  same value today, but coupling them prevents independent change later.
- ❌ Adding external margin to a component definition (`<Card class="mb-4" />`
  baked into the Card's template). **Use** layout-level spacing on the parent
  (`flex flex-col gap-4`) instead.
- ❌ Off-scale arbitrary values: `px-[18px]` to "match Figma". **Either** snap
  to the nearest scale step (`px-4` or `px-5`) **or** decide the off-scale
  value is intentional and document it as a sanctioned exception in this file.
  Silent off-scale is the worst outcome.

---

## Cross-references

- [`foundations/spacing.md`](../foundations/spacing.md) — the primitive scale
  every component-padding token aliases to
- [`foundations/sizing.md`](../foundations/sizing.md) (todo) — heights/widths
  paired with padding (e.g. button `h-10` + horizontal padding)
- [`foundations/typography.md`](../foundations/typography.md) — line-height
  contributes to perceived padding inside text-bearing components
- [`concepts/button-hierarchy.md`](./button-hierarchy.md) (todo) — which
  button variant for which intent (uses these padding tokens)
- [`concepts/density-and-rhythm.md`](./density-and-rhythm.md) (todo) — how
  component padding interacts with section spacing for overall density
- [`concepts/section-rhythm.md`](./section-rhythm.md) (todo) — section-level
  vertical rhythm (where `PageSection` and similar layout regions belong)
- [`../CLAUDE.md`](../CLAUDE.md) — agent rules

---

## Open questions for follow-up sessions

These are unresolved and need a working session to decide:

1. **Off-scale `padding-button-m-x: 18px`** — fix to scale (16 or 20) or sanction the exception?
2. **`*Card` family** — single shared `padding-card` or per-card variants? (audit needed)
3. **Code-side implementation** — when this doc stabilises, how do we expose tokens
   in `omr-js`? CSS custom properties? Tailwind theme extension? Separate plan.
4. **Figma-side implementation** — when this doc stabilises, how do we mirror tokens
   into the Figma file (correct scopes, proper aliasing)? Separate plan.
