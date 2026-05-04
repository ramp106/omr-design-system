---
title: [Foundation or Concept Name]
type: foundation        # foundation | concept
status: draft           # draft | stable | deprecated
last_updated: YYYY-MM-DD
related: []             # ["color.md", "spacing.md"]
---

# [Foundation or Concept Name]

## TL;DR

2-3 sentences. What this is, when it's relevant, what's the one thing
you should remember if you read nothing else.

---

## Architecture (foundations only)

If this foundation has a layered structure (e.g. primitives + semantic),
explain it here. Otherwise delete this section.

---

## Tokens / Scale (foundations only)

The canonical reference. One table per logical group. Always include:

| Tailwind utility | CSS variable | Usage |
|---|---|---|
| `...` | `--...` | One-line description of when this is the right choice |

**Rule:** values appear here and **only here**. Other sections reference
them by token name, never by raw value.

---

## Foundations involved (concepts only)

List which foundations this concept combines and why a cross-cutting
rule is needed:

| Foundation | What it contributes |
|---|---|
| Color | `bg-primary-main`, status colours |
| Typography | `txt-label-m-bold` for button text |
| Spacing | `px-4 py-2` for button padding |

---

## Decision rules ("Spielregeln")

**For foundations:** token-local rules only. These guide which token to pick
within this single foundation.

> **Separation rule:** Does this rule reference tokens from only one
> foundation? -> It belongs here. Does it reference 2+ foundations?
> -> Move it to a concept file, leave a cross-reference here.

- **Use X when** ... (typical case)
- **Use Y when** ... (exception case)
- **Default to Z** if the situation isn't covered above

**For concepts:** cross-cutting rules that combine tokens from multiple
foundations. Explain the combination pattern, not the individual tokens.

---

## Anti-patterns

What **not** to do. Be explicit — AI agents pattern-match well to "do"
examples but often miss "don't" constraints.

- ❌ Don't use `[wrong token]` — use `[correct token]` instead
- ❌ Don't hardcode `[value]` — use `[utility]` instead

---

## Tailwind config reference (foundations only)

Where these tokens are wired into Tailwind. Pseudo-code only — the
actual config lives in the codebase, but show the shape so an agent
knows what's available:

```css
/* @theme block, illustrative */
@theme {
  --token-name: var(--source-variable);
}
```

---

## Examples

### Do
Short, concrete, copy-pasteable snippets.

### Don't
The same scenario done wrong, with a 1-line explanation of why it's wrong.

---

## Cross-references

- Related foundations: `[link.md]`
- Related concepts: `[link.md]`
- Component specs that depend on this: `[link.md]`
