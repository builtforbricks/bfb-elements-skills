---
name: bfbe-bought-together
description: "Use when adding a frequently bought together set, complete the look or a set discount to a product page with `bfbe-bought-together`: ticked companions from picks, upsells, cross-sells or past orders, a live total and one button that adds them."
---

# BFB Bought Together (`bfbe-bought-together`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-bought-together.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/bought-together/

## What it is
Two to four products that go together, this one first, each with a real checkbox, its image, its name and its price, a total of the ticked ones, and one button that adds them all. Companions are picked by hand, taken from WooCommerce's upsells or cross-sells, or drawn from your own paid orders. It is a nestable form whose parts you place in Bricks' own containers, and an optional set discount comes off once the set's own button has added it, while the whole set is in the cart, worked out on your server.

**Not for:** Not for quantities: it adds one of each product, and the quantity is changed in the cart. For an offer where the shopper picks any three from a category, use BFB Bundle Builder.

**Costs a page:** CSS 1.43 KB, JS 1.14 KB (gzipped), plus shop-live, loaded only on pages that use it.

**Nestable:** yes · **In a query loop:** no · **Dynamic data:** no · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Nestable. Its own children: `bfbe-bought-together-products`, `bfbe-bought-together-total`.
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-bought-together",
    "settings": {},
    "children": [
        {
            "name": "bfbe-bought-together-products",
            "settings": {}
        },
        {
            "name": "bfbe-bought-together-total",
            "settings": {}
        },
        {
            "name": "button",
            "settings": {
                "text": "Add the ticked products",
                "tag": "button",
                "style": "primary",
                "_cssClasses": "bfbe-bt__add",
                "_attributes": [
                    {
                        "id": "bfbebt",
                        "name": "type",
                        "value": "submit"
                    }
                ]
            }
        }
    ]
}
```

`bfbe-bought-together-products` (BFB Bought Together Products), 93 controls, schema `../bfbe-schemas/references/elements/bfbe-bought-together-products.json`.

`bfbe-bought-together-total` (BFB Bought Together Total), 49 controls, schema `../bfbe-schemas/references/elements/bfbe-bought-together-total.json`.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Set (`bfbeSet`)
- `product` (select) **Product**: placeholder The product of the page. The set's own product, ticked and fixed; the product of the page unless chosen, so in a product template every product gets its own set.
- `source` (select) **Companions from**: options: `pick` Picked here (default), `upsells` Its upsells, `cross` Its cross-sells, `orders` Bought with it in your orders. Picked here (the default), Its upsells, Its cross-sells, or Bought with it in your orders, the products most often in the same paid order, kept for an hour and counted again when an order's status changes.
- `products` (select) **Companions**: placeholder Pick up to three products; only when `source` is not `upsells` or `cross` or `orders`. The products to offer, picked in the panel, with Picked here.
- `most` (number) **Products in the set**: placeholder 3. 2 to 4, this one included, 3 unless set. A product that cannot be bought now drops out and the next takes its place.
- `variable` (select) **Other variable products**: options: `choose` With a select of their options (default), `leave` Left out. With a select of their options (the default) or Left out.
- `unticked` (checkbox) **Start the others unticked**. For a set that is a suggestion rather than a deal; the companions start ticked otherwise.
- `discount` (number) **Set discount (%)**: placeholder 0. 0 to 90, none unless set, taken off while every product of the set is in the cart.

## What it guarantees for accessibility (do not undo)
- Each product has a real checkbox named by its product, ticked with a press or the space bar; the set's own product is ticked and cannot be unticked.
- The total is an output element, so its new sum is read out once as the ticks change.
- A variable product's select is named for its product (Options for ...) and set aside while that product is unticked.
- After the add one sentence says what happened, such as Added to your cart: Oak Serving Board, Stoneware Mug Set.
- Under reduced motion the tick on the picture changes without a transition.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<form id="brxe-{id}" class="brxe-bfbe-bought-together bfbe-bt" method="post" data-bfbe-bt='{"fmt":{…}}' data-bfbe-shop-need="cart">
  <input type="hidden" name="bfbe_shop_act" value="bought_together_add"> <!-- + _bfbe_back, post, el; _bfbe_nonce when signed in -->
  <!-- BFB Bought Together Products, anywhere inside -->
  <ul class="brxe-bfbe-bought-together-products bfbe-bt__list bfbe-bt__list--list bfbe-bt__list--tick-badge bfbe-bt__list--pic-start">
    <li class="bfbe-bt__item bfbe-bt__item--this" data-bfbe-bt-price="29">
      <input type="hidden" name="ids[]" value="123">
      <label class="bfbe-bt__label" for="…"><span class="bfbe-bt__media"><img …><input type="checkbox" class="bfbe-bt__box bfbe-tick" checked disabled></span>
        <span class="bfbe-bt__text"><span class="bfbe-bt__this">This item</span> <span class="bfbe-bt__name">…</span> <span class="bfbe-bt__price">…</span></span></label>
    </li>
    <li class="bfbe-bt__item bfbe-bt__item--choice is-off" data-bfbe-bt-price="24">
      <label …><span class="bfbe-bt__media"><img …><input type="checkbox" class="bfbe-bt__box bfbe-tick" name="ids[]" value="456"></span>…</label>
      <select class="bfbe-bt__var" name="v_456" aria-label="Options for …" disabled><option value="789" data-bfbe-bt-price="24">…</option></select>
    </li>
  </ul>
  <!-- BFB Bought Together Total -->
  <div class="brxe-bfbe-bought-together-total bfbe-bt__total">
    <p class="bfbe-bt__line"><span class="bfbe-bt__total-word">Total for the ticked products</span> <output class="bfbe-bt__sum">…</output></p>
    <p class="bfbe-bt__deal">10% off the set when you buy them all.</p>
    <p class="bfbe-bt__note" hidden></p>
  </div>
  <button class="brxe-button bricks-button bricks-background-primary bfbe-bt__add" type="submit">Add the ticked products</button>
</form>
```

- The parent's root is a real `form`, a flex column (`gap: var(--bfbe-gap)`) until Bricks' Style tab lays it out. A child directly in it with `bfbe-bt__add` aligns to the start.
- The set's own product is ticked and disabled, carried by a hidden `ids[]`. **Tick** `tick: "badge"` puts the box inside `.bfbe-bt__media` as a round badge and hides it on that product; `tick: "box"` puts a checkbox before the label in a column of its own.
- The script toggles `is-off` on unticked cards (picture, words and select fade to **Unticked opacity** `offOpacity`), disables an unticked product's select, rewrites `.bfbe-bt__price` and `.bfbe-bt__sum` from the `data-bfbe-bt-price` values, and sets `aria-busy="true"` on `.bfbe-bt__add` while it posts. The answer goes into `.bfbe-bt__note`, `hidden` until then.
- Where controls write, on Products: `item*` to `.bfbe-bt__item` (`itemOnBorder` to `:not(.is-off)`), `image*` to `.bfbe-bt__media img`, `cardWidth`, `gap`, `imageWidth` and the badge's colours and sizes to `--bfbe-bt-*` on the list, `select*` to `.bfbe-bt__var`. On Total: `sumTypography`, `dealTypography`, `note*` to their parts. Bricks' Style tab draws each child's root: the list's box, the total's box and its words.

## Wiring to other elements

- **The parent holds the set; the parts print it.** Products and Total find the nearest `bfbe-bought-together` above them and read its settings; the server adds from the parent's saved settings only, never a child's. Place them anywhere inside it, in Bricks' own containers. Schemas: `../bfbe-schemas/references/elements/bfbe-bought-together-products.json`, `../bfbe-schemas/references/elements/bfbe-bought-together-total.json`.
- **BFB Bought Together Products** carries the cards' words and look: **This product** `thisWord`, **Products sit** `layout` (`list` or `row`, with **Narrowest card** `cardWidth`), **Picture** `picture` (`start` or `top`), **Tick** `tick` (`badge` or `box`) and the Card, Picture, Tick, Look and Options list controls.
- **BFB Bought Together Total** carries **Total words** `totalWord`, **Discount words** `dealWord` (`%s` is the percentage) and the message's look. It is where the add's sentence shows.
- **The add button is Bricks' Button, found by class.** Put `bfbe-bt__add` in its `_cssClasses`, with `tag: "button"` and the seeded `_attributes` type `submit`. It may sit beside the products or in any container inside the form.
- **The product**: with **Product** `product` unset, the product of the page, so one element in a product template gives every product its set. **Companions from** `source: "upsells"` or `"cross"` reads WooCommerce's Linked Products tab; `"orders"` counts paid orders; `"pick"` reads **Companions** `products`.
- **The cart**: after the add the script swaps the shop's cart fragments and fires WooCommerce's `wc_fragment_refresh`, so Bricks' Mini cart and every live cart figure follow. See `bfbe-shop` for the shop's switches.
- For your own CSS give the parent a class in `_cssClasses`, never `_cssId`: component instances share ids.

## Verified patterns

**On a product template: the product's upsells, the total and the button in a column beside the cards** (the 2.4 site's demo shop, `dev/demo/shop/10-templates.php`, the product template's section "Bought together"; trimmed of the brand's colours and type). The parent is a flex row with `_display: "flex"`, back to a column at `tablet_portrait`; the Block beside the cards holds Total and Button. Use it where the page has a product: outside one, nothing prints but the heading.

```json
{
  "name": "block",
  "settings": { "_rowGap": "20px" },
  "children": [
    { "name": "heading", "settings": { "text": "Goes well with", "tag": "h2" } },
    {
      "name": "bfbe-bought-together",
      "settings": {
        "source": "upsells", "most": 3, "discount": 5, "_cssClasses": "fh-bt",
        "_display": "flex", "_flexDirection": "row", "_alignItems": "center", "_gap": "32px",
        "_flexDirection:tablet_portrait": "column", "_alignItems:tablet_portrait": "stretch"
      },
      "children": [
        { "name": "bfbe-bought-together-products", "settings": { "thisWord": "This piece", "layout": "row", "cardWidth": "270px", "gap": "16px", "itemAlign": "flex-start", "imageWidth": "96px", "_flexGrow": "1", "_flexShrink": "1", "_widthMin": "0" } },
        { "name": "block", "settings": { "_rowGap": "14px", "_alignItems": "flex-start", "_width": "260px", "_flexShrink": "0", "_width:tablet_portrait": "100%" }, "children": [
          { "name": "bfbe-bought-together-total", "settings": { "totalWord": "Together" } },
          { "name": "button", "settings": { "text": "Add all three", "tag": "button", "style": "primary", "_cssClasses": "bfbe-bt__add", "_attributes": [ { "id": "bfbebt", "name": "type", "value": "submit" } ], "_width": "100%" } }
        ] }
      ]
    }
  ]
}
```

**A set picked by hand, on any page, with a set discount** (the 2.4 demo shop's Sets page, `dev/demo/shop/20-pages.php`, "The slow coffee set", with the dev fixture's products from `fixture-shop-bought-together`). **Product** `product` and **Companions** `products` fix the set, so it needs no product page; the total and the button share one wrapping row under the cards. The ids are the dev site's: read the target site's products first.

```json
{
  "name": "bfbe-bought-together",
  "settings": { "product": "79028", "source": "pick", "products": [ "79033", "79073" ], "most": 3, "discount": 10, "_display": "flex", "_flexDirection": "column", "_gap": "20px" },
  "children": [
    { "name": "bfbe-bought-together-products", "settings": { "thisWord": "The set", "layout": "row", "imageWidth": "88px", "gap": "16px", "itemAlign": "flex-start" } },
    { "name": "block", "settings": { "_direction": "row", "_flexWrap": "wrap", "_alignItems": "center", "_columnGap": "24px", "_rowGap": "12px" }, "children": [
      { "name": "bfbe-bought-together-total", "settings": { "totalWord": "All three" } },
      { "name": "button", "settings": { "text": "Add the three", "tag": "button", "style": "primary", "_cssClasses": "bfbe-bt__add", "_attributes": [ { "id": "bfbebt", "name": "type", "value": "submit" } ] } }
    ] }
  ]
}
```

## Gotchas

- **The set lives on the parent, the look on the parts.** `layout`, `tick`, `thisWord`, `totalWord` and the card controls were removed from `bfbe-bought-together` on 29 October and now belong to Products and Total; the parent keeps only the Set group. <!-- src: docs/SHOP-LABELS-2.0.0.md "BFB Bought Together (`bfbe-bought-together`)" layout round ; plugins/bfb-elements-pro/elements/bought-together.php:13-18 -->
- **A set that cannot be made prints nothing.** The product and at least one companion must be published, purchasable, in stock or on back-order, simple or variable; otherwise the site gets no markup and no file, and the canvas a notice. A product never ordered with others has no `orders` set. <!-- src: plugins/bfb-elements-pro/elements/bought-together.php:179 ; plugins/bfb-elements-pro/elements/bought-together.php:196-200 ; plugins/bfb-elements-pro/includes/shop/class-bought-together.php:130-168 ; docs/elements/bought-together.md "Limits" -->
- **Variable companions need one select.** A variation that takes any value of an attribute is left out of the select; a variable product with none left drops out, and `variable: "leave"` skips variable companions. **Products in the set** `most` counts this product, 2 to 4. <!-- src: plugins/bfb-elements-pro/includes/shop/class-bought-together.php:119-123 ; plugins/bfb-elements-pro/includes/shop/class-bought-together.php:171-188 -->
- **The button must be a real submit.** Bricks' Button is a `span` unless `tag: "button"`, and any `link` turns it into an `a`; neither submits the form. Keep the seeded tag and class. <!-- src: themes/bricks/includes/elements/button.php:11 ; themes/bricks/includes/elements/button.php:169-171 ; plugins/bfb-elements-pro/elements/bought-together.php:162-171 -->
- **No form inside the form.** A Bricks Form, Search or Product add to cart, a BFB Advanced Forms form, another set or a Bundle Builder inside it is dropped by the browser on the site; the builder shows "Keep other forms out of this one". <!-- src: plugins/bfb-elements-pro/includes/shop/class-bought-together.php:253-278 ; plugins/bfb-elements-pro/elements/bought-together.php:217-219 -->
- **Without the Total, nobody sees the answer.** The add's sentence and its refusals are written into `.bfbe-bt__note`, which only BFB Bought Together Total prints; without it they go to the shop's visually hidden live region alone. <!-- src: src/elements/bought-together/bought-together.js:51-55 ; src/elements/shop-live/shop-live.js:33 -->
- **The total is before the discount.** `.bfbe-bt__sum` adds the ticked prices as shown; the discount is a "Bought together" fee in the cart, 0 to 90%, only while every product of the set is there, one of each per whole set. The deal line says so. <!-- src: plugins/bfb-elements-pro/includes/shop/class-bought-together.php:235-245 ; plugins/bfb-elements-pro/includes/shop/class-bought-together.php:567-604 ; plugins/bfb-elements-pro/elements/bought-together-total.php:153-159 -->
- **The canvas shows the set as last saved.** Each part renders on its own in the builder and reads its parent from the saved page: save after changing the set. An unsaved parent shows "Save the page to show the set here"; ticks are disabled, the message is a sample, and a press posts nothing. <!-- src: plugins/bfb-elements/includes/abstract-element.php:505-521 ; plugins/bfb-elements-pro/elements/bought-together-products.php:393-396 ; plugins/bfb-elements-pro/elements/bought-together-total.php:160-163 ; src/elements/bought-together/bought-together.js:57-58 -->
- **The parent's layout keys need `_display: "flex"`.** It is not a Bricks container: it takes `_flexDirection`, `_alignItems`, `_justifyContent` and `_gap` with `_display: "flex"`, and has no `_direction`, `_rowGap`, `_columnGap`, wrap or grid template. Nest a Bricks Block for those. <!-- src: themes/bricks/includes/elements/base.php:888-1004 ; plugins/bfb-elements/includes/abstract-element.php:871-884 -->
- **The badge's controls and the checkbox's are apart.** **Mark colour** `markColor`, **Unticked colour** `emptyColor`, **Size** `tickSize` and **Offset** `tickInset` show with `tick: "badge"`; **Checkbox** `boxLook` and its colours only with `tick: "box"`. The set's own product shows no badge. <!-- src: plugins/bfb-elements-pro/elements/bought-together-products.php:261-303 ; src/elements/bought-together/bought-together.css:54 -->

## Never do

- Do not set `layout`, `tick`, `thisWord`, `totalWord` or card keys on `bfbe-bought-together`; set them on its two parts.
- Do not give the add button a `link`, or leave out `tag: "button"` and the class `bfbe-bt__add`.
- Do not place a Bricks Form, Search, Product add to cart, BFB Advanced Forms form, another set or a bundle inside it.
- Do not leave out BFB Bought Together Total where the visitor must see what the add did.
- Do not set `_flexDirection`, `_alignItems` or `_gap` on the parent without `_display: "flex"`; nest a Block for wrapping rows and grids.
- Do not place BFB Bought Together Products or Total outside a `bfbe-bought-together`.
- Do not set `products` unless `source` is `pick`.
