---
title: Agent Instructions — OMR Design System
type: agent-instructions
status: stable
last_updated: 2026-05-04
---

# Agent Instructions — OMR Design System

You are generating UI for the **OMR platform** (`omr-js`, Vue 3 + Tailwind v4).
This file is the contract between you and the OMR design system. Follow it on every task.

---

## Required reading — before writing any UI code

1. The relevant **foundation** file(s) in `foundations/` — tokens, values, and token-local constraints
2. The relevant **concept** file(s) in `concepts/` — cross-cutting rules that combine 2+ foundations
3. If it exists: the **component** file in `components/` — for variants and anatomy

**Foundations** answer "what token do I use?" (single foundation).
**Concepts** answer "how do I combine tokens?" (multiple foundations).

Producing UI without reading the relevant docs leads to token violations and inconsistent UI.
If a file is missing, **stop and ask the user** — do not invent the answer.

---

## Hard rules (blocking errors)

These are non-negotiable. Violating any of them is a blocking error and must be fixed before delivering code.

1. **Tailwind utilities only** for design tokens — never raw CSS values, never hex codes, never `style="..."` attributes.
2. **Semantic tokens only** for colors — `bg-surface`, `text-primary`, `border-error`. Never primitive tokens like `bg-purple-700` or `text-grey-500`.
3. **Typography** — use `txt-{category}-{size}-{weight}` utilities only. Never raw `font-size`, `font-weight`, `letter-spacing`.
4. **Spacing** — Tailwind utilities only (`p-4`, `gap-6`, `m-2`). Never raw `px` values.
5. **Z-index** — `z-{below,base,raised,dropdown,sticky,overlay,modal,toast}`. Never raw numbers.
6. **Border radius** — `rounded`, `rounded-s`, `rounded-m`, `rounded-l`, `rounded-full`. Never `rounded-[16px]` or arbitrary values.
7. **Transitions** — `var(--transition-*)` shorthands or `var(--duration-*)` / `var(--easing-*)`. Never hardcoded `200ms ease-out`.
8. **Generated files** — never edit or suggest edits to `*.generated.css`. Token updates go through Figma → `variables.json` → `pnpm extract`.

---

## Decision protocol

When making a UI choice that the docs cover:

1. Look up the rule in the relevant foundation/concept file
2. Apply the rule
3. If the rule has an explicit decision tree, follow it
4. If the rule is ambiguous or your case isn't covered, **ask the user** — don't guess

When making a UI choice that the docs **don't** cover:

1. Check if a sibling foundation/concept file might apply
2. If still nothing, ask the user — surface that the docs have a gap so they can be updated

---

## Anti-patterns

- ❌ Inventing variants not listed in the docs (e.g. a 6th button type, a "subtle-error" background)
- ❌ Mixing semantic and primitive tokens in the same component
- ❌ Hardcoding values "just for this one case"
- ❌ Adding `style="..."` inline to bypass utilities
- ❌ Editing `*.generated.css` to "fix" a token — fix it in Figma instead

---

## Output format

When generating Vue components, follow `<script setup lang="ts">` Composition API + TypeScript.
Use single quotes for strings, no comments, empty line at end of file.
After the code, add 3–5 bullets explaining variant choices so the designer can tweak them.

For accessibility see the OMR spec — semantic HTML + ARIA where needed, focus utilities `omr-focus-visible-outline` (open) or `omr-focus-visible-inset` (clipped containers).

---

## Cross-references

- Documentation index: [`README.md`](./README.md) — full list of foundations and concepts
- Foundations: `foundations/` — one file per token category
- Concepts: `concepts/` — cross-cutting decision rules
- Existing implementation reference: `omr-js/specs/` (component-level)
