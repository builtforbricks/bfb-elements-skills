---
name: bfbe-compare-button
description: "Use when placing, wiring or styling BFB Compare Button (`bfbe-compare-button`). Read before writing its settings."
---

# BFB Compare Button (`bfbe-compare-button`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-compare-button.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/compare-button/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 1.17 KB, JS 0.78 KB (gzipped), no dependencies, loaded only on pages that use it.

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Button (`bfbeButton`)
- `textAdd` (text) **Words to add**: placeholder Compare; dynamic data accepted
- `textOn` (text) **Words when added**: placeholder Comparing; dynamic data accepted
- `content` (select) **Button shows**: options: `both` Icon and words (default), `icon` Icon only, `words` Words only
- `iconAdd` (icon) **Icon to add**: only when `content` is not `words`
- `iconOn` (icon) **Icon when added**: only when `content` is not `words`

### Look (`bfbeLook`)
- `iconPlace` (select) **Icon sits**: options: `row` Before the words (default), `row-reverse` After the words; writes CSS; only when `content` is not `icon` or `words`
Styling, in the schema file: `btnType`, `btnBackground`, `btnBorder`, `btnShadow`, `btnPadding`, `hoverBackground`, `hoverColor`, `hoverBorderColor`, `iconSize`, `iconColor`, `gap`, `onBackground`, `onColorText`, `onBorderColor`, `onColor`.
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
