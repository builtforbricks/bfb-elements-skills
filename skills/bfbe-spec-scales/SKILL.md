---
name: bfbe-spec-scales
description: "Use when placing, wiring or styling BFB Spec Scales (`bfbe-spec-scales`). Read before writing its settings."
---

# BFB Spec Scales (`bfbe-spec-scales`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-spec-scales.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/spec-scales/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 0.46 KB, JS none (gzipped), no dependencies, loaded only on pages that use it.

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Scales (`bfbeScales`)
- `scales` (repeater) **Scales**: placeholder Scale

### Look (`bfbeLook`)
- `layout` (select) **Layout**: options: `rows` Name, scale and figure in a row (default), `stacked` Name above the scale
Styling, in the schema file: `nameWidth`, `gap`, `columnGap`, `rowBackground`, `rowBorder`, `rowPadding`, `height`, `fill`, `track`, `border`, `nameTypography`, `figureTypography`.
<!-- bfbe:generated:end -->

## Rendered DOM

_Not written yet._

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
