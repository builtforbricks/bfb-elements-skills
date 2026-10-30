---
name: bfbe-shop-add-to-cart
description: "Use for the shop's settings on Bricks' Add to cart and Products: the buy form's layout, option lists and swatches, ask for a price, quantity breaks, and swatches with add to cart on product cards (BFB Shop add to cart, `shop-add-to-cart`). Read before writing these settings."
---

# BFB Shop add to cart (`shop-add-to-cart`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 2.0.0 or later, and BFB Elements Pro 2.0.0 or later for the groups marked Pro, WooCommerce active, the feature switches on (WordPress menu BFB Elements, Elements): `shop-product-page`, `shop-buy`, `shop-cards`, `shop-quantity-breaks`. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/shop-add-to-cart.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/shop-add-to-cart/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

## Where it lives
A feature, not an element: its groups are added to Bricks' own elements, on the Content tab after Bricks' own groups. By element:
- Add to cart (`product-add-to-cart`): BFB Buying form (`bfbeShopBuyForm`), BFB Options list (`bfbeShopOptsList`), BFB Ask for a price (`bfbeShopAsk`), BFB Product cards (`bfbeShopCards`), BFB Quantity breaks (`bfbeShopQb`).
- Products (`woocommerce-products`): BFB Product cards (`bfbeShopCards`).

## Settings that decide the build

### Add to cart (`product-add-to-cart`)

#### BFB Buying form (`bfbeShopBuyForm`)
Free, switch `shop-product-page`.
- `bfbeShopQtyButtons` (select) **Quantity buttons**: options: `bricks` Bricks' − and +, `browser` The browser's arrows, `none` None
Styling, in the schema file: `bfbeShopVarStack`, `bfbeShopVarGap`, `bfbeShopVarLabelGap`, `bfbeShopVarClearTypography`, `bfbeShopSwatchFill`, `bfbeShopQtyOne`, `bfbeShopQtyHeight`, `bfbeShopQtyBorder`, `bfbeShopQtyTypography`, `bfbeShopQtyButtonWidth`, `bfbeShopQtyButtonColor`, `bfbeShopQtyButtonHover`, `bfbeShopQtyDisabled`, `bfbeShopRowStack`, `bfbeShopRowWide`, `bfbeShopRowHeight`.

#### BFB Options list (`bfbeShopOptsList`)
Free, switch `shop-product-page`.
- `bfbeShopOptsListLook` (select) **Open list**: options: `native` As the browser draws it (default), `custom` Styled with the controls below. Selects shown as Bricks' swatches keep them.
Styling, in the schema file: `bfbeShopOptsListTypography`, `bfbeShopOptsListBackground`, `bfbeShopOptsListBorder`, `bfbeShopOptsListPadding`, `bfbeShopOptsListChevron`, `bfbeShopOptsListPanelBg`, `bfbeShopOptsListPanelBorder`, `bfbeShopOptsListPanelShadow`, `bfbeShopOptsListPanelPadding`, `bfbeShopOptsListOptTypography`, `bfbeShopOptsListOptPadding`, `bfbeShopOptsListOptHover`, `bfbeShopOptsListHoverText`, `bfbeShopOptsListOptOnBg`, `bfbeShopOptsListOptOnColor`, `bfbeShopOptsListTick`.

#### BFB Ask for a price (`bfbeShopAsk`)
Pro, switch `shop-buy`.
Styling only, every key in the schema file: `bfbeShopAskWidth`.

#### BFB Product cards (`bfbeShopCards`)
Pro, switch `shop-cards`.
- `bfbeShopCardSwatches` (checkbox) **Swatches on the card**. Inside a product loop.
- `bfbeShopCardSimple` (select) **On simple products**: options: `swatch` Show its swatch (default), `none` Nothing; only when `bfbeShopCardSwatches` is set
- `bfbeShopCardSimpleAttr` (select) **Attribute**: options: `pa_colour` Colour, `pa_material` Material, `pa_size` Size, `pa_warmth` Warmth; only when `bfbeShopCardSwatches` is set and `bfbeShopCardSimple` is not `none`
- `bfbeShopCardAddText` (text) **Label**: placeholder Add to cart; only when `bfbeShopCardSwatches` is set
- `bfbeShopFirst` (checkbox) **Preselect first variation**
- `bfbeShopSoldOut` (select) **Sold-out options**: options: `hidden` Hidden, `crossed` Crossed out
Styling, in the schema file: `bfbeShopCardLegendTypography`, `bfbeShopCardSwatchBorder`, `bfbeShopCardSwatchOn`, `bfbeShopCardSwatchSize`, `bfbeShopCardLabelPadding`, `bfbeShopCardLabelBackground`, `bfbeShopCardSwatchGap`, `bfbeShopCardSwatchScroll`, `bfbeShopCardBtnTypography`, `bfbeShopCardBtnBackground`, `bfbeShopCardBtnBorder`, `bfbeShopCardBtnPadding`, `bfbeShopCardBtnWidth`, `bfbeShopCardBtnShadow`, `bfbeShopCardBtnHover`, `bfbeShopCardBtnHoverColor`.

#### BFB Quantity breaks (`bfbeShopQb`)
Pro, switch `shop-quantity-breaks`.
- `bfbeShopQbEach` (checkbox) **Show**
Styling, in the schema file: `bfbeShopQbEachTypography`.

### Products (`woocommerce-products`)

#### BFB Product cards (`bfbeShopCards`)
Pro, switch `shop-cards`.
- `bfbeShopCardSwatches` (checkbox) **Swatches on the card**. Place them in a field with {bfbe_card_swatches}.
- `bfbeShopSoldOut` (select) **Sold-out options**: options: `hidden` Hidden, `crossed` Crossed out (default); only when `bfbeShopCardSwatches` is set
Styling, in the schema file: `bfbeShopCardLegendTypography`, `bfbeShopCardSwatchBorder`, `bfbeShopCardSwatchOn`, `bfbeShopCardSwatchSize`, `bfbeShopCardLabelPadding`, `bfbeShopCardLabelBackground`, `bfbeShopCardSwatchGap`, `bfbeShopCardSwatchScroll`, `bfbeShopCardBtnTypography`, `bfbeShopCardBtnBackground`, `bfbeShopCardBtnBorder`, `bfbeShopCardBtnPadding`, `bfbeShopCardBtnWidth`, `bfbeShopCardBtnShadow`, `bfbeShopCardBtnHover`, `bfbeShopCardBtnHoverColor`.
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
