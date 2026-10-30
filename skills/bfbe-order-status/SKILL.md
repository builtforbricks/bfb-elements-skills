---
name: bfbe-order-status
description: "Use when placing, wiring or styling BFB Order Status (`bfbe-order-status`). Read before writing its settings."
---

# BFB Order Status (`bfbe-order-status`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-order-status.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/order-status/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 1.07 KB, JS none (gzipped), no dependencies, loaded only on pages that use it.

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Lookup form (`bfbeForm`)
- `shows` (select) **Show**: options: `both` Form and answer (default), `form` Form only, `answer` Answer only. Place the answer elsewhere with a second element.
- `intro` (textarea) **Intro**: dynamic data accepted; only when `shows` is not `answer`
- `numberLabel` (text) **Order number label**: placeholder Order number; only when `shows` is not `answer`
- `emailLabel` (text) **Email label**: placeholder Email address used for the order; only when `shows` is not `answer`
- `buttonText` (text) **Button**: placeholder Check my order; only when `shows` is not `answer`
- `buttonStyle` (select) **Style**: options: `primary` Primary (default), `secondary` Secondary, `light` Light, `dark` Dark, `muted` Muted, `info` Info, `success` Success, `warning` Warning, `danger` Danger; only when `shows` is not `answer`
Styling, in the schema file: `formGap`, `introTypography`, `labelTypography`, `fieldTypography`, `fieldBackground`, `fieldBorder`, `fieldPadding`, `focusBorderColor`, `buttonTypography`, `buttonBackground`, `buttonBorder`, `buttonPadding`, `buttonHoverBackground`, `buttonHoverColor`, `buttonHoverBorder`, `refusedBorder`, `errorTypography`.

### Timeline (`bfbeTimeline`)
The whole group shows only when `shows` is not `form`.
- `showHistory` (select) **History**: options: `show` Show (default), `hide` Hide
- `showItems` (select) **Items**: options: `show` Show (default), `hide` Hide
- `showTracking` (select) **Tracking numbers**: options: `show` Show (default), `hide` Hide
- `stepDirection` (select) **Direction**: options: `row` Across (default), `column` Down
Styling, in the schema file: `stepTypography`, `stepColor`, `stepDoneColor`, `stepCurrentColor`, `stepSize`, `stepLineColor`, `stepLineWidth`.

### Answer (`bfbeAnswer`)
The whole group shows only when `shows` is not `form`.
- `titleText` (text) **Title**: placeholder Order #{number}. {number} is filled in.
- `titleTag` (select) **Title tag**: options: `h2` H2, `h3` H3 (default), `h4` H4, `h5` H5, `h6` H6, `p` p
- `placedLabel` (text) **Date label**: placeholder Placed
- `statusLabel` (text) **Status label**: placeholder Status
- `shippingLabel` (text) **Shipping label**: placeholder Shipping
- `trackingLabel` (text) **Tracking label**: placeholder Tracking; only when `showTracking` is not `hide`
- `historyHeading` (text) **History heading**: placeholder History; only when `showHistory` is not `hide`
- `itemsHeading` (text) **Items heading**: placeholder Items; only when `showItems` is not `hide`
- `headingTag` (select) **Heading tag**: options: `h2` H2, `h3` H3, `h4` H4 (default), `h5` H5, `h6` H6, `p` p
Styling, in the schema file: `boxBackground`, `boxBorder`, `boxShadow`, `boxPadding`, `answerTitleTypography`, `headingTypography`, `historyTypography`, `factLabelTypography`, `factValueTypography`, `dateColor`, `trackingColor`, `trackingHoverColor`, `itemNameTypography`, `itemQtyTypography`, `itemDividerColor`, `itemDividerWidth`.
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
