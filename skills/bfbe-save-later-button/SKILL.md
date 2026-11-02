---
name: bfbe-save-later-button
description: "Use for BFB Save for Later Button (`bfbe-save-later-button`): a Save for later button placed anywhere in a cart line of Bricks 2.4's v2 cart, moving the line to the saved list. Read before writing its settings."
---

# BFB Save for Later Button (`bfbe-save-later-button`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-save-later-button.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/save-later-button/

## What it is
The Save for later button of one cart line, for Bricks' experimental cart (v2), whose lines are a query loop of the cart. Place it anywhere inside the line; a press moves the line out of the cart into the visitor's saved list. It needs the Cart lines feature on; the classic Cart items element and the mini cart get their button from that feature.

**Not for:** It is for the lines of Bricks' experimental cart; the classic Cart items element and the mini cart get their button from the Cart lines feature. A free gift, an offer's line, a line with product options or one in a bundle gets no button, and with WooCommerce's own Save for later on it prints nothing.

**Nestable:** no · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** no

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Save for later (`bfbeSaveLater`)
- `label` (text) **Label**: placeholder Save for later. "Save for later" unless you set it; screen readers hear it with the line added ("Save for later: Waffle Bath Towel"). The element is the button, so Bricks' Style tab draws its typography, background, border, padding and hover.

## What it guarantees for accessibility (do not undo)
- A real submit button, named with its line for screen readers.
- After a press the result is said once ("Saved for later: Stoneware Mug Set."), and the focus goes to the same control where the cart is drawn again.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<!-- in a cart line (a row of Bricks 2.4's cart loop): no id, the element id as a class -->
<button class="brxe-{id} brxe-bfbe-save-later-button bfbe-savelater" type="submit" form="bfbe-savelater-form"
        name="key" value="{cart item key}" aria-label="Save for later: Waffle Bath Towel"
        data-bfbe-savelater="Waffle Bath Towel">Save for later</button>
<!-- once per page, in the footer -->
<form id="bfbe-savelater-form" class="bfbe-savelater__form" method="post" hidden>
  <input type="hidden" name="bfbe_shop_act" value="cart_save_later">…</form>
```

- The root is the button itself: Bricks' Style tab draws it (`_typography`, `_background`, `_border`, `_padding`, and hover through Bricks' `:hover` state). The stylesheet's default is a small outlined button, `inline-block`, with a 4px top margin.
- It is a real submit owned by the footer's form through the `form` attribute, because the line sits inside WooCommerce's cart form, where a second form cannot be. Its value is the line's cart item key; its name for screen readers adds the line's name.
- While a press runs, the button is `disabled`. In the canvas it is `type="button"` with no `form`, inert, inside a line or outside one.
- It shares the class `bfbe-savelater` and the footer form with the button the Cart lines feature adds to the classic Cart items element and to the mini cart's lines; one script handles all three.
- No file of its own: it loads the Cart lines feature's save for later stylesheet and script (`shop-save-later`) beside the shop's shared script.

## Wiring to other elements

- **It reads the line of the loop it sits in.** In Bricks 2.4, the Cart (v2) element's cart form holds a Div with **Use query loop** and `query.objectType: "wooCart"` (the preset's "Cart loop"); place the button anywhere in that Div's row, at any depth, beside Bricks' Cart item data, Cart quantity or the line's texts. The demo shop also places one in the Checkout (v2) order summary's cart loop.
- **Bricks 2.3 has no such loop.** There, and on 2.4's classic elements, the button comes from the **BFB Cart lines** group on Bricks' Cart items and Mini cart (`bfbeShopCartLinesSave`, `bfbeShopCartLinesSaveText`; skills `bfbe-shop-cart-page`, `bfbe-shop-mini-cart`).
- **Where the line goes.** A press moves the line into the visitor's saved list: list it with a query loop of type **Saved for later** (`bfbeShopSaved`, skill `bfbe-shop-loops`) and give each row BFB Saved Item Button (`bfbe-saved-item-button`). `{bfbe_saved_count}` counts the list, live.
- **After a press** the mini cart refreshes from the fragments, a v2 cart is fetched again and swapped whole, a classic cart its form and totals, and every saved loop on the page is drawn again.
- In a loop the button has no id, so give it a class in `_cssClasses` for your own CSS. Nothing targets it by attribute.

## Verified patterns

**The line's details with Save for later among them.** From the fixture template `bfbe-shop-cart-v2` on the Bricks 2.4 site ("Product details wrapper" in the preset's Cart row), with the demo checkout's pill look (`bfb-demo-checkout`, "Quantity, save for later and remove"). The dev site runs Bricks 2.3.10, which has no v2 cart, so this tree is checked for its keys there, not rendered. Add it inside the preset's Cart loop row; the preset's Cart item data and Cart quantity go beside it on 2.4.

```json
{
  "name": "div",
  "settings": { "_display": "flex", "_direction": "column", "_rowGap": "10px", "_flexGrow": "1", "_cssClasses": "line-details" },
  "children": [
    { "name": "text-basic", "settings": { "text": "{woo_cart_product_title:plain}" } },
    { "name": "text-basic", "settings": { "text": "{woo_cart_item_price}" } },
    { "name": "bfbe-save-later-button", "settings": { "label": "Save for later", "_typography": { "font-size": "13px", "font-weight": "600", "color": { "hex": "#101828" } }, "_background": { "color": { "hex": "#ffffff" } }, "_background:hover": { "color": { "hex": "#f0ecff" } }, "_border": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "999", "right": "999", "bottom": "999", "left": "999" } }, "_padding": { "top": "5", "right": "12", "bottom": "5", "left": "12" }, "_cssClasses": "line-save" } }
  ]
}
```

## Gotchas

- **Outside a cart line it prints nothing.** It needs the loop row of a cart line; anywhere else the page gets nothing, while the canvas still shows the button to style. <!-- src: plugins/bfb-elements-pro/elements/save-later-button.php:81-91 ; plugins/bfb-elements-pro/includes/shop/class-save-for-later.php:218-225 -->
- **Not inside a loop nested in the line.** It reads the innermost loop's object, so inside another query loop within the row it finds no cart line. <!-- src: plugins/bfb-elements-pro/includes/shop/class-save-for-later.php:218-225 -->
- **Gift and offer lines get none.** A Cart Goals gift line or a BFB Offer line belongs to the server, so the button prints nothing there. <!-- src: plugins/bfb-elements-pro/includes/shop/class-save-for-later.php:227-230 -->
- **It needs the Cart lines feature.** With **Cart lines** (`shop-cart-lines`) off on BFB Elements, Elements, it prints nothing and the canvas says so. <!-- src: plugins/bfb-elements-pro/elements/save-later-button.php:60-62 ; plugins/bfb-elements-pro/elements/save-later-button.php:75-80 -->
- **WooCommerce's own Save for later wins.** With that WooCommerce feature on, this element prints nothing; WooCommerce's block cart keeps the list. <!-- src: plugins/bfb-elements-pro/elements/save-later-button.php:61 ; plugins/bfb-elements-pro/includes/shop/class-save-for-later.php:103-114 ; docs/elements/save-later-button.md "With WooCommerce's own Save for later" -->
- **The saved list holds fifty.** A fifty-first product is refused with "Your saved list is full (50). Remove something from it first." and the line stays in the cart. <!-- src: plugins/bfb-elements-pro/includes/shop/class-save-for-later.php:453-458 -->
- **Custom CSS needs a class.** In the cart loop the button carries no id, so `%root%` or `#brxe-…` in custom CSS finds nothing; target `_cssClasses`. <!-- src: dev/demo/shop/15-templates-buy.php:475-476 -->
- **Without a script it posts to the page.** The footer's form takes the line's key; the line leaves the cart and the visitor comes back to the cart with WooCommerce's notice. <!-- src: plugins/bfb-elements-pro/includes/shop/class-save-for-later.php:291-294 ; docs/elements/save-later-button.md "Without the script" -->

## Never do

- Do not place it outside a row of Bricks 2.4's cart loop; on 2.3 use the BFB Cart lines group on Bricks' Cart items.
- Do not put it inside another query loop nested in the cart line.
- Do not place it on a site with the Cart lines feature off or WooCommerce's own Save for later on.
- Do not style it through `%root%` or `#brxe-…`; give it a class.
- Do not add `disabled` or a `form` of your own to it; the script and the footer's form handle the press.
