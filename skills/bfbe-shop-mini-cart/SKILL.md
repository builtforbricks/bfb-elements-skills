---
name: bfbe-shop-mini-cart
description: "Use for the shop's settings on Bricks' Mini cart: the accessible panel, its empty state, its look, save for later and undo on its lines (BFB Shop mini cart, `shop-mini-cart`). Read before writing these settings."
---

# BFB Shop mini cart (`shop-mini-cart`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 2.0.0 or later, and BFB Elements Pro 2.0.0 or later for the groups marked Pro, WooCommerce active, the feature switches on (WordPress menu BFB Elements, Elements): `shop-mini-cart`, `shop-cart-lines`. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/shop-mini-cart.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/shop-mini-cart/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

## Where it lives
A feature, not an element: its groups are added to Bricks' own elements, on the Content tab after Bricks' own groups. By element:
- Mini cart (`woocommerce-mini-cart`): BFB Mini cart (`bfbeShopMiniCart`), BFB Mini cart look (`bfbeShopMiniCartLook`), BFB Cart lines (`bfbeShopCartLines`).

## Settings that decide the build

### Mini cart (`woocommerce-mini-cart`)

#### BFB Mini cart (`bfbeShopMiniCart`)
Free, switch `shop-mini-cart`.
- `bfbeShopMiniCartTitle` (text) **Panel title**. At the top of the panel, beside the close button.
- `bfbeShopMiniCartAdded` (text) **Announcement after adding**: placeholder Added: {product}. {cart}
- `bfbeShopMiniCartRemoved` (text) **Announcement after removing**: placeholder Removed: {product}. {cart}
- `bfbeShopMiniCartEmpty` (select) **When empty**: options: `woo` Show WooCommerce's text (default), `template` Show a template, `hide` Hide the whole mini cart
- `bfbeShopMiniCartTemplate` (select) **Template**: options: the site's own, read when the panel opens; only when `bfbeShopMiniCartEmpty` is `template`
Styling, in the schema file: `bfbeShopMiniCartEmptyPadding`.

#### BFB Mini cart look (`bfbeShopMiniCartLook`)
Free, switch `shop-mini-cart`.
- `bfbeShopMiniCartCountPlace` (select) **Count sits**: options: `static` After the amount, `absolute` On the link's corner; writes CSS
Styling, in the schema file: `bfbeShopMiniCartPanelMargin`, `bfbeShopMiniCartTitleTypography`, `bfbeShopMiniCartTitlePadding`, `bfbeShopMiniCartTextStart`, `bfbeShopMiniCartLineBackground`, `bfbeShopMiniCartLineBorder`, `bfbeShopMiniCartLinePadding`, `bfbeShopMiniCartLineShadow`, `bfbeShopMiniCartLineGap`, `bfbeShopMiniCartPictureBorder`, `bfbeShopMiniCartRemovePosition`, `bfbeShopMiniCartLinkHeight`, `bfbeShopMiniCartLinkWidth`, `bfbeShopMiniCartLinkPadding`, `bfbeShopMiniCartLinkAlign`, `bfbeShopMiniCartLinkBackground`, `bfbeShopMiniCartLinkBorder`, `bfbeShopMiniCartLinkTransition`, `bfbeShopMiniCartIconSize`, `bfbeShopMiniCartIconColor`, `bfbeShopMiniCartCountMargin`, `bfbeShopMiniCartCountShadow`, `bfbeShopMiniCartAmountHide`.

#### BFB Cart lines (`bfbeShopCartLines`)
Pro, switch `shop-cart-lines`.
- `bfbeShopCartLinesUndo` (select) **Show**: options: `on` On (default), `off` Off. A strip to bring back a removed item.
- `bfbeShopCartLinesUndoTime` (number) **Stays for (s)**: placeholder 12; only when `bfbeShopCartLinesUndo` is not `off`
- `bfbeShopCartLinesSave` (select) **Show**: options: `on` On (default), `off` Off. A button on each line.
- `bfbeShopCartLinesSaveText` (text) **Label**: placeholder Save for later; only when `bfbeShopCartLinesSave` is not `off`
Styling, in the schema file: `bfbeShopCartLinesUndoTypography`, `bfbeShopCartLinesUndoBackground`, `bfbeShopCartLinesUndoBorder`, `bfbeShopCartLinesUndoPadding`, `bfbeShopCartLinesUndoShadow`, `bfbeShopCartLinesUndoOver`, `bfbeShopCartLinesUndoPosition`, `bfbeShopCartLinesUndoBtnTypography`, `bfbeShopCartLinesUndoBtnBackground`, `bfbeShopCartLinesUndoBtnBorder`, `bfbeShopCartLinesUndoBtnPadding`, `bfbeShopCartLinesUndoBtnHover`, `bfbeShopCartLinesUndoBtnHoverColor`, `bfbeShopCartLinesSaveTypography`, `bfbeShopCartLinesSaveBackground`, `bfbeShopCartLinesSaveBorder`, `bfbeShopCartLinesSavePadding`, `bfbeShopCartLinesSaveHover`.
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
