---
name: bfbe-delivery-estimate
description: "Use when placing, wiring or styling BFB Delivery Estimate (`bfbe-delivery-estimate`). Read before writing its settings."
---

# BFB Delivery Estimate (`bfbe-delivery-estimate`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-delivery-estimate.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/delivery-estimate/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 0.78 KB, JS 1.71 KB (gzipped), plus shop-live, loaded only on pages that use it.

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Estimate (`bfbeEstimate`)
- `show` (select) **Show**: options: `both` Estimate and postcode check (default), `estimate` Estimate only, `check` Postcode check only, `pickup` Pickup hours only
- `withinText` (text) **Before the cut-off**: placeholder Order within {time} for delivery {date}; only when `show` is not `check` or `pickup`. {time}, {date}, {from} and {to} are filled in.
- `afterText` (text) **After the cut-off**: placeholder Delivery {date}; only when `show` is not `check` or `pickup`
- `noneText` (text) **Without an estimate**: placeholder Nothing is shown; dynamic data accepted; only when `show` is not `check` or `pickup`. When no transit rule covers the visitor.

### Postcode check (`bfbeCheck`)
The whole group shows only when `show` is not `estimate` or `pickup`.
- `checkTitle` (text) **Title**: placeholder Delivery to your address; dynamic data accepted; only when `show` is not `estimate` or `pickup`
- `checkFor` (select) **Check for**: options: `auto` This product, else the cart (default), `cart` The cart; only when `show` is not `estimate` or `pickup`
- `countryLabel` (text) **Country label**: placeholder Country; only when `show` is not `estimate` or `pickup`
- `postcodeLabel` (text) **Postcode label**: placeholder Postcode; only when `show` is not `estimate` or `pickup`
- `buttonText` (text) **Button text**: placeholder Check; only when `show` is not `estimate` or `pickup`
- `fieldsDirection` (select) **Direction**: options: `row` Across (default), `column` Down; only when `show` is not `estimate` or `pickup`
Styling, in the schema file: `checkTitleTypography`, `fieldLabelTypography`, `fieldsGap`, `fieldTypography`, `fieldBackground`, `fieldBorder`, `fieldPadding`, `fieldFocusBorder`, `buttonTypography`, `buttonBackground`, `buttonColor`, `buttonBorder`, `buttonPadding`, `buttonHoverBackground`, `buttonHoverColor`, `rateGap`, `ratePadding`, `rateNameTypography`, `rateCostTypography`, `rateWhenTypography`, `rateLineColor`, `noneTypography`, `errorTypography`.

### Pickup (`bfbePickup`)
- `pickup` (select) **Pickup hours**: options: `hours` From a BFB Business Hours element, `words` In words. Shown while Local pickup is offered to the visitor.
- `pickupFrom` (select) **Business Hours in**: placeholder This page; only when `pickup` is `hours`
- `pickupWords` (textarea) **Pickup hours in words**: placeholder Monday to Friday, 9:00 to 17:00; dynamic data accepted; only when `pickup` is `words`
- `pickupTitle` (text) **Pickup title**: placeholder Pickup hours; dynamic data accepted; only when `pickup` is set

### Look (`bfbeLook`)
- `lines` (checkbox) **Lines between parts**
Styling, in the schema file: `gap`, `lineColor`, `lineWidth`, `estimateTypography`, `timeTypography`, `dateTypography`, `pickupTitleTypography`, `pickupDaysTypography`, `pickupHoursTypography`, `pickupWordsTypography`.

### Country list (`bfbeCountryList`)
The whole group shows only when `show` is not `estimate` or `pickup`.
- `countryListLook` (select) **Open list**: options: `native` As the browser draws it (default), `custom` Styled with the controls below. Phones keep their own list either way.
Styling, in the schema file: `countryListChevron`, `countryListPanelBg`, `countryListPanelBorder`, `countryListPanelShadow`, `countryListPanelPadding`, `countryListOptTypography`, `countryListOptPadding`, `countryListOptHover`, `countryListHoverText`, `countryListOptOnBg`, `countryListOptOnColor`, `countryListTick`.
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
