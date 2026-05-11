---
title: Color
type: foundation
status: stable
last_updated: 2026-05-11
related: [elevation.md, typography.md, button-hierarchy.md, elevation-system.md]

tokens:
  # === Architecture ===
  layers:
    primitives:
      file: "packages/config-tailwind/src/omrTheme/primitiveColors.generated.css"
      usage: "Never use directly. Only inside semantic-token definitions."
    semantic-light:
      file: "packages/config-tailwind/src/omrTheme/lightTheme.generated.css"
      usage: "Always use via Tailwind utilities. Light theme variant."
    semantic-dark:
      file: "packages/config-tailwind/src/omrTheme/darkTheme.generated.css"
      usage: "Always use via Tailwind utilities. Dark theme variant. Same token names as light."

  # === Primitive palette (reference only — do not reference directly) ===
  primitive-scales:
    grey:      [0, 25, 50, 100, 150, 200, 250, 300, 350, 400, 450, 500, 550, 600, 650, 700, 750, 800, 850, 900, 950, 975, 1000]
    purple:    [25, 50, 100, 200, 300, 400, 500, 600, 700, 800, 900, 950]
    yellow:    [50, 100, 200, 300, 400, 500, 600, 700, 800, 900, 950]
    blue:      [25, 50, 100, 200, 300, 400, 500, 600, 700, 800, 900, 950]
    red:       [50, 100, 200, 300, 400, 500, 600, 700, 800, 900, 950]
    jade:      [50, 100, 200, 300, 400, 500, 600, 700, 800, 900, 950]
    green:     [50, 100, 200, 300, 400, 500, 600, 700, 800, 900, 950]
    mint:      [50, 100, 200, 300, 400, 500, 600, 700, 800, 900, 950]
    rose:      [50, 100, 200, 300, 400, 500, 600, 700, 800, 900, 950]

  primitive-aliases:
    color-white:       { resolves_to: "var(--color-grey-25)",  value: "#fdfdfd", note: "near-white" }
    color-true-white:  { resolves_to: null,                    value: "#ffffff" }
    color-black:       { resolves_to: "var(--color-grey-950)", value: "#0c0d0f", note: "near-black" }
    color-true-black:  { resolves_to: null,                    value: "#000000" }

  # === Text colors ===
  text:
    main:                       { tailwind: "text-main",                       var: "--text-color-main",                       usage: "Primary readable body text — the default" }
    subtle:                     { tailwind: "text-subtle",                     var: "--text-color-subtle",                     usage: "Secondary / supporting text" }
    subtlest:                   { tailwind: "text-subtlest",                   var: "--text-color-subtlest",                   usage: "Placeholder, hint text" }
    primary:                    { tailwind: "text-primary",                    var: "--text-color-primary",                    usage: "Brand purple — emphasis, brand mentions" }
    primary-subtle:             { tailwind: "text-primary-subtle",             var: "--text-color-primary-subtle",             usage: "Lighter brand purple text" }
    selected:                   { tailwind: "text-selected",                   var: "--text-color-selected",                   usage: "Highlighted / selected state text" }
    solid:                      { tailwind: "text-solid",                      var: "--text-color-solid",                      usage: "Pure black — charts, print contexts" }
    solid-inverse:              { tailwind: "text-solid-inverse",              var: "--text-color-solid-inverse",              usage: "Pure white — charts, print contexts" }
    inverse:                    { tailwind: "text-inverse",                    var: "--text-color-inverse",                    usage: "Text on dark backgrounds (pair with bg-surface-inverse)" }
    disabled:                   { tailwind: "text-disabled",                   var: "--text-color-disabled",                   usage: "Disabled labels" }
    error:                      { tailwind: "text-error",                      var: "--text-color-error",                      usage: "Error messages" }
    error-inverse:              { tailwind: "text-error-inverse",              var: "--text-color-error-inverse",              usage: "Error text on dark backgrounds" }
    success:                    { tailwind: "text-success",                    var: "--text-color-success",                    usage: "Success messages" }
    success-inverse:            { tailwind: "text-success-inverse",            var: "--text-color-success-inverse",            usage: "Success text on dark backgrounds" }
    warning:                    { tailwind: "text-warning",                    var: "--text-color-warning",                    usage: "Warning messages" }
    warning-inverse:            { tailwind: "text-warning-inverse",            var: "--text-color-warning-inverse",            usage: "Warning text on dark backgrounds" }
    badge-filled-success:       { tailwind: "text-badge-filled-success",       var: "--text-color-badge-filled-success",       usage: "Text on filled success badge" }
    badge-filled-warning:       { tailwind: "text-badge-filled-warning",       var: "--text-color-badge-filled-warning",       usage: "Text on filled warning badge" }
    badge-filled-error:         { tailwind: "text-badge-filled-error",         var: "--text-color-badge-filled-error",         usage: "Text on filled error badge" }

  icon:
    main:                       { tailwind: "text-icon-main",                  var: "--text-color-icon-main",                  usage: "Default icons" }
    subtle:                     { tailwind: "text-icon-subtle",                var: "--text-color-icon-subtle",                usage: "Secondary icons" }
    subtlest:                   { tailwind: "text-icon-subtlest",              var: "--text-color-icon-subtlest",              usage: "Tertiary / muted icons" }
    primary:                    { tailwind: "text-icon-primary",               var: "--text-color-icon-primary",               usage: "Brand icons" }
    primary-subtle:             { tailwind: "text-icon-primary-subtle",        var: "--text-color-icon-primary-subtle",        usage: "Lighter brand icons" }
    secondary:                  { tailwind: "text-icon-secondary",             var: "--text-color-icon-secondary",             usage: "Secondary brand icons (yellow)" }
    secondary-subtle:           { tailwind: "text-icon-secondary-subtle",      var: "--text-color-icon-secondary-subtle",      usage: "Lighter secondary icons" }
    selected:                   { tailwind: "text-icon-selected",              var: "--text-color-icon-selected",              usage: "Selected / highlighted icons" }
    solid:                      { tailwind: "text-icon-solid",                 var: "--text-color-icon-solid",                 usage: "Pure black icons" }
    solid-inverse:              { tailwind: "text-icon-solid-inverse",         var: "--text-color-icon-solid-inverse",         usage: "Pure white icons" }
    inverse:                    { tailwind: "text-icon-inverse",               var: "--text-color-icon-inverse",               usage: "Icons on dark backgrounds" }
    disabled:                   { tailwind: "text-icon-disabled",              var: "--text-color-icon-disabled",              usage: "Disabled icons" }
    error:                      { tailwind: "text-icon-error",                 var: "--text-color-icon-error",                 usage: "Error icons" }
    error-inverse:              { tailwind: "text-icon-error-inverse",         var: "--text-color-icon-error-inverse",         usage: "Error icons on dark backgrounds" }
    success:                    { tailwind: "text-icon-success",               var: "--text-color-icon-success",               usage: "Success icons" }
    success-inverse:            { tailwind: "text-icon-success-inverse",       var: "--text-color-icon-success-inverse",       usage: "Success icons on dark backgrounds" }
    warning:                    { tailwind: "text-icon-warning",               var: "--text-color-icon-warning",               usage: "Warning icons" }
    warning-inverse:            { tailwind: "text-icon-warning-inverse",       var: "--text-color-icon-warning-inverse",       usage: "Warning icons on dark backgrounds" }
    badge-filled-success:       { tailwind: "text-icon-badge-filled-success",  var: "--text-color-icon-badge-filled-success",  usage: "Icon on filled success badge" }
    badge-filled-warning:       { tailwind: "text-icon-badge-filled-warning",  var: "--text-color-icon-badge-filled-warning",  usage: "Icon on filled warning badge" }
    badge-filled-error:         { tailwind: "text-icon-badge-filled-error",    var: "--text-color-icon-badge-filled-error",    usage: "Icon on filled error badge" }

  link:
    main:     { tailwind: "text-link-main",     var: "--text-color-link-main",     usage: "Default link colour" }
    primary:  { tailwind: "text-link-primary",  var: "--text-color-link-primary",  usage: "Brand-coloured link" }
    inverse:  { tailwind: "text-link-inverse",  var: "--text-color-link-inverse",  usage: "Link on dark backgrounds" }
    disabled: { tailwind: "text-link-disabled", var: "--text-color-link-disabled", usage: "Disabled link" }

  # === Background colors ===
  background-surface:
    surface:                { tailwind: "bg-surface",                var: "--background-color-surface",                usage: "Page base — the canvas" }
    solid:                  { tailwind: "bg-solid",                  var: "--background-color-solid",                  usage: "Pure white (e.g. cards on tinted pages)" }
    surface-elevation-1:    { tailwind: "bg-surface-elevation-1",    var: "--background-color-surface-elevation-1",    usage: "+1 depth (lightest grey above page)" }
    surface-elevation-2:    { tailwind: "bg-surface-elevation-2",    var: "--background-color-surface-elevation-2",    usage: "+2 depth" }
    surface-elevation-3:    { tailwind: "bg-surface-elevation-3",    var: "--background-color-surface-elevation-3",    usage: "+3 depth" }
    surface-elevation-4:    { tailwind: "bg-surface-elevation-4",    var: "--background-color-surface-elevation-4",    usage: "+4 depth" }
    surface-elevation-5:    { tailwind: "bg-surface-elevation-5",    var: "--background-color-surface-elevation-5",    usage: "+5 depth (darkest grey, rare)" }
    surface-inverse:        { tailwind: "bg-surface-inverse",        var: "--background-color-surface-inverse",        usage: "Dark surface (pair with text-inverse)" }

  background-surface-alpha:
    surface-alpha-elevation-1: { tailwind: "bg-surface-alpha-elevation-1", var: "--background-color-surface-alpha-elevation-1", usage: "Transparent +1 depth — content shows through" }
    surface-alpha-elevation-2: { tailwind: "bg-surface-alpha-elevation-2", var: "--background-color-surface-alpha-elevation-2", usage: "Transparent +2 depth" }
    surface-alpha-elevation-3: { tailwind: "bg-surface-alpha-elevation-3", var: "--background-color-surface-alpha-elevation-3", usage: "Transparent +3 depth" }
    surface-alpha-elevation-4: { tailwind: "bg-surface-alpha-elevation-4", var: "--background-color-surface-alpha-elevation-4", usage: "Transparent +4 depth" }
    surface-alpha-elevation-5: { tailwind: "bg-surface-alpha-elevation-5", var: "--background-color-surface-alpha-elevation-5", usage: "Transparent +5 depth" }

  background-primary:
    primary-main:        { tailwind: "bg-primary-main",        var: "--background-color-primary-main",        usage: "Brand purple fill — primary buttons, brand emphasis" }
    primary-strong:      { tailwind: "bg-primary-strong",      var: "--background-color-primary-strong",      usage: "Darker brand purple — hover on primary" }
    primary-stronger:    { tailwind: "bg-primary-stronger",    var: "--background-color-primary-stronger",    usage: "Even darker — pressed state" }
    primary-strongest:   { tailwind: "bg-primary-strongest",   var: "--background-color-primary-strongest",   usage: "Darkest brand purple" }
    primary-subtle:      { tailwind: "bg-primary-subtle",      var: "--background-color-primary-subtle",      usage: "Pale purple fill — selected items, brand banners" }
    primary-subtler:     { tailwind: "bg-primary-subtler",     var: "--background-color-primary-subtler",     usage: "Lighter pale purple" }
    primary-subtlest:    { tailwind: "bg-primary-subtlest",    var: "--background-color-primary-subtlest",    usage: "Lightest pale purple — backgrounds, hovers" }

  background-primary-alpha:
    primary-alpha-strong:    { tailwind: "bg-primary-alpha-strong",    var: "--background-color-primary-alpha-strong",    usage: "Transparent dark brand purple overlay" }
    primary-alpha-stronger:  { tailwind: "bg-primary-alpha-stronger",  var: "--background-color-primary-alpha-stronger",  usage: "Transparent darker brand purple overlay" }
    primary-alpha-strongest: { tailwind: "bg-primary-alpha-strongest", var: "--background-color-primary-alpha-strongest", usage: "Transparent darkest brand purple overlay" }
    primary-alpha-subtle:    { tailwind: "bg-primary-alpha-subtle",    var: "--background-color-primary-alpha-subtle",    usage: "Transparent pale purple overlay" }
    primary-alpha-subtler:   { tailwind: "bg-primary-alpha-subtler",   var: "--background-color-primary-alpha-subtler",   usage: "Transparent lighter pale purple overlay" }
    primary-alpha-subtlest:  { tailwind: "bg-primary-alpha-subtlest",  var: "--background-color-primary-alpha-subtlest",  usage: "Transparent lightest pale purple overlay" }

  background-secondary:
    secondary-main:      { tailwind: "bg-secondary-main",      var: "--background-color-secondary-main",      usage: "Secondary yellow fill — accent elements" }
    secondary-strong:    { tailwind: "bg-secondary-strong",    var: "--background-color-secondary-strong",    usage: "Darker secondary — hover on secondary" }
    secondary-stronger:  { tailwind: "bg-secondary-stronger",  var: "--background-color-secondary-stronger",  usage: "Even darker secondary" }
    secondary-strongest: { tailwind: "bg-secondary-strongest", var: "--background-color-secondary-strongest", usage: "Darkest secondary" }
    secondary-subtle:    { tailwind: "bg-secondary-subtle",    var: "--background-color-secondary-subtle",    usage: "Pale yellow fill" }
    secondary-subtler:   { tailwind: "bg-secondary-subtler",   var: "--background-color-secondary-subtler",   usage: "Lighter pale yellow" }
    secondary-subtlest:  { tailwind: "bg-secondary-subtlest",  var: "--background-color-secondary-subtlest",  usage: "Lightest pale yellow — backgrounds" }

  background-status:
    error-strong:    { tailwind: "bg-error-strong",    var: "--background-color-error-strong",    usage: "Solid error fill — high-emphasis indicators" }
    error-subtle:    { tailwind: "bg-error-subtle",    var: "--background-color-error-subtle",    usage: "Pale error tint — banners, badges" }
    success-strong:  { tailwind: "bg-success-strong",  var: "--background-color-success-strong",  usage: "Solid success fill" }
    success-subtle:  { tailwind: "bg-success-subtle",  var: "--background-color-success-subtle",  usage: "Pale success tint" }
    warning-strong:  { tailwind: "bg-warning-strong",  var: "--background-color-warning-strong",  usage: "Solid warning fill" }
    warning-subtle:  { tailwind: "bg-warning-subtle",  var: "--background-color-warning-subtle",  usage: "Pale warning tint" }
    disabled:        { tailwind: "bg-disabled",        var: "--background-color-disabled",        usage: "Disabled element fill" }

  background-badge:
    badge-filled-success: { tailwind: "bg-badge-filled-success", var: "--background-color-badge-filled-success", usage: "Filled success badge background" }
    badge-filled-warning: { tailwind: "bg-badge-filled-warning", var: "--background-color-badge-filled-warning", usage: "Filled warning badge background" }
    badge-filled-error:   { tailwind: "bg-badge-filled-error",   var: "--background-color-badge-filled-error",   usage: "Filled error badge background" }

  background-component:
    # Reference only — use semantic tokens above for general UI
    button:    ["button-outline", "button-outline-color", "button-outline-destructive", "button-outline-success", "button-primary-color", "button-primary-destructive", "button-primary-neutral", "button-primary-success", "button-secondary-color", "button-secondary-destructive", "button-secondary-neutral", "button-secondary-success"]
    timetable: ["timetable-event-active", "timetable-event-inactive", "timetable-event-passed", "timetable-meeting-active", "timetable-meeting-inactive", "timetable-meeting-passed"]
    ui-chrome: ["scrollbar-handle", "toggle-inactive"]

  background-backdrop:
    effect-backdrop-overlay: { tailwind: "bg-effect-backdrop-overlay", var: "--background-color-effect-backdrop-overlay", usage: "Modal backdrop — pair with backdrop-blur-xs" }
    effect-focused:          { tailwind: "bg-effect-focused",          var: "--background-color-effect-focused",          usage: "Focus ring background (rare — see effect-text)" }

  # === Border colors ===
  border:
    main:                   { tailwind: "border-main",                   var: "--border-color-main",                   usage: "Default border — most cards, inputs, dividers" }
    main-solid:             { tailwind: "border-main-solid",             var: "--border-color-main-solid",             usage: "Solid (no alpha) variant for crisp edges" }
    subtle:                 { tailwind: "border-subtle",                 var: "--border-color-subtle",                 usage: "De-emphasised dividers" }
    strong:                 { tailwind: "border-strong",                 var: "--border-color-strong",                 usage: "Strong emphasis — modal headers, sticky bars" }
    primary:                { tailwind: "border-primary",                var: "--border-color-primary",                usage: "Brand purple border" }
    primary-solid:          { tailwind: "border-primary-solid",          var: "--border-color-primary-solid",          usage: "Solid brand border" }
    primary-subtle:         { tailwind: "border-primary-subtle",         var: "--border-color-primary-subtle",         usage: "Subtle brand purple border" }
    primary-subtle-solid:   { tailwind: "border-primary-subtle-solid",   var: "--border-color-primary-subtle-solid",   usage: "Solid subtle brand border" }
    secondary:              { tailwind: "border-secondary",              var: "--border-color-secondary",              usage: "Secondary yellow border" }
    secondary-subtle:       { tailwind: "border-secondary-subtle",       var: "--border-color-secondary-subtle",       usage: "Subtle secondary border" }
    error:                  { tailwind: "border-error",                  var: "--border-color-error",                  usage: "Error state — invalid inputs" }
    error-subtle:           { tailwind: "border-error-subtle",           var: "--border-color-error-subtle",           usage: "Subtle error border — banners" }
    success:                { tailwind: "border-success",                var: "--border-color-success",                usage: "Success state" }
    success-subtle:         { tailwind: "border-success-subtle",         var: "--border-color-success-subtle",         usage: "Subtle success border" }
    warning:                { tailwind: "border-warning",                var: "--border-color-warning",                usage: "Warning state" }
    warning-subtle:         { tailwind: "border-warning-subtle",         var: "--border-color-warning-subtle",         usage: "Subtle warning border" }
    selected:               { tailwind: "border-selected",               var: "--border-color-selected",               usage: "Selection indicator (chips, radio, options)" }
    disabled:               { tailwind: "border-disabled",               var: "--border-color-disabled",               usage: "Disabled state" }
    inverse:                { tailwind: "border-inverse",                var: "--border-color-inverse",                usage: "Border on dark backgrounds" }

  # === Effect colors (focus, overlays) ===
  effect-text:
    focused:                       { tailwind: "text-effect-focused",                       var: "--text-color-effect-focused",                       usage: "Focus ring outline colour (2px solid)" }
    backdrop-overlay:              { tailwind: "text-effect-backdrop-overlay",              var: "--text-color-effect-backdrop-overlay",              usage: "Text overlay on backdrop" }
    overlay-surface-solid:         { tailwind: "text-effect-overlay-surface-solid",         var: "--text-color-effect-overlay-surface-solid",         usage: "Text on solid overlay surface" }
    overlay-surface-strongest:     { tailwind: "text-effect-overlay-surface-strongest",     var: "--text-color-effect-overlay-surface-strongest",     usage: "Text on strongest overlay surface" }
    overlay-surface-subtlest:      { tailwind: "text-effect-overlay-surface-subtlest",      var: "--text-color-effect-overlay-surface-subtlest",      usage: "Text on subtlest overlay surface" }
    overlay-surface-transparent:   { tailwind: "text-effect-overlay-surface-transparent",   var: "--text-color-effect-overlay-surface-transparent",   usage: "Text on transparent overlay surface" }

  effect-background:
    focused:                       { tailwind: "bg-effect-focused",                         var: "--background-color-effect-focused",                       usage: "Focus ring background" }
    backdrop-overlay:              { tailwind: "bg-effect-backdrop-overlay",                var: "--background-color-effect-backdrop-overlay",              usage: "Modal backdrop overlay" }
    overlay-surface-solid:         { tailwind: "bg-effect-overlay-surface-solid",           var: "--background-color-effect-overlay-surface-solid",         usage: "Solid overlay surface background" }
    overlay-surface-strongest:     { tailwind: "bg-effect-overlay-surface-strongest",       var: "--background-color-effect-overlay-surface-strongest",     usage: "Strongest overlay surface background" }
    overlay-surface-subtlest:      { tailwind: "bg-effect-overlay-surface-subtlest",        var: "--background-color-effect-overlay-surface-subtlest",      usage: "Subtlest overlay surface background" }
    overlay-surface-transparent:   { tailwind: "bg-effect-overlay-surface-transparent",     var: "--background-color-effect-overlay-surface-transparent",   usage: "Transparent overlay surface background" }

  effect-utilities:
    omr-focus-visible-outline: { source: "utilities.css", usage: "Focus ring for open layouts" }
    omr-focus-visible-inset:   { source: "utilities.css", usage: "Focus ring for clipped containers (overflow-hidden)" }
    blur-overlay-style:        { source: "utilities.css", composes: ["bg-effect-backdrop-overlay", "backdrop-blur-xs"] }

  # === Graphic colors (charts, illustrations) ===
  graphic-core:
    black:    { tailwind: "graphic-black",    var: "--graphic-color-black",    usage: "Black graphic element" }
    white:    { tailwind: "graphic-white",    var: "--graphic-color-white",    usage: "White graphic element" }
    disabled: { tailwind: "graphic-disabled", var: "--graphic-color-disabled", usage: "Disabled/inactive graphic element" }

  graphic-status:
    error:   { tailwind: "graphic-error",   var: "--graphic-color-error",   usage: "Error indicator in graphics" }
    success: { tailwind: "graphic-success", var: "--graphic-color-success", usage: "Success indicator in graphics" }
    warning: { tailwind: "graphic-warning", var: "--graphic-color-warning", usage: "Warning indicator in graphics" }

  graphic-grey:
    grey-subtle: { tailwind: "graphic-grey-subtle", var: "--graphic-color-grey-subtle", usage: "Light grey — background fills, grid lines" }
    grey-medium: { tailwind: "graphic-grey-medium", var: "--graphic-color-grey-medium", usage: "Medium grey — secondary data series" }
    grey-strong: { tailwind: "graphic-grey-strong", var: "--graphic-color-grey-strong", usage: "Dark grey — labels, axes" }

  graphic-primary:
    primary-subtle: { tailwind: "graphic-primary-subtle", var: "--graphic-color-primary-subtle", usage: "Light purple — area fills, backgrounds" }
    primary-medium: { tailwind: "graphic-primary-medium", var: "--graphic-color-primary-medium", usage: "Medium purple — secondary series" }
    primary-strong: { tailwind: "graphic-primary-strong", var: "--graphic-color-primary-strong", usage: "Dark purple — primary data series, key metrics" }

  graphic-secondary:
    secondary-subtle: { tailwind: "graphic-secondary-subtle", var: "--graphic-color-secondary-subtle", usage: "Light yellow — area fills" }
    secondary-medium: { tailwind: "graphic-secondary-medium", var: "--graphic-color-secondary-medium", usage: "Medium yellow — secondary accent" }
    secondary-strong: { tailwind: "graphic-secondary-strong", var: "--graphic-color-secondary-strong", usage: "Dark yellow — accent data series" }

  graphic-tertiary:
    tertiary-subtle: { tailwind: "graphic-tertiary-subtle", var: "--graphic-color-tertiary-subtle", usage: "Light tertiary — area fills" }
    tertiary-medium: { tailwind: "graphic-tertiary-medium", var: "--graphic-color-tertiary-medium", usage: "Medium tertiary — third data series" }
    tertiary-strong: { tailwind: "graphic-tertiary-strong", var: "--graphic-color-tertiary-strong", usage: "Dark tertiary — tertiary data series" }

  # === Interaction state layers ===
  state-layer-composites:
    state-layer-neutral:         { tailwind: "state-layer-neutral",         usage: "Neutral interactive surfaces (cards, list items)", triggers: { hover: "bg-state-hover-neutral", pressed: "bg-state-pressed-neutral", drag: "bg-state-drag-neutral" } }
    state-layer-primary:         { tailwind: "state-layer-primary",         usage: "Brand-coloured interactive elements",              triggers: { hover: "bg-state-hover-primary", pressed: "bg-state-pressed-primary", drag: "bg-state-drag-primary" } }
    state-layer-neutral-inverse: { tailwind: "state-layer-neutral-inverse", usage: "Dark-themed surfaces",                              triggers: { hover: "bg-state-hover-neutral-inverse", pressed: "bg-state-pressed-neutral-inverse", drag: "bg-state-drag-neutral-inverse" } }

  state-raw:
    # For custom implementations only — prefer state-layer-* composites
    hover-neutral:           { tailwind: "bg-state-hover-neutral",           var: "--background-color-state-hover-neutral",           trigger: "hover on neutral surface" }
    pressed-neutral:         { tailwind: "bg-state-pressed-neutral",         var: "--background-color-state-pressed-neutral",         trigger: "press on neutral surface" }
    drag-neutral:            { tailwind: "bg-state-drag-neutral",            var: "--background-color-state-drag-neutral",            trigger: "drag on neutral surface" }
    hover-neutral-inverse:   { tailwind: "bg-state-hover-neutral-inverse",   var: "--background-color-state-hover-neutral-inverse",   trigger: "hover on dark surface" }
    pressed-neutral-inverse: { tailwind: "bg-state-pressed-neutral-inverse", var: "--background-color-state-pressed-neutral-inverse", trigger: "press on dark surface" }
    drag-neutral-inverse:    { tailwind: "bg-state-drag-neutral-inverse",    var: "--background-color-state-drag-neutral-inverse",    trigger: "drag on dark surface" }
    hover-primary:           { tailwind: "bg-state-hover-primary",           var: "--background-color-state-hover-primary",           trigger: "hover on brand surface" }
    pressed-primary:         { tailwind: "bg-state-pressed-primary",         var: "--background-color-state-pressed-primary",         trigger: "press on brand surface" }
    drag-primary:            { tailwind: "bg-state-drag-primary",            var: "--background-color-state-drag-primary",            trigger: "drag on brand surface" }
---

# Color

## TL;DR

OMR colors are a **two-layer system**: raw primitives auto-generated from Figma
(never use these directly), and **semantic tokens** that components reference via
Tailwind utilities. Choose tokens by **intent** (`text-primary` for brand,
`text-error` for errors), not by hue. Dark theme works automatically — no extra work needed.

---

## Architecture

| Layer | What it is | Where it lives | When to use it |
|---|---|---|---|
| **Layer 1 — Primitives** | Raw hex palette (e.g. `--color-purple-700`) | `primitiveColors.generated.css` | **Never directly.** Only inside semantic-token definitions. |
| **Layer 2 — Semantic tokens** | Intent-named tokens (e.g. `--text-color-primary`) | `lightTheme.generated.css`, `darkTheme.generated.css` | **Always.** Via Tailwind utilities (`text-primary`). |

> **Why two layers:** primitives can change without breaking components, dark theme
> can swap values per token, and AI agents have a small, intent-based vocabulary
> to choose from instead of hundreds of hex codes.

### Primitive palette (reference only — do not reference directly)

| Scale | Steps |
|---|---|
| **grey** | 0, 25, 50, 100, 150, 200, 250, 300, 350, 400, 450, 500, 550, 600, 650, 700, 750, 800, 850, 900, 950, 975, 1000 (23 steps) |
| **purple** | 25, 50, 100, 200, 300, 400, 500, 600, 700, 800, 900, 950 (12 steps) |
| **yellow** | 50, 100, 200, 300, 400, 500, 600, 700, 800, 900, 950 (11 steps) |
| **blue** | 25, 50, 100, 200, 300, 400, 500, 600, 700, 800, 900, 950 (12 steps) |
| **red** | 50, 100, 200, 300, 400, 500, 600, 700, 800, 900, 950 (11 steps) |
| **jade** | 50, 100, 200, 300, 400, 500, 600, 700, 800, 900, 950 (11 steps) |
| **green** | 50, 100, 200, 300, 400, 500, 600, 700, 800, 900, 950 (11 steps) |
| **mint** | 50, 100, 200, 300, 400, 500, 600, 700, 800, 900, 950 (11 steps) |
| **rose** | 50, 100, 200, 300, 400, 500, 600, 700, 800, 900, 950 (11 steps) |

**Special aliases** (defined in `theme.css`):

| Alias | Resolves to |
|---|---|
| `--color-white` | `var(--color-grey-25)` — near-white `#fdfdfd` |
| `--color-true-white` | `#ffffff` |
| `--color-black` | `var(--color-grey-950)` — near-black `#0c0d0f` |
| `--color-true-black` | `#000000` |

---

## Decision rule — which token category do I need?

```
What am I colouring?
├─ Text or icon       → Text colors / Icon colors
├─ A link             → Link colors
├─ A surface / fill   → Background colors
├─ A 1px line or ring → Border colors
├─ A hover/press/drag feedback layer → Interaction state colors
└─ A focus ring       → Effect colors
```

For **status meaning** (success/error/warning) the same rule applies but the
status modifier picks the variant — e.g. text feedback -> `text-error`,
filled status banner -> `bg-error-subtle` + `border-error` + `text-error`.

---

## Text colors

| Tailwind utility | CSS variable | Usage |
|---|---|---|
| `text-main` | `--text-color-main` | Primary readable body text — the default |
| `text-subtle` | `--text-color-subtle` | Secondary / supporting text |
| `text-subtlest` | `--text-color-subtlest` | Placeholder, hint text |
| `text-primary` | `--text-color-primary` | Brand purple — emphasis, brand mentions |
| `text-primary-subtle` | `--text-color-primary-subtle` | Lighter brand purple text |
| `text-selected` | `--text-color-selected` | Highlighted / selected state text |
| `text-solid` | `--text-color-solid` | Pure black — charts, print contexts |
| `text-solid-inverse` | `--text-color-solid-inverse` | Pure white — charts, print contexts |
| `text-inverse` | `--text-color-inverse` | Text on **dark** backgrounds (use with `bg-surface-inverse`) |
| `text-disabled` | `--text-color-disabled` | Disabled labels |
| `text-error` | `--text-color-error` | Error messages |
| `text-error-inverse` | `--text-color-error-inverse` | Error text on dark backgrounds |
| `text-success` | `--text-color-success` | Success messages |
| `text-success-inverse` | `--text-color-success-inverse` | Success text on dark backgrounds |
| `text-warning` | `--text-color-warning` | Warning messages |
| `text-warning-inverse` | `--text-color-warning-inverse` | Warning text on dark backgrounds |
| `text-badge-filled-success` | `--text-color-badge-filled-success` | Text on filled success badge |
| `text-badge-filled-warning` | `--text-color-badge-filled-warning` | Text on filled warning badge |
| `text-badge-filled-error` | `--text-color-badge-filled-error` | Text on filled error badge |

### Icons

| Utility | Variable | Usage |
|---|---|---|
| `text-icon-main` | `--text-color-icon-main` | Default icons |
| `text-icon-subtle` | `--text-color-icon-subtle` | Secondary icons |
| `text-icon-subtlest` | `--text-color-icon-subtlest` | Tertiary / muted icons |
| `text-icon-primary` | `--text-color-icon-primary` | Brand icons |
| `text-icon-primary-subtle` | `--text-color-icon-primary-subtle` | Lighter brand icons |
| `text-icon-secondary` | `--text-color-icon-secondary` | Secondary brand icons (yellow) |
| `text-icon-secondary-subtle` | `--text-color-icon-secondary-subtle` | Lighter secondary icons |
| `text-icon-selected` | `--text-color-icon-selected` | Selected / highlighted icons |
| `text-icon-solid` | `--text-color-icon-solid` | Pure black icons |
| `text-icon-solid-inverse` | `--text-color-icon-solid-inverse` | Pure white icons |
| `text-icon-inverse` | `--text-color-icon-inverse` | Icons on dark backgrounds |
| `text-icon-disabled` | `--text-color-icon-disabled` | Disabled icons |
| `text-icon-error` | `--text-color-icon-error` | Error icons |
| `text-icon-error-inverse` | `--text-color-icon-error-inverse` | Error icons on dark backgrounds |
| `text-icon-success` | `--text-color-icon-success` | Success icons |
| `text-icon-success-inverse` | `--text-color-icon-success-inverse` | Success icons on dark backgrounds |
| `text-icon-warning` | `--text-color-icon-warning` | Warning icons |
| `text-icon-warning-inverse` | `--text-color-icon-warning-inverse` | Warning icons on dark backgrounds |
| `text-icon-badge-filled-success` | `--text-color-icon-badge-filled-success` | Icon on filled success badge |
| `text-icon-badge-filled-warning` | `--text-color-icon-badge-filled-warning` | Icon on filled warning badge |
| `text-icon-badge-filled-error` | `--text-color-icon-badge-filled-error` | Icon on filled error badge |

### Links

| Utility | Variable | Usage |
|---|---|---|
| `text-link-main` | `--text-color-link-main` | Default link colour |
| `text-link-primary` | `--text-color-link-primary` | Brand-coloured link |
| `text-link-inverse` | `--text-color-link-inverse` | Link on dark backgrounds |
| `text-link-disabled` | `--text-color-link-disabled` | Disabled link |

---

## Background colors

### Surface tiers — **this is how OMR expresses elevation, not shadows**

| Utility | Variable | Usage |
|---|---|---|
| `bg-surface` | `--background-color-surface` | Page base — the canvas |
| `bg-solid` | `--background-color-solid` | Pure white (e.g. cards on tinted pages) |
| `bg-surface-elevation-1` | `--background-color-surface-elevation-1` | +1 depth (lightest grey above page) |
| `bg-surface-elevation-2` | `--background-color-surface-elevation-2` | +2 depth |
| `bg-surface-elevation-3` | `--background-color-surface-elevation-3` | +3 depth |
| `bg-surface-elevation-4` | `--background-color-surface-elevation-4` | +4 depth |
| `bg-surface-elevation-5` | `--background-color-surface-elevation-5` | +5 depth (darkest grey, rare) |
| `bg-surface-inverse` | `--background-color-surface-inverse` | Dark surface (use with `text-inverse`) |

### Alpha surface tiers (for overlays on imagery)

| Utility | Variable | Usage |
|---|---|---|
| `bg-surface-alpha-elevation-1` | `--background-color-surface-alpha-elevation-1` | Transparent +1 depth — content shows through |
| `bg-surface-alpha-elevation-2` | `--background-color-surface-alpha-elevation-2` | Transparent +2 depth |
| `bg-surface-alpha-elevation-3` | `--background-color-surface-alpha-elevation-3` | Transparent +3 depth |
| `bg-surface-alpha-elevation-4` | `--background-color-surface-alpha-elevation-4` | Transparent +4 depth |
| `bg-surface-alpha-elevation-5` | `--background-color-surface-alpha-elevation-5` | Transparent +5 depth |

### Primary fills (brand purple)

| Utility | Variable | Usage |
|---|---|---|
| `bg-primary-main` | `--background-color-primary-main` | Brand purple fill — primary buttons, brand emphasis |
| `bg-primary-strong` | `--background-color-primary-strong` | Darker brand purple — hover on primary |
| `bg-primary-stronger` | `--background-color-primary-stronger` | Even darker — pressed state |
| `bg-primary-strongest` | `--background-color-primary-strongest` | Darkest brand purple |
| `bg-primary-subtle` | `--background-color-primary-subtle` | Pale purple fill — selected items, brand banners |
| `bg-primary-subtler` | `--background-color-primary-subtler` | Lighter pale purple |
| `bg-primary-subtlest` | `--background-color-primary-subtlest` | Lightest pale purple — backgrounds, hovers |

### Primary alpha fills (transparent primary for overlays on imagery)

| Utility | Variable | Usage |
|---|---|---|
| `bg-primary-alpha-strong` | `--background-color-primary-alpha-strong` | Transparent dark brand purple overlay |
| `bg-primary-alpha-stronger` | `--background-color-primary-alpha-stronger` | Transparent darker brand purple overlay |
| `bg-primary-alpha-strongest` | `--background-color-primary-alpha-strongest` | Transparent darkest brand purple overlay |
| `bg-primary-alpha-subtle` | `--background-color-primary-alpha-subtle` | Transparent pale purple overlay |
| `bg-primary-alpha-subtler` | `--background-color-primary-alpha-subtler` | Transparent lighter pale purple overlay |
| `bg-primary-alpha-subtlest` | `--background-color-primary-alpha-subtlest` | Transparent lightest pale purple overlay |

> Use primary alpha fills when layering brand colour on top of imagery or
> content that should remain visible. Analogous to the alpha surface tiers.

### Secondary fills (brand yellow)

| Utility | Variable | Usage |
|---|---|---|
| `bg-secondary-main` | `--background-color-secondary-main` | Secondary yellow fill — accent elements |
| `bg-secondary-strong` | `--background-color-secondary-strong` | Darker secondary — hover on secondary |
| `bg-secondary-stronger` | `--background-color-secondary-stronger` | Even darker secondary |
| `bg-secondary-strongest` | `--background-color-secondary-strongest` | Darkest secondary |
| `bg-secondary-subtle` | `--background-color-secondary-subtle` | Pale yellow fill |
| `bg-secondary-subtler` | `--background-color-secondary-subtler` | Lighter pale yellow |
| `bg-secondary-subtlest` | `--background-color-secondary-subtlest` | Lightest pale yellow — backgrounds |

### Status fills

| Utility | Variable | Usage |
|---|---|---|
| `bg-error-strong` | `--background-color-error-strong` | Solid error fill — high-emphasis indicators |
| `bg-error-subtle` | `--background-color-error-subtle` | Pale error tint — banners, badges |
| `bg-success-strong` | `--background-color-success-strong` | Solid success fill |
| `bg-success-subtle` | `--background-color-success-subtle` | Pale success tint |
| `bg-warning-strong` | `--background-color-warning-strong` | Solid warning fill |
| `bg-warning-subtle` | `--background-color-warning-subtle` | Pale warning tint |
| `bg-disabled` | `--background-color-disabled` | Disabled element fill |

### Badge fills

| Utility | Variable | Usage |
|---|---|---|
| `bg-badge-filled-success` | `--background-color-badge-filled-success` | Filled success badge background |
| `bg-badge-filled-warning` | `--background-color-badge-filled-warning` | Filled warning badge background |
| `bg-badge-filled-error` | `--background-color-badge-filled-error` | Filled error badge background |

> Pair badge backgrounds with matching badge text tokens: `bg-badge-filled-success` + `text-badge-filled-success`.

### Component-specific background tokens (reference only)

These tokens are designed for specific components. Full documentation will live in
the respective component files. Do not use them in general UI — use the semantic
tokens above instead.

| Component | Tokens (Tailwind `bg-*`) |
|---|---|
| **Button** | `button-outline`, `button-outline-color`, `button-outline-destructive`, `button-outline-success`, `button-primary-color`, `button-primary-destructive`, `button-primary-neutral`, `button-primary-success`, `button-secondary-color`, `button-secondary-destructive`, `button-secondary-neutral`, `button-secondary-success` |
| **Timetable** | `timetable-event-active`, `timetable-event-inactive`, `timetable-event-passed`, `timetable-meeting-active`, `timetable-meeting-inactive`, `timetable-meeting-passed` |
| **UI chrome** | `scrollbar-handle`, `toggle-inactive` |

### Backdrop / overlay

| Utility | Variable | Usage |
|---|---|---|
| `bg-effect-backdrop-overlay` | `--background-color-effect-backdrop-overlay` | Modal backdrop — pair with `backdrop-blur-xs` |
| `bg-effect-focused` | `--background-color-effect-focused` | Focus ring background (rare — see Effect colors) |

---

## Border colors

| Utility | Variable | Usage |
|---|---|---|
| `border-main` | `--border-color-main` | Default border — most cards, inputs, dividers |
| `border-main-solid` | `--border-color-main-solid` | Solid (no alpha) variant for crisp edges |
| `border-subtle` | `--border-color-subtle` | De-emphasised dividers |
| `border-strong` | `--border-color-strong` | Strong emphasis — modal headers, sticky bars |
| `border-primary` | `--border-color-primary` | Brand purple border |
| `border-primary-solid` | `--border-color-primary-solid` | Solid brand border |
| `border-primary-subtle` | `--border-color-primary-subtle` | Subtle brand purple border |
| `border-primary-subtle-solid` | `--border-color-primary-subtle-solid` | Solid subtle brand border |
| `border-secondary` | `--border-color-secondary` | Secondary yellow border |
| `border-secondary-subtle` | `--border-color-secondary-subtle` | Subtle secondary border |
| `border-error` | `--border-color-error` | Error state — invalid inputs |
| `border-error-subtle` | `--border-color-error-subtle` | Subtle error border — banners |
| `border-success` | `--border-color-success` | Success state |
| `border-success-subtle` | `--border-color-success-subtle` | Subtle success border |
| `border-warning` | `--border-color-warning` | Warning state |
| `border-warning-subtle` | `--border-color-warning-subtle` | Subtle warning border |
| `border-selected` | `--border-color-selected` | Selection indicator (chips, radio, options) |
| `border-disabled` | `--border-color-disabled` | Disabled state |
| `border-inverse` | `--border-color-inverse` | Border on dark backgrounds |

---

## Effect colors

Focus rings and backdrop overlays.

| Utility | Variable | Usage |
|---|---|---|
| `text-effect-focused` | `--text-color-effect-focused` | Focus ring outline colour (2 px solid) |
| `text-effect-backdrop-overlay` | `--text-color-effect-backdrop-overlay` | Text overlay on backdrop |
| `text-effect-overlay-surface-solid` | `--text-color-effect-overlay-surface-solid` | Text on solid overlay surface |
| `text-effect-overlay-surface-strongest` | `--text-color-effect-overlay-surface-strongest` | Text on strongest overlay surface |
| `text-effect-overlay-surface-subtlest` | `--text-color-effect-overlay-surface-subtlest` | Text on subtlest overlay surface |
| `text-effect-overlay-surface-transparent` | `--text-color-effect-overlay-surface-transparent` | Text on transparent overlay surface |
| `bg-effect-focused` | `--background-color-effect-focused` | Focus ring background |
| `bg-effect-backdrop-overlay` | `--background-color-effect-backdrop-overlay` | Modal backdrop overlay |
| `bg-effect-overlay-surface-solid` | `--background-color-effect-overlay-surface-solid` | Solid overlay surface background |
| `bg-effect-overlay-surface-strongest` | `--background-color-effect-overlay-surface-strongest` | Strongest overlay surface background |
| `bg-effect-overlay-surface-subtlest` | `--background-color-effect-overlay-surface-subtlest` | Subtlest overlay surface background |
| `bg-effect-overlay-surface-transparent` | `--background-color-effect-overlay-surface-transparent` | Transparent overlay surface background |

> Apply focus via `omr-focus-visible-outline` (open layouts) or `omr-focus-visible-inset`
> (clipped containers with `overflow-hidden`). The `blur-overlay-style` utility
> combines `bg-effect-backdrop-overlay` + `backdrop-blur-xs` for modal backdrops.
> Overlay surface tokens provide layered surface backgrounds with matching text tokens
> at different opacity levels.

---

## Graphic colors

Dedicated colours for illustrations, charts, data visualisations, and decorative
graphics. These use the `graphic-*` Tailwind prefix and `--graphic-color-*` CSS
variables — a separate namespace from text/bg/border tokens.

### Core

| Utility | Variable | Usage |
|---|---|---|
| `graphic-black` | `--graphic-color-black` | Black graphic element |
| `graphic-white` | `--graphic-color-white` | White graphic element |
| `graphic-disabled` | `--graphic-color-disabled` | Disabled/inactive graphic element |

### Status

| Utility | Variable | Usage |
|---|---|---|
| `graphic-error` | `--graphic-color-error` | Error indicator in graphics |
| `graphic-success` | `--graphic-color-success` | Success indicator in graphics |
| `graphic-warning` | `--graphic-color-warning` | Warning indicator in graphics |

### Grey scale

| Utility | Variable | Usage |
|---|---|---|
| `graphic-grey-subtle` | `--graphic-color-grey-subtle` | Light grey — background fills, grid lines |
| `graphic-grey-medium` | `--graphic-color-grey-medium` | Medium grey — secondary data series |
| `graphic-grey-strong` | `--graphic-color-grey-strong` | Dark grey — labels, axes |

### Primary scale (purple)

| Utility | Variable | Usage |
|---|---|---|
| `graphic-primary-subtle` | `--graphic-color-primary-subtle` | Light purple — area fills, backgrounds |
| `graphic-primary-medium` | `--graphic-color-primary-medium` | Medium purple — secondary series |
| `graphic-primary-strong` | `--graphic-color-primary-strong` | Dark purple — primary data series, key metrics |

### Secondary scale (yellow)

| Utility | Variable | Usage |
|---|---|---|
| `graphic-secondary-subtle` | `--graphic-color-secondary-subtle` | Light yellow — area fills |
| `graphic-secondary-medium` | `--graphic-color-secondary-medium` | Medium yellow — secondary accent |
| `graphic-secondary-strong` | `--graphic-color-secondary-strong` | Dark yellow — accent data series |

### Tertiary scale

| Utility | Variable | Usage |
|---|---|---|
| `graphic-tertiary-subtle` | `--graphic-color-tertiary-subtle` | Light tertiary — area fills |
| `graphic-tertiary-medium` | `--graphic-color-tertiary-medium` | Medium tertiary — third data series |
| `graphic-tertiary-strong` | `--graphic-color-tertiary-strong` | Dark tertiary — tertiary data series |

> Use graphic colours only for illustrations and data visualisations — not for
> UI surfaces, text, or borders. For UI elements, use the semantic text/bg/border tokens.

---

## Interaction state layers

State layers are **semi-transparent overlays** added on hover, press, drag.
Don't reach for individual `bg-*` tokens to fake hover — use the state-layer system.

### State-layer composite utilities

| Utility | Hover | Press | Drag | Use on |
|---|---|---|---|---|
| `state-layer-neutral` | `bg-state-hover-neutral` | `bg-state-pressed-neutral` | `bg-state-drag-neutral` | Neutral interactive surfaces (cards, list items) |
| `state-layer-primary` | `bg-state-hover-primary` | `bg-state-pressed-primary` | `bg-state-drag-primary` | Brand-coloured interactive elements |
| `state-layer-neutral-inverse` | `bg-state-hover-neutral-inverse` | `bg-state-pressed-neutral-inverse` | `bg-state-drag-neutral-inverse` | Dark-themed surfaces |

> Use the `state-layer-*` utilities on the interactive element directly —
> they handle `::before` pseudo-element, z-index, opacity transition, and
> `:hover` / `:active` / `[data-drag="true"]` states automatically.

### Raw state tokens (for custom implementations only)

| Utility | Variable | Triggered by |
|---|---|---|
| `bg-state-hover-neutral` | `--background-color-state-hover-neutral` | Hover on neutral surface |
| `bg-state-pressed-neutral` | `--background-color-state-pressed-neutral` | Press on neutral surface |
| `bg-state-drag-neutral` | `--background-color-state-drag-neutral` | Drag on neutral surface |
| `bg-state-hover-neutral-inverse` | `--background-color-state-hover-neutral-inverse` | Hover on dark surface |
| `bg-state-pressed-neutral-inverse` | `--background-color-state-pressed-neutral-inverse` | Press on dark surface |
| `bg-state-drag-neutral-inverse` | `--background-color-state-drag-neutral-inverse` | Drag on dark surface |
| `bg-state-hover-primary` | `--background-color-state-hover-primary` | Hover on brand surface |
| `bg-state-pressed-primary` | `--background-color-state-pressed-primary` | Press on brand surface |
| `bg-state-drag-primary` | `--background-color-state-drag-primary` | Drag on brand surface |

---

## Decision rules ("Spielregeln")

### Choosing text colour
- **Default to `text-main`** for body text. Don't use `text-primary` "for emphasis"
  unless the content is brand-related. (How to express emphasis -> see [`concepts/visual-hierarchy.md`](../concepts/visual-hierarchy.md))
- **Use `text-subtle`** for metadata, captions, helper text — anything secondary.
- **Use `text-subtlest`** for placeholders and hint text.
- **Use `text-primary`** *only* for: brand mentions, links inside brand contexts, focused/selected indicators.
- **Use status text colours (`text-error`, `text-success`, `text-warning`)**
  only when the content carries that status meaning. Don't use red text for "important".
- **Use `*-inverse` variants** only on dark/inverse surfaces — never on light backgrounds.

### Choosing background / surface
- **`bg-surface`** is the page. Don't repeat it inside a card.
- **`bg-solid`** for cards on top of `bg-surface` when you want stark white.
- **`bg-surface-elevation-1` and up** when you need visual depth (panels, inset areas, hover states on flat surfaces).
- **Don't stack more than 3 elevation tiers** on screen at once — visual hierarchy collapses.
- **`bg-primary-main`** is reserved for primary call-to-action buttons and brand emphasis. Don't use as page background.
- **`bg-secondary-main`** is the secondary brand color (yellow). Use for accent elements, secondary CTAs, or highlights that complement the primary purple.
- **Subtle status fills (`bg-error-subtle` etc.)** for banners and badges.
  Solid status fills (`bg-error-strong`) only for high-emphasis indicators (notification dots, severity banners).
- **Badge fills** (`bg-badge-filled-*`) pair with matching badge text tokens — always use both together.

### Choosing border
- **Default to `border-main`** for most divisions.
- **`border-subtle`** when the divider is contextual (e.g. inside a card already differentiated by background).
- **`border-strong`** sparingly — typically only on sticky elements that need to "pop" against scrolling content.
- **`border-primary` or `border-selected`** to indicate selection / focus / brand state — never both at the same time.
- **`border-secondary`** for secondary brand-coloured borders (yellow accent).
- **Status borders** (`border-error`, `border-success`, `border-warning`) match the status of the input/element.
- **`*-subtle` status borders** (`border-error-subtle`, etc.) for lower-emphasis status indicators like banners.

### Mixing colours
- **One brand emphasis per view.** If you have a primary button, don't also have brand-purple text headers.
- **One status colour per element.** A success banner uses success bg + success border + success text — not mixed.
- **Backgrounds and borders should match in tier** — `bg-error-subtle` pairs with `border-error-subtle` or `border-error`, not `border-main`.

---

## Anti-patterns

- ❌ `class="bg-purple-700"` — primitive token. **Use** `bg-primary-main`.
- ❌ `style="color: #060708"` — raw hex. **Use** `text-main`.
- ❌ `class="bg-[#fdfdfd]"` — arbitrary value. **Use** `bg-surface`.
- ❌ Using `text-primary` for emphasis on non-brand content. **Use** typography weight instead (see [`concepts/visual-hierarchy.md`](../concepts/visual-hierarchy.md)).
- ❌ Stacking `bg-surface-elevation-3` on `bg-surface-elevation-2` on `bg-surface-elevation-1` on the same screen — collapses depth perception. **Limit to 2-3 visible tiers.**
- ❌ Manual hover via `hover:bg-grey-100`. **Use** the `state-layer-*` system.
- ❌ Using `bg-error-main` — this token does not exist. **Use** `bg-error-strong` for solid error fills.
- ❌ Editing `lightTheme.generated.css` or `darkTheme.generated.css` — these are auto-generated. **Update tokens in Figma**, then run `pnpm extract`.
- ❌ Inventing a new semantic token in code (e.g. `--text-color-warning-bold`). **Pipe the token through Figma -> variables.json first.**
- ❌ Mixing primary and secondary brand colours on the same element — pick one.

---

## Tailwind config reference

OMR uses **Tailwind v4** with CSS-first configuration. Tokens flow through this pipeline:

```
Figma -> variables.json -> pnpm extract -> primitiveColors.generated.css   (@theme — raw palette)
                                         -> colorTheme.generated.css       (@theme — registers semantic vars)
                                         -> lightTheme.generated.css       (@utility light-theme — light values)
                                         -> darkTheme.generated.css        (@utility dark-theme — dark values)
                                                    |
                                       Tailwind v4 resolves utilities
                                                    |
                                       text-main, bg-surface, border-primary ...
```

### How it works

1. **`primitiveColors.generated.css`** — `@theme` block defines `--color-*` primitives (the raw palette).
2. **`colorTheme.generated.css`** — `@theme` block registers all semantic variables as `unset`, telling Tailwind v4 they exist. Tailwind derives utility names from CSS variable namespaces:
   - `--text-color-{name}` -> `text-{name}`
   - `--background-color-{name}` -> `bg-{name}`
   - `--border-color-{name}` -> `border-{name}`
3. **`lightTheme.generated.css`** / **`darkTheme.generated.css`** — `@utility` blocks that assign actual colour values per theme.
4. **`theme.css`** — declares `@custom-variant dark` and `@custom-variant light`, color aliases, typography, and breakpoints.

---

## Dark theme

Dark theme is **automatic**. To enable it for a subtree, wrap a parent element:

```html
<div class="dark-theme">
  <!-- everything inside resolves dark-theme variants -->
  <p class="text-main bg-surface">...</p>
</div>
```

Every semantic token is overridden by `darkTheme.generated.css` — components don't
need any conditional classes. **Do not** write `dark:bg-...` overrides in components.

The implementation uses Tailwind v4 custom variants:
- `@custom-variant dark` — targets `.dark *` descendants
- `@custom-variant light` — targets `.light` descendants
- `@utility dark-theme { ... }` — sets all dark values
- `@utility light-theme { ... }` — sets all light values (active by default on body)

---

## Examples

### Do — primary CTA on a card

```html
<div class="bg-solid border border-main rounded-m p-6">
  <h3 class="txt-headline-m-bold text-main">Upgrade your plan</h3>
  <p class="txt-body-m-regular text-subtle mt-2">More reviews, more insights.</p>
  <button class="bg-primary-main text-inverse rounded px-4 py-2 mt-4 state-layer-primary">
    Upgrade
  </button>
</div>
```

### Do — error state on an input

```html
<input class="bg-solid border border-error rounded text-main px-3 py-2" />
<p class="txt-body-s-regular text-error mt-1">Email is required.</p>
```

### Do — success banner

```html
<div class="bg-success-subtle border border-success-subtle rounded-m p-4 flex items-center gap-3">
  <span class="text-icon-success"><!-- icon --></span>
  <p class="txt-body-s-regular text-success">Changes saved successfully.</p>
</div>
```

### Do — filled badge

```html
<span class="bg-badge-filled-warning text-badge-filled-warning txt-label-s rounded-full px-2 py-0.5">
  Pending
</span>
```

### Do — interactive card with state layer

```html
<div class="bg-solid border border-main rounded-m p-4 cursor-pointer state-layer-neutral">
  <p class="txt-body-m-regular text-main">Click me</p>
</div>
```

### Don't — primitive tokens + raw values

```html
<div class="bg-[#fdfdfd] border border-grey-200 rounded-[8px] p-6">
  <h3 class="text-[#060708] font-bold text-[18px]">...</h3>
  <button class="bg-purple-700 text-white rounded px-4 py-2">Upgrade</button>
</div>
```
**Why wrong:** arbitrary hex/values bypass the token system, primitive tokens
break theming, raw `font-*` bypasses the typography system.

### Don't — fake hover with primitive

```html
<div class="bg-surface hover:bg-grey-100 rounded-m p-4 cursor-pointer">...</div>
```
**Why wrong:** `grey-100` is primitive. **Use** the state layer:
```html
<div class="bg-surface state-layer-neutral rounded-m p-4 cursor-pointer">...</div>
```

### Don't — wrong status fill token name

```html
<div class="bg-error-main p-4">...</div>
```
**Why wrong:** `bg-error-main` does not exist. **Use** `bg-error-strong` for solid error fill.

---

## Cross-references

- [`elevation.md`](./elevation.md) (todo) — surface tiers + z-index combined
- [`typography.md`](./typography.md) (todo) — text-color always pairs with `txt-*`
- [`../concepts/visual-hierarchy.md`](../concepts/visual-hierarchy.md) (todo) — emphasis via typography weight vs. colour
- [`../concepts/button-hierarchy.md`](../concepts/button-hierarchy.md) (todo) — colour usage per button variant
- [`../concepts/interactive-states.md`](../concepts/interactive-states.md) (todo) — full state-layer pattern
- [`../CLAUDE.md`](../CLAUDE.md) — agent rules
