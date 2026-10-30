---
name: bfbe-rating-summary
description: "Use when placing, wiring or styling BFB Rating Summary (`bfbe-rating-summary`). Read before writing its settings."
---

# BFB Rating Summary (`bfbe-rating-summary`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-rating-summary.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/rating-summary/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 0.67 KB, JS none (gzipped), no dependencies, loaded only on pages that use it.

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Summary (`bfbeSummary`)
- `shows` (select) **Shows**: options: `both` Summary and bars (default), `summary` Summary only, `bars` Bars only
- `text` (text) **Text**: placeholder {average} out of 5, from {count} reviews; dynamic data accepted; only when `shows` is not `bars`. {average}, {count} and {max} are filled in.
- `none` (text) **No reviews yet**: placeholder No reviews yet; dynamic data accepted; only when `shows` is not `bars`
- `stars` (checkbox) **Stars**: only when `shows` is not `bars`
Styling, in the schema file: `textTypography`, `averageTypography`, `summaryGap`, `summaryJustify`, `summaryAlign`, `starsSize`, `starsColor`, `starsEmptyColor`.

### Bars (`bfbeBars`)
The whole group shows only when `shows` is not `summary`.
- `order` (select) **Order**: options: `desc` 5 stars first (default), `asc` 1 star first
- `figure` (select) **Beside each bar**: options: `count` The count (default), `percent` The share in percent, `both` Both, `none` Nothing
- `links` (select) **Filter the reviews**: options: `yes` Yes, as links (default), `no` No
- `anchor` (text) **Review list anchor**: placeholder #reviews; only when `links` is not `no`
- `allText` (text) **Show all**: placeholder Show all reviews; dynamic data accepted; only when `links` is not `no`
Styling, in the schema file: `barHeight`, `barColor`, `trackColor`, `barBorder`, `rowGap`, `columnGap`, `labelWidth`, `barTypography`, `figuresTypography`, `rowHoverColor`, `rowHoverFill`, `rowChosenColor`, `allTypography`, `allBackground`, `allBorder`, `allPadding`, `allHoverBackground`, `allHoverColor`.
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
