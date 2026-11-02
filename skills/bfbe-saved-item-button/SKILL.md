---
name: bfbe-saved-item-button
description: "Use for BFB Saved Item Button (`bfbe-saved-item-button`): Move to cart or Remove on a row of a Saved for later query loop, placed anywhere in the row. Read before writing its settings."
---

# BFB Saved Item Button (`bfbe-saved-item-button`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-saved-item-button.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/saved-item-button/

## What it is
Move to cart or Remove for one row of a Saved for later query loop, placed anywhere in the row. Move to cart adds the product back through WooCommerce's own add to cart in the saved quantity; Remove takes it off the visitor's saved list, and the block is drawn again. It needs the Cart lines feature on.

**Not for:** It works inside a Saved for later loop and prints nothing elsewhere. It is not a wishlist button: for lists a shopper keeps and shares, use BFB Wishlist Button and BFB Wishlist Bar.

**Nestable:** no · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** no

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Saved item (`bfbeSavedItem`)
- `does` (select) **Button**: options: `move` Move to cart (default), `remove` Remove. Move to cart by default, or Remove. Place one of each in a row for both.
- `label` (text) **Label**: placeholder Move to cart. "Move to cart" or "Remove" unless you set it; screen readers hear it with the product's name ("Move to cart: Stoneware Mug Set"). The element is the button, so Bricks' Style tab draws its typography, background, border, padding and hover.

## What it guarantees for accessibility (do not undo)
- A real submit button, named with the product for screen readers.
- Each press is said once: "Moved to the cart: Stoneware Mug Set." or "Removed from your saved list: Stoneware Mug Set."
- When the block is drawn again, the focus goes to the same control at the pressed one's place.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<!-- the row: the looping element, marked by the Saved for later loop -->
<div class="brxe-{id} brxe-block saved-row" data-bfbe-saved-row="412:a1b2c3" data-bfbe-saved-item="88:0" data-bfbe-shop-need="cart,saved">
  …
  <button class="brxe-{id} brxe-bfbe-saved-item-button bfbe-saved__move" type="submit" form="bfbe-saved-move-form"
          name="item" value="88:0" aria-label="Move to cart: Stoneware Mug Set">Move to cart</button>
  <button class="brxe-{id} brxe-bfbe-saved-item-button bfbe-saved__remove" type="submit" form="bfbe-saved-remove-form"
          name="item" value="88:0" aria-label="Remove: Stoneware Mug Set">Remove</button>
</div>
<!-- once per page, in the footer -->
<form id="bfbe-saved-move-form" class="bfbe-saved__form" method="post" data-bfbe-saved-act="saved_move" hidden>…</form>
<form id="bfbe-saved-remove-form" class="bfbe-saved__form" method="post" data-bfbe-saved-act="saved_remove" hidden>…</form>
```

- The root is the button itself: `bfbe-saved__move` with **Button** `does: "move"` (the default), `bfbe-saved__remove` with `does: "remove"`. Bricks' Style tab draws it (`_typography`, `_background`, `_border`, `_padding`, and hover through Bricks' `:hover` state); the stylesheet's default is an outlined button, Move to cart in bold.
- Its value is the row's `product:variation`; its name for screen readers adds the row's title. It is a real submit owned by the footer's form for its action, so it posts before any script and from inside any form.
- While a press runs, the button is `disabled`. In the canvas it is always `type="button"`, inert, with no `form` and no value.
- The row's root carries `data-bfbe-saved-row="<page>:<loop element>"` and `data-bfbe-saved-item`; an empty list prints `div.bfbe-saved__wait` beside Bricks' no-results content. The script compares those rows with the live list and draws the loop again when they differ.
- No file of its own: it loads the Cart lines feature's save for later stylesheet and script (`shop-save-later`) beside the shop's shared script.

## Wiring to other elements

- **It lives in a row of a Saved for later loop.** Place it inside the Container, Block or Div that carries `hasLoop: true` and `query.objectType: "bfbeShopSaved"`, at any depth in the row: over the picture, beside the price, at the row's start (skill `bfbe-shop-loops`). The loop has no set controls; its empty text is Bricks' own `query.no_results_text`.
- **One element per action.** Place one with `does: "move"` and one with `does: "remove"` for both; either may be left out.
- **The rest of the row** is Bricks' own elements reading the row's product: an Image of `{featured_image}`, a Heading of `{post_title}`, a Basic Text of `{woo_product_price}`, Product price or stock.
- **Rows come from Save for Later.** BFB Save for Later Button on a Bricks 2.4 cart line, or the **BFB Cart lines** group on Bricks' Cart items and Mini cart, fills the list (skills `bfbe-save-later-button`, `bfbe-shop-cart-page`, `bfbe-shop-mini-cart`). `{bfbe_saved_count}` counts it, live.
- **After a press** the loop is drawn again from the server (`wc-ajax=bfbe_shop_saved`), the mini cart refreshes from the fragments, and a cart page refreshes its form and totals, so a moved product shows in the cart at once.
- In a loop the button has no id, so give it a class in `_cssClasses` for your own CSS. Nothing targets it by attribute.

## Verified patterns

**Saved cards under the cart.** From the demo shop's cart template (`bfb-demo-cart`, "Saved for later"), colours resolved to hex. A grid of cards, each row a Block of the Saved for later loop with Bricks' Image, Heading and Basic Text, the two buttons last in a row of their own: Move to cart a dark pill, Remove a quiet word that turns orange on hover.

```json
{
  "name": "block",
  "settings": { "_display": "grid", "_gridTemplateColumns": "repeat(3, minmax(0, 1fr))", "_gridTemplateColumns:mobile_landscape": "repeat(2, minmax(0, 1fr))", "_gridGap": "16px", "_cssClasses": "saved-grid" },
  "children": [
    { "name": "block", "settings": { "hasLoop": true, "query": { "objectType": "bfbeShopSaved", "no_results_text": "Nothing saved. Press Save for later on a line to keep it here." }, "_rowGap": "6px", "_cssClasses": "saved-card" }, "children": [
      { "name": "image", "settings": { "image": { "useDynamicData": "{featured_image}", "size": "woocommerce_thumbnail" } } },
      { "name": "heading", "settings": { "text": "{post_title}", "tag": "h4" } },
      { "name": "text-basic", "settings": { "text": "{woo_product_price}" } },
      { "name": "block", "settings": { "_direction": "row", "_flexWrap": "wrap", "_alignItems": "center", "_columnGap": "12px", "_rowGap": "6px", "_margin": { "top": "auto" } }, "children": [
        { "name": "bfbe-saved-item-button", "settings": { "does": "move", "label": "Move to cart", "_typography": { "font-size": "13px", "font-weight": "700", "color": { "hex": "#ffffff" } }, "_background": { "color": { "hex": "#101828" } }, "_background:hover": { "color": { "hex": "#6e44ff" } }, "_border": { "radius": { "top": "999", "right": "999", "bottom": "999", "left": "999" } }, "_padding": { "top": "7", "right": "14", "bottom": "7", "left": "14" }, "_cssClasses": "saved-move" } },
        { "name": "bfbe-saved-item-button", "settings": { "does": "remove", "label": "Remove", "_typography": { "font-size": "13px", "font-weight": "600", "color": { "hex": "#667085" } }, "_typography:hover": { "color": { "hex": "#c2410c" } }, "_background": { "color": { "raw": "transparent" } }, "_border": { "width": { "top": "0", "right": "0", "bottom": "0", "left": "0" } }, "_padding": { "top": "7", "right": "2", "bottom": "7", "left": "2" }, "_cssClasses": "saved-remove" } }
      ] }
    ] }
  ]
}
```

**The buttons at the row's start.** From the fixture page `fixture-shop-p7b` ("Saved for later loop"). The row is a horizontal Block; the two buttons sit first in their own Block, before the picture, title and price, to show they need not come last.

```json
{
  "name": "block",
  "settings": { "hasLoop": true, "query": { "objectType": "bfbeShopSaved" }, "_direction": "row", "_columnGap": "16px", "_alignItems": "flex-start", "_cssClasses": "saved-row" },
  "children": [
    { "name": "block", "settings": { "_direction": "row", "_columnGap": "8px", "_cssClasses": "saved-buttons" }, "children": [
      { "name": "bfbe-saved-item-button", "settings": { "does": "move" } },
      { "name": "bfbe-saved-item-button", "settings": { "does": "remove" } }
    ] },
    { "name": "image", "settings": { "image": { "useDynamicData": "{featured_image}", "size": "woocommerce_thumbnail" } } },
    { "name": "heading", "settings": { "text": "{post_title}", "tag": "h4" } },
    { "name": "text-basic", "settings": { "text": "{woo_product_price}" } }
  ]
}
```

## Gotchas

- **Outside a Saved for later loop it prints nothing.** It needs the loop's row; anywhere else the page gets nothing, while the canvas shows the button to style. <!-- src: plugins/bfb-elements-pro/elements/saved-item-button.php:101-111 ; plugins/bfb-elements-pro/includes/shop/class-saved-set.php:132-147 -->
- **Not inside a loop nested in the row.** It reads the innermost loop, so inside another query loop within the row it finds no saved row. <!-- src: plugins/bfb-elements-pro/includes/shop/class-saved-set.php:136-140 -->
- **It needs the Cart lines feature.** With **Cart lines** (`shop-cart-lines`) off, the loop type is gone and the button prints nothing; the canvas says so. <!-- src: plugins/bfb-elements-pro/elements/saved-item-button.php:77-79 ; plugins/bfb-elements-pro/elements/saved-item-button.php:90-97 -->
- **The label follows the action.** Empty, **Label** prints "Move to cart" or "Remove" by `does`, though the panel's placeholder reads Move to cart for both. <!-- src: plugins/bfb-elements-pro/elements/saved-item-button.php:67-74 ; plugins/bfb-elements-pro/elements/saved-item-button.php:100 -->
- **Move to cart can be refused.** It adds the saved quantity through WooCommerce's own add to cart; a product sold out or no longer for sale stays in the list and WooCommerce's reason is announced. <!-- src: plugins/bfb-elements-pro/includes/shop/class-save-for-later.php:479-504 -->
- **The rows are replaced after every change.** The script draws the loop again from the server, so classes or listeners added to a row by other code are lost; style rows through Bricks. <!-- src: src/elements/shop-save-later/shop-save-later.js:47-70 -->
- **A redraw needs a page the visitor may read.** The server draws the loop again from its page and element ids; on a draft or private page a guest gets a 404 and the rows stay as they were. <!-- src: plugins/bfb-elements-pro/includes/shop/class-save-for-later.php:572-590 ; dev/shop/p7b-probe.mjs:635 -->
- **Custom CSS needs a class.** In a loop the button carries no id, so `%root%` or `#brxe-…` in custom CSS finds nothing; target `_cssClasses`. <!-- src: dev/demo/shop/15-templates-buy.php:475-476 -->
- **Without a script it posts to the page.** The footer's form for the action takes the row's item; the visitor comes back with the list changed and WooCommerce's notice. <!-- src: plugins/bfb-elements-pro/includes/shop/class-save-for-later.php:271-276 ; docs/elements/saved-item-button.md "Without the script" -->

## Never do

- Do not place it outside a row of a Saved for later loop (`query.objectType: "bfbeShopSaved"`).
- Do not put it inside another query loop nested in the saved row.
- Do not expect one element to give both actions; place one with `does: "move"` and one with `does: "remove"`.
- Do not style it or its row through `%root%`, `#brxe-…` or classes added by script; use `_cssClasses` and Bricks' controls.
- Do not add `disabled` or a `form` of your own to it; the script and the footer's forms handle the press.
