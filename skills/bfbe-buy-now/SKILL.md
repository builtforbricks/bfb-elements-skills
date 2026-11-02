---
name: bfbe-buy-now
description: "Use when placing a Buy now button that goes straight to the checkout, beside Bricks' Add to cart, anywhere on a product page or on product cards in a query loop (BFB Buy Now, `bfbe-buy-now`). Read before writing its settings."
---

# BFB Buy Now (`bfbe-buy-now`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-buy-now.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/buy-now/

## What it is
A Buy now button you place anywhere on a product page or in a product query loop row, which takes the shopper straight to the checkout with this product. It joins the product's own add to cart form, so the chosen variation, the quantity and any option fields go with it, and WooCommerce adds the product with its own checks. By default the rest of the cart is set aside and comes back on the cart page or after the order. It needs the Buying switch on.

**Not for:** Not for external products, sold-out products or products under catalogue mode, which get no button. Bricks' Products element prints its own cards, so the button cannot stand inside them: use a query loop for cards with a Buy now.

**Costs a page:** CSS none, JS none (gzipped), plus shop-buy, loaded only on pages that use it. Only where used, buying: the BFB Buy Now's post and look, and catalogue mode with ask for a price: CSS 0.25 KB, JS 1.40 KB.

**Nestable:** no · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** no

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Buy now (`bfbeBuy`)
- `text` (text) **Label**: placeholder Buy now; dynamic data accepted. The button's words, Buy now unless set; it takes dynamic data.
- `takes` (select) **Buy now takes**: options: `alone` This item alone, the cart kept for later (default), `with` This item with the cart. This item alone, the cart kept for later (the default) sets the cart's lines and coupons aside, so the checkout holds this item alone, and puts them back on the cart page or after the order. Choose This item with the cart for a shop where people buy several things at once.

## What it guarantees for accessibility (do not undo)
- It is a real submit button joined to the product's form by the HTML form attribute, so Enter and Space press it, and it posts before and without JavaScript.
- On a variable product's page it is disabled while no variation is chosen, following WooCommerce's own add button, and dimmed to half while it waits.
- In a product card, pressed before every swatch is chosen, it says what is missing through the shop's live region and moves the focus to a swatch group still open; nothing is posted.
- Its focus ring is the pack's own focus outline.
<!-- bfbe:generated:end -->

## Rendered DOM

The element's root is the button itself, a real submit with WooCommerce's `.button` look:

```html
<button type="submit" form="bfbe-cart-123" id="brxe-{id}" class="brxe-bfbe-buy-now button bfbe-buy"
        name="bfbe_buy_now" value="alone" data-bfbe-buy data-bfbe-buy-product="123"
        data-bfbe-buy-url="https://example.com/product/workshop-apron/">Buy now</button>
<!-- a simple product only: the product id the press must carry -->
<input type="hidden" form="bfbe-cart-123" name="add-to-cart" value="123">
```

- `form` names the product's own add to cart form: `bfbe-cart-{product id}` on a product page, `bfbe-cart-{id}-{loop element id}-{row}` in a query loop row. `value` is **Buy now takes** (`takes`: `alone` or `with`).
- A simple product with no form to join (in a loop, or on a page with no Add to cart) gets a form of its own after the button: `form.bfbe-buy__form[hidden]`, id `bfbe-buy-{id}-{n}`, posting `add-to-cart` and `quantity` 1 to the product's address.
- States: `disabled` while a variable product's page has no variation chosen, dimmed to half by the stylesheet. The script joins a form the server could not name by setting `form` itself, and in a card form it posts the form with a hidden `bfbe_buy_now` field.
- In the builder the button is `type="button"` with no `form`: it posts nothing.
- A product that cannot be bought prints nothing at all on the page.
- No look controls: Bricks' Style tab (typography, background, border, padding, width, height, hover) writes the button directly. The stylesheet adds only the disabled look and the focus ring.

## Wiring to other elements

- **It joins Bricks' Add to cart by the product, never by class or id.** On a product template place it anywhere, in any container, before or after the form: the Add to cart's `form.cart` carries `bfbe-cart-{id}` (the Buying switch adds it) and the button names it, so the chosen variation, the quantity and any option fields post with it. Nothing needs a `_cssClasses` or `_cssId`.
- **In a query loop row** it joins the card form that BFB Product cards (`bfbeShopCardSwatches` on Bricks' Add to cart) prints in the same looping element: the loop element and the row are in both ids. Pressed before every swatch is chosen, it says so and focuses the first open group.
- **Product options.** A BFB Advanced Forms form with the shop's product options joins the same `bfbe-cart-{id}` form, so its fields post with a Buy now press too.
- **Bricks' AJAX add to cart** binds the add button alone (`.single_add_to_cart_button`), so with it on the Add to cart adds in place and Buy now still posts and lands on the checkout.
- **The cart page and the order-received page** give back the cart set aside by `takes: "alone"`; nothing to place there.
- See `bfbe-shop-add-to-cart` for the form and the card swatches, and `bfbe-shop` for the switches.

## Verified patterns

**Buy now beside Add to cart, feet on one line.** From the 2.4 site's demo shop, template "Fernhouse: product page" (`bfb-demo-product`), the row "Add to cart and Buy now". The row aligns at its end, since Add to cart holds the choices above its button; both share the row and stack on a phone. The Buy Now's 52px `_height` matches the form's `bfbeShopRowHeight`. Trimmed: the Add to cart's look and the demo's colour variables.

```json
{
  "name": "block",
  "settings": { "_direction": "row", "_alignItems": "flex-end", "_columnGap": "10px", "_rowGap": "10px", "_direction:mobile_landscape": "column", "_alignItems:mobile_landscape": "stretch" },
  "children": [
    { "name": "product-add-to-cart", "settings": { "bfbeShopRowHeight": "52px", "_flexGrow": "1", "_flexShrink": "1", "_flexBasis": "0", "_widthMin": "0" } },
    {
      "name": "bfbe-buy-now",
      "settings": {
        "text": "Buy now",
        "takes": "alone",
        "_display": "flex", "_justifyContent": "center", "_alignItems": "center",
        "_flexGrow": "1", "_flexShrink": "1", "_flexBasis": "0", "_widthMin": "0",
        "_height": "52px",
        "_padding": { "top": "12", "right": "22", "bottom": "12", "left": "22" },
        "_background": { "color": { "hex": "#101828" } },
        "_typography": { "font-size": "15px", "font-weight": "700", "color": { "hex": "#ffffff" } },
        "_border": { "radius": { "top": "999", "right": "999", "bottom": "999", "left": "999" } }
      }
    }
  ]
}
```

**Buy now away from the form.** From the template "Shop P5a: single product" (`bfbe-shop-product-p5a`), the block "Elsewhere" in the gallery's column, a whole column away from the Add to cart: the table follows the form's quantity and the button posts the form. Takes the item alone.

```json
{
  "name": "block",
  "settings": { "_rowGap": "12px" },
  "children": [
    { "name": "bfbe-quantity-breaks", "settings": {} },
    { "name": "bfbe-buy-now", "settings": { "takes": "alone", "text": "Buy now" } }
  ]
}
```

**Buy now on product cards.** From the fixture "PRO: Shop, Buy now on cards and catalogue products in a loop" (`fixture-shop-buy-cards`). The button sits above the image in each looping card and takes the item with the cart; the card's Add to cart carries the swatch form it joins. A simple product's card posts its own small form. The fixture's `post__in` list is left out, and its grid moved onto a wrapper, since Bricks repeats the looping element itself.

```json
{
  "name": "block",
  "settings": { "_display": "grid", "_gridTemplateColumns": "repeat(3, minmax(0, 1fr))", "_gridGap": "24px" },
  "children": [
    {
      "name": "block",
      "settings": { "hasLoop": true, "query": { "objectType": "post", "post_type": ["product"], "posts_per_page": 6 } },
      "children": [
        { "name": "bfbe-buy-now", "settings": { "takes": "with", "text": "Buy now" } },
        { "name": "image", "settings": { "image": { "useDynamicData": "{featured_image}", "size": "woocommerce_thumbnail" } } },
        { "name": "product-title", "settings": { "tag": "h3" } },
        { "name": "product-price", "settings": {} },
        { "name": "product-add-to-cart", "settings": { "bfbeShopCardSwatches": true, "bfbeShopCardAddText": "Add" } }
      ]
    }
  ]
}
```

## Gotchas

- **It needs the Buying switch.** Without `shop-buy` on (BFB Elements, Elements) the press has nowhere to go: the canvas says so and the page prints nothing. The switch also gives Add to cart's form the id the button names. <!-- src: plugins/bfb-elements-pro/elements/buy-now.php:82 ; plugins/bfb-elements-pro/includes/shop/class-buy-now.php:55-61 -->
- **Some products get no button.** External products, products out of stock and products under a catalogue rule print nothing, and so does a page that is not a product's or a loop row that holds none. <!-- src: plugins/bfb-elements-pro/elements/buy-now.php:87-98 -->
- **A variable product in a loop needs the card form.** Without Product cards' swatches on the Add to cart in the same row there is nothing to choose with: with JavaScript the press opens the product page, without it the press does nothing. <!-- src: src/elements/shop-buy/shop-buy.js:28-37 ; docs/elements/buy-now.md "Limits" -->
- **Not inside Bricks' Products element.** It prints its own cards, so the button cannot stand in them; build the cards with a query loop instead. <!-- src: docs/elements/buy-now.md "Limits" -->
- **It waits with the add button.** On a variable product's page it stays `disabled` until a variation is chosen, mirroring WooCommerce's own classes on the add button; on a card it stays pressable and says what is missing. <!-- src: src/elements/shop-buy/shop-buy.js:50-54 -->
- **This item alone sets the cart aside.** `takes: "alone"` stashes the cart's lines and coupons in WooCommerce's session and empties the cart, so the checkout holds this item. They come back on the cart page or after the order, checked again for stock; a failed press puts them straight back; they last as long as the session, 48 hours. <!-- src: plugins/bfb-elements-pro/includes/shop/class-buy-now.php:233-337 -->
- **A simple product takes the page's quantity only with an Add to cart there.** Joined to Bricks' Add to cart it posts that form's quantity; with no Add to cart on the page, and always in a loop, it posts quantity 1 from its own form. <!-- src: plugins/bfb-elements-pro/includes/shop/class-buy-now.php:192-216 -->
- **The look is all on the Style tab.** The element has no look controls and no margin; the Add to cart's Buttons controls (`bfbeShopRowHeight`, `bfbeShopRowWide`) never reach it, since it stands outside the form. Without a Style setting it takes the theme's `.button`. <!-- src: src/elements/shop-buy/shop-buy.css:7-9 ; plugins/bfb-elements/includes/shop/class-product-page.php:243 ; docs/elements/buy-now.md "Buy now" -->
- **It works without JavaScript.** It is a form post; with no variation chosen WooCommerce refuses with its own notice ("Please choose product options"). The canvas button posts nothing. <!-- src: plugins/bfb-elements-pro/includes/shop/class-buy-now.php:7-19 ; plugins/bfb-elements-pro/includes/shop/class-buy-now.php:188 ; docs/elements/buy-now.md "Where it works" -->

## Never do

- Do not place it without the Buying switch on, or on a page that is not a product's.
- Do not put it inside Bricks' Products element's cards; use a query loop with Bricks' Add to cart.
- Do not put a card's Buy Now in another looping element than the Add to cart it should join.
- Do not leave a variable product's card without `bfbeShopCardSwatches` on its Add to cart when it carries a Buy Now.
- Do not style it through the Add to cart's `bfbeShopRow*` controls; use its own Style tab.
- Do not give it a `_cssId` to wire it; it joins by the product.
