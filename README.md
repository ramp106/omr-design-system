---
title: OMR Design System Documentation
type: index
status: in-progress
last_updated: 2026-05-10
---

# OMR Design System Documentation

AI-readable documentation of the OMR design system.
Used by humans for reference and by AI agents (Claude Code, Cursor, Claude.ai)
as the authoritative source for generating UI in `omr-js`.

> **For AI agents:** read [`CLAUDE.md`](./CLAUDE.md) **first**, then consult the
> foundation/concept files relevant to your task.

---

## How this documentation is organised

Two layers, one rule for deciding where content goes:

| Layer | Question it answers | Contains | Where it lives |
|---|---|---|---|
| **Foundations** | *What exists?* | Tokens, values, scales, plus **token-local constraints** (allowed values, defaults, when-to-use per token) | `foundations/` |
| **Concepts** | *How do tokens combine?* | **Cross-cutting decision rules** that touch 2+ foundations simultaneously | `concepts/` |

### The separation rule

> **Does this rule reference tokens from only one foundation?** Keep it in that foundation.
> **Does it reference tokens from multiple foundations?** It belongs in a concept.

Example: "Default to `text-main` for body text" is color-only -> `foundations/color.md`.
Example: "Button primary uses `bg-primary-main` + `txt-label-m-bold` + `px-4 py-2`" spans Color + Typography + Spacing -> `concepts/button-hierarchy.md`.

Foundations may include a cross-reference to a concept when a related rule lives there.

---

## Foundations — the vocabulary

What the system *has*. One file per token category. Every token shown with its
Tailwind utility, CSS variable, and intended use. Includes token-local constraints
and decision guidance.

| File | Status | Content |
|---|---|---|
| [`foundations/color.md`](./foundations/color.md) | stable | Semantic color tokens: text, bg, border, status, state, effects |
| [`foundations/typography.md`](./foundations/typography.md) | stable | `txt-*` utility system, weights, fluid sizes |
| [`foundations/spacing.md`](./foundations/spacing.md) | stable | 4 px-based scale, gap rules, layout utilities |
| `foundations/sizing.md` | todo | Component heights, container widths, icon sizes |
| [`foundations/radius.md`](./foundations/radius.md) | stable | Tailwind v4 radius scale + directional/logical utilities |
| `foundations/elevation.md` | todo | Surface tiers + z-index scale |
| `foundations/effects.md` | todo | Opacity, blur, transitions, durations, easings |
| [`foundations/breakpoints.md`](./foundations/breakpoints.md) | stable | Tablet / laptop / desktop / wide |

## Concepts — the grammar

How to combine foundations into consistent UI. Each concept touches 2+ foundations.
One file per cross-cutting decision.

| File | Status | Foundations involved |
|---|---|---|
| [`concepts/component-padding.md`](./concepts/component-padding.md) | draft | Spacing + Sizing + Typography (component-internal padding tokens) |
| `concepts/button-hierarchy.md` | todo | Color + Typography + Spacing + Radius |
| `concepts/elevation-system.md` | todo | Elevation + Effects (shadow) + Border + Z-index |
| `concepts/density-and-rhythm.md` | todo | Spacing + Sizing + Typography |
| `concepts/visual-hierarchy.md` | todo | Color + Typography + Spacing |
| `concepts/color-usage.md` | todo | Color + Typography (emphasis rules, status patterns) |
| `concepts/interactive-states.md` | todo | Color (state layers) + Effects (transitions) + Elevation |
| `concepts/icons.md` | todo | Sizing + Color + Spacing |
| `concepts/motion.md` | todo | Effects (transitions, durations, easings) |
| `concepts/accessibility.md` | todo | Color (contrast) + Typography (sizing) + Spacing (touch targets) |

## Templates

- [`_TEMPLATE.md`](./_TEMPLATE.md) — copy this when starting a new file

---

## Conventions

- **Language:** all docs in English (matches Linear convention)
- **Tailwind utilities** are the primary interface — CSS variables are the backing layer
- **Tokens are not invented in docs.** They reflect what's defined in the OMR token pipeline (Figma -> `variables.json` -> `pnpm extract` -> generated CSS)
- **Don't edit `*.generated.css`.** Token changes go through the pipeline above.
- **Token-local rules** (constraints, defaults, when-to-use) stay in the foundation file
- **Cross-cutting rules** (combining 2+ foundations) go in a concept file

---

## Project tracking

This documentation is the deliverable of the **Design System AI-Readiness** project
in Linear (`design-system-6e33db8ced8b`, Reviews team).
See Phase 1 milestone *Audit & Baseline* for related issues.
