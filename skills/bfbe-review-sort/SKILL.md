---
name: bfbe-review-sort
description: "Use when placing, wiring or styling BFB Review Sort (`bfbe-review-sort`). Read before writing its settings."
---

# BFB Review Sort (`bfbe-review-sort`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-review-sort.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/review-sort/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Sort (`bfbeSort`)
- `as` (select) **Show as**: options: `select` A dropdown (default), `radios` Radio buttons
- `label` (text) **Label**: placeholder Sort reviews; dynamic data accepted
Styling, in the schema file: `labelTypography`, `gap`.

### Dropdown (`bfbeDropdown`)
The whole group shows only when `as` is not `radios`.
- `look` (select) **Open list**: options: `native` As the browser draws it (default), `custom` Styled with the controls below. Phones keep their own list either way.
Styling, in the schema file: `ddTypography`, `ddBackground`, `ddBorder`, `ddPadding`, `ddChevron`, `ddPanelBg`, `ddPanelBorder`, `ddPanelShadow`, `ddPanelPadding`, `ddOptTypography`, `ddOptPadding`, `ddOptHover`, `ddHoverText`, `ddOptOnBg`, `ddOptOnColor`, `ddTick`.

### Radio buttons (`bfbeChoices`)
The whole group shows only when `as` is `radios`.
Styling only, every key in the schema file: `chipTypography`, `chipBackground`, `chipBorder`, `chipPadding`, `chipHover`, `chipOnBackground`, `chipOnColor`, `chipOnBorder`.
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
