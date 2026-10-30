---
name: bfbe-view-switch
description: "Use when placing, wiring or styling BFB View Switch (`bfbe-view-switch`). Read before writing its settings."
---

# BFB View Switch (`bfbe-view-switch`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-view-switch.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/view-switch/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 0.68 KB, JS 1.42 KB (gzipped), plus shop-live, loaded only on pages that use it.

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Switch (`bfbeSwitch`)
- `target` (text) **Loop element id**: placeholder The next product loop
- `layouts` (checkbox) **Grid and list buttons**
- `columns` (text) **Column choices**: placeholder 2, 3, 4. Numbers, comma separated; empty for none.
- `perPage` (text) **Per page choices**: placeholder 12, 24, 48. Numbers, comma separated; empty for none.

### Words (`bfbeWords`)
- `gridText` (text) **Grid**: placeholder Grid; only when `layouts` is set
- `listText` (text) **List**: placeholder List; only when `layouts` is set
- `columnsText` (text) **Columns**: placeholder Columns
- `perPageText` (text) **Per page**: placeholder Per page

### Look (`bfbeLook`)
Styling only, every key in the schema file: `gap`, `justify`, `groupBackground`, `groupBorder`, `groupPadding`, `groupGap`, `wordTypography`, `wordPadding`, `buttonTypography`, `buttonPadding`, `buttonBorder`, `buttonBackground`, `hoverBackground`, `hoverColor`, `onBackground`, `onColor`.
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
