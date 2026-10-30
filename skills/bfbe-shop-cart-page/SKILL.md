---
name: bfbe-shop-cart-page
description: "Use for the shop's settings on Bricks' Cart items, Cart totals and Cart coupon, and the live cart switch on Containers (BFB Shop cart page, `shop-cart-page`): the cart table's look, the quantity as one box, save for later on the lines, the coupon field on any page, and a cart or popup mini cart of your own layout that redraws after every cart change. Read before writing these settings."
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

The feature draws no element. It writes CSS at the host's id, attributes on the host's root, and a few parts inside WooCommerce's markup.

- **BFB Table** is CSS on WooCommerce's `table.shop_table`: its border (switched to the separate border model, so corners round), `th` and `td`, `.product-name a`, `.order-total`, the totals' title `.cart_totals > h2`. **Stack the rows** (`bfbeShopTableStack`) makes each `tr` of `table.shop_table_responsive` a block and prints each cell's `data-title` as its label (`::before`).
- **Cart items' line parts**: `.product-thumbnail img`; `.product-remove a` (**Remove button size** sets its width and height, `display: grid`, `place-items: center` and `line-height: 1`, so the × centres); `.quantity input.qty`; `.quantity`, the number and Bricks' buttons as one box (`bfbeShopTableQtyBoxWidth`, `QtyBoxPadding`, `QtyBoxBorder` with `overflow: hidden`); `.quantity .action`, Bricks' − and + (`bfbeShopTableQtyBtn*`); `td.actions`. **Quantity height** (`bfbeShopTableQtyHeight`) sets the number's `height` and `min-height`, Bricks' `--bricks-woo-input-height` on `.quantity`, and `padding: 0` on the number. **Quantity buttons** `browser` or `none` writes `data-bfbe-qty` on the root instead.
- **BFB Form fields** on Cart totals write the shipping calculator's `.form-row` (a row gap makes it a flex column) and the `.select2-selection--single` dropdowns.
- **BFB Cart lines** on Cart items prints, after each line's name, `<button type="submit" class="bfbe-savelater" form="bfbe-savelater-form" name="key" value="{line key}" aria-label="Save for later: …">`, owned by `form#bfbe-savelater-form.bfbe-savelater__form[hidden]` in the footer.
- **BFB Coupons** on Cart coupon (its root is the `form`): `data-bfbe-coupons="1"`, `action` set to the page itself, `data-bfbe-shop-need="cart,coupons"`, Apply renamed `bfbe_apply`, the action's hidden fields and `p.bfbe-coupons__notice[hidden]` (`.is-error` for a refusal) inside. The field and Apply stretch to one height. `bfbeShopCouponsNoticeTypography` and `bfbeShopCouponsErrorColor` write the notice.
- **BFB Live cart** on a Block, Container or Div:

```html
<div class="brxe-block fh-yourcart" data-bfbe-shop-region="412:a1b2c3:412" data-bfbe-shop-stamp="5f2c9e01ab34" data-bfbe-shop-need="regions" aria-busy="true">
  … drawn again on the server and swapped whole after every cart change …
</div>
```

The mark is page, element and context; the stamp names the cart it was drawn for. `aria-busy` stays until the new copy arrives; after a swap `document` hears Bricks' `bricks/ajax/load_page/completed` and `bfbe:shop:regions` (`detail.regions`).

## Wiring to other elements

- **Hub and neighbours.** Start at `bfbe-shop`. The Cart contents loop (`query.objectType: "wooCart"`) and the Saved for later loop (`bfbeShopSaved`) are `bfbe-shop-loops`; the live cart tags (`{bfbe_cart_subtotal}`, `{bfbe_cart_discount}`, `{bfbe_cart_shipping}`, `{bfbe_cart_tax}`, `{bfbe_cart_total}`, `{bfbe_cart_count}`, `{bfbe_cart_coupons}`) and the cart conditions (`bfbe_shop_cart_items`) are `bfbe-shop-tags-and-conditions`.
- **A cart page of Bricks' elements**: Cart items for the lines, Cart totals beside them, Cart coupon with BFB Applied Coupons for the code and the applied list (`bfbe-applied-coupons`), and around them BFB Empty Cart Button, BFB Cart Goals, BFB Offer and a Saved for later loop with BFB Saved Item Button.
- **A cart of your own layout**: one Block with `bfbeLiveCart: true` holding a Cart contents loop whose rows carry BFB Cart Quantity (`bfbe-cart-quantity`) and the row tags, the live tags for the sums, and BFB Cart Shipping (`bfbe-cart-shipping`). Every cart change redraws the region: our actions, WooCommerce's buttons, the Mini cart's remove, the cart page's own update.
- **A mini cart in a Bricks popup** is the same region inside a popup template; it follows the cart open or closed. Bricks' own Mini cart element is `bfbe-shop-mini-cart`.
- **Bricks 2.4's v2 cart** (its experimental shop setting) takes BFB Save for Later Button on its lines (`bfbe-save-later-button`); the Cart lines group here is for the classic Cart items.
- Nothing is wired by class or id: a region is found by its mark, a coupon form by its attribute, save for later by the line key.

## Verified patterns

**A cart page of Bricks' elements.** From the demo shop's cart template (`dev/demo/shop/15-templates-buy.php`, "Lines" and "Totals"). Cart items with a rounded table, the quantity as one pill-shaped box of 30px with round buttons, the × centred in a 30px circle, Save for later on each line, rows stacked on a phone; Cart totals with the same table look; the coupon field beside them with the applied list. Trimmed: the demo's colour variables, the offer, cart goals, delivery estimate and Saved for later block.

```json
{
  "name": "block",
  "settings": { "_display": "grid", "_gridTemplateColumns": "minmax(0, 1fr) 400px", "_gridTemplateColumns:tablet_portrait": "minmax(0, 1fr)", "_gridGap": "40px", "_alignItems": "start" },
  "children": [
    { "name": "woocommerce-cart-items", "settings": {
      "hideCoupon": true, "headBackground": { "hex": "#f7f8fa" }, "width": "84px",
      "bfbeShopTableBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "16", "right": "16", "bottom": "16", "left": "16" } },
      "bfbeShopTableCellPadding": { "top": "16", "right": "16", "bottom": "16", "left": "16" },
      "bfbeShopTableAlign": "left", "bfbeShopTableLine": { "hex": "#e9ecf1" },
      "bfbeShopTableLinkTypography": { "font-weight": "700" },
      "bfbeShopTableImageBorder": { "radius": { "top": "12", "right": "12", "bottom": "12", "left": "12" } },
      "bfbeShopTableRemoveSize": "30px", "bfbeShopTableRemoveBackground": { "hex": "#f7f8fa" },
      "bfbeShopTableRemoveBorder": { "radius": { "top": "999", "right": "999", "bottom": "999", "left": "999" } },
      "bfbeShopTableQtyWidth": "36px", "bfbeShopTableQtyAlign": "center",
      "bfbeShopTableQtyBorder": { "width": { "top": "0", "right": "0", "bottom": "0", "left": "0" }, "style": "solid" },
      "bfbeShopTableQtyBoxWidth": "fit-content", "bfbeShopTableQtyHeight": "30px",
      "bfbeShopTableQtyBoxPadding": { "top": "3", "right": "3", "bottom": "3", "left": "3" },
      "bfbeShopTableQtyBoxBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "999", "right": "999", "bottom": "999", "left": "999" } },
      "bfbeShopTableQtyBtnWidth": "30px", "bfbeShopTableQtyBtnBg": { "hex": "#f6f6f8" }, "bfbeShopTableQtyBtnHover": { "hex": "#f0ecff" },
      "bfbeShopTableQtyBtnBorder": { "width": { "top": "0", "right": "0", "bottom": "0", "left": "0" }, "style": "solid", "radius": { "top": "999", "right": "999", "bottom": "999", "left": "999" } },
      "bfbeShopTableActionsAlign": "right",
      "bfbeShopTableStack:mobile_landscape": true,
      "bfbeShopTableStackPadding:mobile_landscape": { "top": "10", "right": "16", "bottom": "10", "left": "16" },
      "bfbeShopTableLabelTypography": { "font-weight": "700" },
      "bfbeShopCartLinesSave": "on", "bfbeShopCartLinesSaveText": "Save for later"
    } },
    { "name": "block", "settings": { "_rowGap": "18px" }, "children": [
      { "name": "woocommerce-cart-collaterals", "settings": {
        "disableCrossSells": true,
        "tableBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "16", "right": "16", "bottom": "16", "left": "16" } },
        "tablePadding": { "top": "16", "right": "16", "bottom": "16", "left": "16" },
        "bfbeShopTableAlign": "left", "bfbeShopTableLine": { "hex": "#e9ecf1" },
        "bfbeShopTableTotalTypography": { "font-size": "18px", "font-weight": "800" },
        "bfbeShopTableTitleMargin": { "top": "0", "right": "0", "bottom": "16", "left": "0" },
        "bfbeShopTableStack:mobile_landscape": true,
        "bfbeShopFieldsRowGap": "6px", "bfbeShopFieldsRowSpacing": "14px", "bfbeShopFieldsSelectHeight": "46px"
      } },
      { "name": "woocommerce-cart-coupon", "settings": { "bfbeShopCouponsAnywhere": "on" } },
      { "name": "bfbe-applied-coupons", "settings": { "removeWord": "Remove" } }
    ] }
  ]
}
```

**A quick cart in a Bricks popup that follows every change.** From the demo shop's popup template "the quick cart" (`dev/demo/shop/15-templates-buy.php`). One region of the popup's full height with its own scroll; an empty state and the lines, each under a cart condition decided again at every redraw; the rows of a Cart contents loop with BFB Cart Quantity; the next cart goal and the subtotal. Trimmed: the close button, the offer, the buttons and the demo's look.

```json
{
  "name": "block",
  "settings": { "bfbeLiveCart": true, "_cssClasses": "quick-cart", "_rowGap": "16px", "_height": "100%", "_overflow": "auto", "_flexWrap": "nowrap", "_padding": { "top": "24", "right": "24", "bottom": "24", "left": "24" } },
  "children": [
    { "name": "heading", "settings": { "text": "Your cart", "tag": "h2" } },
    { "name": "block", "settings": { "_conditions": [ [ { "key": "bfbe_shop_cart_items", "compare": "==", "value": "0" } ] ] }, "children": [
      { "name": "text-basic", "settings": { "text": "Nothing in your cart yet." } }
    ] },
    { "name": "block", "settings": { "_rowGap": "16px", "_conditions": [ [ { "key": "bfbe_shop_cart_items", "compare": ">=", "value": "1" } ] ] }, "children": [
      { "name": "block", "settings": { "hasLoop": true, "query": { "objectType": "wooCart" }, "_direction": "row", "_flexWrap": "nowrap", "_columnGap": "14px" }, "children": [
        { "name": "image", "settings": { "image": { "useDynamicData": "{featured_image}", "size": "woocommerce_thumbnail" }, "_width": "64px" } },
        { "name": "block", "settings": { "_rowGap": "6px", "_flexGrow": "1" }, "children": [
          { "name": "text-basic", "settings": { "text": "{post_title}" } },
          { "name": "text-basic", "settings": { "text": "{bfbe_cart_line_options}" } },
          { "name": "bfbe-cart-quantity", "settings": { "size": "32px", "inputWidth": "34px" } }
        ] },
        { "name": "text-basic", "settings": { "text": "{woo_cart_subtotal}" } }
      ] },
      { "name": "bfbe-cart-goals", "settings": { "nextOnly": true, "steps": "hide" } },
      { "name": "text-basic", "settings": { "text": "Subtotal {bfbe_cart_subtotal}" } }
    ] }
  ]
}
```

**A coupon field on a page that is not the cart.** From the demo shop's "Have a code?" card (`dev/demo/shop/20-pages.php`). Works anywhere applies the code without leaving the page; the class `woocommerce` lets the theme style's WooCommerce button reach Apply; the applied list and the codes tag sit under it.

```json
{
  "name": "block",
  "settings": { "_rowGap": "12px" },
  "children": [
    { "name": "heading", "settings": { "text": "Have a code?", "tag": "h3" } },
    { "name": "woocommerce-cart-coupon", "settings": { "bfbeShopCouponsAnywhere": "on", "_cssClasses": "woocommerce" } },
    { "name": "bfbe-applied-coupons", "settings": { "removeWord": "Remove" } },
    { "name": "text-basic", "settings": { "text": "On your cart now: <strong>{bfbe_cart_coupons @fallback:'no code yet'}</strong>" } }
  ]
}
```

## Gotchas

- **Put the live switch on the element that holds the loop.** On the looping element itself each row would be drawn as the whole loop, so the switch is ignored there. <!-- src: plugins/bfb-elements-pro/includes/shop/class-live-cart.php:116-120 ; docs/elements/shop-live-cart.md "BFB Live cart" -->
- **Some regions are never drawn again.** A region inside a component is not, nor more than twelve on a page; a region whose own conditions say no is hidden until they say yes, so keep conditions on the elements inside it. <!-- src: docs/elements/shop-live-cart.md "Limits" ; plugins/bfb-elements-pro/includes/shop/class-live-cart.php:46-47 -->
- **A region of fixed height needs `_flexWrap: "nowrap"`.** A Block wraps by default, and a column of fixed height in a popup wraps its overflow into a second column. <!-- src: dev/demo/shop/15-templates-buy.php:133-135 -->
- **A region says nothing and shows nothing new in the builder.** The action that changed the cart announces; the canvas prints no region marks. <!-- src: src/elements/shop-live-cart/shop-live-cart.js:12-13 ; plugins/bfb-elements-pro/includes/shop/class-live-cart.php:113 -->
- **Set Quantity height to tame a tall field.** A theme style's field padding and minimum height (Bricks' and BFB Form fields) make the cart's number taller than any height; only `bfbeShopTableQtyHeight` makes them give way. <!-- src: plugins/bfb-elements/includes/shop/class-woo-look.php:370-383 -->
- **Bricks' buttons' look needs Bricks' buttons.** `bfbeShopTableQtyBtnWidth`, `QtyBtnColor`, `QtyBtnBg`, `QtyBtnBorder` and `QtyBtnHover` show only while `bfbeShopTableQtyButtons` is not `browser` or `none`. <!-- src: plugins/bfb-elements/includes/shop/class-woo-look.php:398-440 -->
- **BFB Table differs by host.** Cart totals has no Border or Cell padding (use Bricks' `tableBorder` and `tablePadding`), and Cart items no header row (use Bricks' `headBackground` and `headTypography`). <!-- src: plugins/bfb-elements/includes/shop/class-woo-look.php:37-43 ; dev/demo/shop/15-templates-buy.php:227 -->
- **Stack the rows at a phone breakpoint.** `bfbeShopTableStack` set without a breakpoint suffix stacks the table at every width; the demo sets `bfbeShopTableStack:mobile_landscape`. <!-- src: plugins/bfb-elements/includes/shop/class-woo-look.php:244-250 ; dev/demo/shop/15-templates-buy.php:203 -->
- **Works anywhere is on unless set off.** The form then posts to its own page and Apply is renamed, even on the cart page; set `bfbeShopCouponsAnywhere: "off"` to keep Bricks' element as it is, with its **Update cart via AJAX** (`ajaxUpdate`). <!-- src: plugins/bfb-elements-pro/includes/shop/class-coupons.php:214-233 ; docs/elements/shop-coupons.md "Bricks' Cart coupon element, anywhere" -->
- **WooCommerce's own coupon row in Cart items is not changed.** Hide it with Bricks' `hideCoupon` and place Cart coupon where it belongs. With Direction set to column, the field and Apply stretch to the full width. <!-- src: docs/elements/shop-coupons.md "Limits" ; src/elements/shop-coupons/shop-coupons.css:2-5 -->
- **Off a shop page Apply misses the theme's WooCommerce button.** That look is written for `.woocommerce .button`; give the Cart coupon the class `woocommerce`, as the demo does. <!-- src: dev/demo/shop/20-pages.php:345 ; plugins/bfb-elements/includes/shop/class-theme-styles.php:45 -->
- **Save for later skips some lines.** A gift's or an offer's line gets no button, and where WooCommerce's own Save for Later in Cart is on, the controls are not offered at all. <!-- src: plugins/bfb-elements-pro/includes/shop/class-save-for-later.php:77-79 ; plugins/bfb-elements-pro/includes/shop/class-save-for-later.php:226-230 -->

## Never do

- Do not set `bfbeLiveCart` on a looping element, or on an element inside a component.
- Do not give a fixed-height region in a popup Bricks' default wrap; set `_flexWrap: "nowrap"`.
- Do not set a `bfbeShopTableQtyBtn*` key with `bfbeShopTableQtyButtons` set to `browser` or `none`.
- Do not look for BFB Table's Border on Cart totals or its header row on Cart items; use Bricks' own controls there.
- Do not leave `bfbeShopCouponsAnywhere` on where Bricks' `ajaxUpdate` must run.
- Do not keep WooCommerce's coupon row in Cart items beside a Cart coupon element; set `hideCoupon`.
- Do not place a Cart coupon off a shop page without the class `woocommerce` when the theme style's WooCommerce button must reach it.
