---
name: bfbe-product-badges
description: "Use when placing, wiring or styling BFB Product Badges (`bfbe-product-badges`). Read before writing its settings."
---

# BFB Product Badges (`bfbe-product-badges`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-product-badges.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/product-badges/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 0.38 KB, JS none (gzipped), no dependencies, loaded only on pages that use it.

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Badges (`bfbeBadges`)
- `max` (number) **Badges at most**: placeholder 2
- `rules` (select) **Rules shown**: options: `0` Sold out, `1` Back-order, `2` Pre-order: ships {date}, `3` Only a few left, `4` Save {percent}%, `5` Sale, `6` Best seller, `7` New, `8` Featured, `9` Kitchen, `10` A gift, `11` Sold per litre. Set the badges in BFB Elements > Shop > Products.
- `layout` (select) **Layout**: options: `stacked` Stacked (default), `inline` Inline
Styling, in the schema file: `alignStacked`, `alignInline`.

### Look (`bfbeLook`)
Styling only, every key in the schema file: `gap`, `badgeBackground`, `badgeColor`, `badgeTypography`, `badgePadding`, `badgeBorder`, `badgeShadow`.
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
