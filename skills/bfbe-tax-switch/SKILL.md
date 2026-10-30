---
name: bfbe-tax-switch
description: "Use when placing, wiring or styling BFB Tax Switch (`bfbe-tax-switch`). Read before writing its settings."
---

# BFB Tax Switch (`bfbe-tax-switch`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-tax-switch.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/tax-switch/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 0.26 KB, JS 0.62 KB (gzipped), no dependencies, loaded only on pages that use it.

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Switch (`bfbeSwitch`)
- `label` (text) **Label**: placeholder Prices; dynamic data accepted
- `labelShow` (select) **Label shown**: options: `show` Beside the buttons (default), `sr` Hidden
- `inclText` (text) **With tax**: placeholder With VAT; dynamic data accepted
- `exclText` (text) **Without tax**: placeholder Without VAT; dynamic data accepted
Styling, in the schema file: `labelTypography`, `buttonTypography`, `buttonBackground`, `buttonBorder`, `buttonShadow`, `buttonPadding`, `buttonGap`, `hoverBackground`, `hoverColor`, `pressedTypography`, `pressedBackground`, `pressedColor`, `pressedBorder`.
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
