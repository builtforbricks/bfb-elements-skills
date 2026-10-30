---
name: bfbe-shop-cart-page
description: "Use for the shop's settings on Bricks' Cart items, Cart totals (collaterals) and Cart coupon: the cart table and fields look, coupons anywhere, save for later on the lines, and the live cart switch on Containers that redraws a cart of your own layout (BFB Shop cart page, `shop-cart-page`). Read before writing these settings."
---

# BFB Shop cart page (`shop-cart-page`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 2.0.0 or later, and BFB Elements Pro 2.0.0 or later for the groups marked Pro, WooCommerce active, the feature switches on (WordPress menu BFB Elements, Elements): `shop-live-cart`, `shop-coupons`, `shop-cart-lines`. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/shop-cart-page.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/shop-cart-page/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

## Where it lives
A feature, not an element: its groups are added to Bricks' own elements, on the Content tab after Bricks' own groups. By element:
- Block, Container and Div (`block`, `container`, `div`): BFB Live cart (`bfbeLiveCart`).
- Cart totals (`woocommerce-cart-collaterals`): BFB Table (`bfbeShopTable`), BFB Form fields (`bfbeShopFields`).
- Cart coupon (`woocommerce-cart-coupon`): BFB Coupons (`bfbeShopCoupons`).
- Cart items (`woocommerce-cart-items`): BFB Table (`bfbeShopTable`), BFB Cart lines (`bfbeShopCartLines`).

## Settings that decide the build

### Block, Container and Div (`block`, `container`, `div`)

#### BFB Live cart (`bfbeLiveCart`)
Pro, switch `shop-live-cart`.
- `bfbeLiveCart` (checkbox) **Redraw when the cart changes**. Drawn again on the server after every cart change.

### Cart totals (`woocommerce-cart-collaterals`)

#### BFB Table (`bfbeShopTable`)
Free.
Styling only, every key in the schema file: `bfbeShopTableTitleMargin`, `bfbeShopTableAlign`, `bfbeShopTableLine`, `bfbeShopTableTotalTypography`, `bfbeShopTableStack`, `bfbeShopTableStackPadding`, `bfbeShopTableLabelTypography`.

#### BFB Form fields (`bfbeShopFields`)
Free.
Styling only, every key in the schema file: `bfbeShopFieldsRowGap`, `bfbeShopFieldsRowSpacing`, `bfbeShopFieldsSelectBorder`, `bfbeShopFieldsSelectHeight`, `bfbeShopFieldsSelectPadding`.

### Cart coupon (`woocommerce-cart-coupon`)

#### BFB Coupons (`bfbeShopCoupons`)
Pro, switch `shop-coupons`.
- `bfbeShopCouponsAnywhere` (select) **Works anywhere**: options: `on` On (default), `off` Off
Styling, in the schema file: `bfbeShopCouponsNoticeTypography`, `bfbeShopCouponsErrorColor`.

### Cart items (`woocommerce-cart-items`)

#### BFB Table (`bfbeShopTable`)
Free.
- `bfbeShopTableQtyButtons` (select) **Quantity buttons**: options: `bricks` Bricks' − and +, `browser` The browser's arrows, `none` None
Styling, in the schema file: `bfbeShopTableBorder`, `bfbeShopTableCellPadding`, `bfbeShopTableAlign`, `bfbeShopTableLine`, `bfbeShopTableLinkTypography`, `bfbeShopTableImageBorder`, `bfbeShopTableImageBackground`, `bfbeShopTableRemoveSize`, `bfbeShopTableRemoveBackground`, `bfbeShopTableRemoveBorder`, `bfbeShopTableQtyWidth`, `bfbeShopTableQtyAlign`, `bfbeShopTableQtyBorder`, `bfbeShopTableQtyBoxWidth`, `bfbeShopTableQtyHeight`, `bfbeShopTableQtyBoxPadding`, `bfbeShopTableQtyBoxBorder`, `bfbeShopTableQtyBtnWidth`, `bfbeShopTableQtyBtnColor`, `bfbeShopTableQtyBtnBg`, `bfbeShopTableQtyBtnBorder`, `bfbeShopTableQtyBtnHover`, `bfbeShopTableActionsAlign`, `bfbeShopTableStack`, `bfbeShopTableStackPadding`, `bfbeShopTableLabelTypography`.

#### BFB Cart lines (`bfbeShopCartLines`)
Pro, switch `shop-cart-lines`.
- `bfbeShopCartLinesSave` (select) **Save for later**: options: `on` On (default), `off` Off. A button on each line.
- `bfbeShopCartLinesSaveText` (text) **Label**: placeholder Save for later; only when `bfbeShopCartLinesSave` is not `off`
Styling, in the schema file: `bfbeShopCartLinesSaveTypography`, `bfbeShopCartLinesSaveBackground`, `bfbeShopCartLinesSaveBorder`, `bfbeShopCartLinesSavePadding`, `bfbeShopCartLinesSaveHover`.
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
