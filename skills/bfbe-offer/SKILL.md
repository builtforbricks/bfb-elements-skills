---
name: bfbe-offer
description: "Use when adding an order bump, a one-time offer or an add-on checkbox to the cart, checkout or any page with `bfbe-offer`: one product at a set price or a percent off, shown by cart conditions, ticked in and out of the cart."
---

# BFB Offer (`bfbe-offer`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-offer.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/offer/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 0.44 KB, JS 1.08 KB (gzipped), no dependencies, loaded only on pages that use it.

## Structure
Nestable. Its own children: `bfbe-offer-checkbox`.
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-offer",
    "settings": {},
    "children": [
        {
            "name": "image",
            "settings": {
                "image": {
                    "useDynamicData": "{bfbe_offer_image}",
                    "size": "woocommerce_thumbnail"
                },
                "_width": "96px"
            }
        },
        {
            "name": "block",
            "settings": {
                "_rowGap": "8px",
                "_flexGrow": "1"
            },
            "children": [
                {
                    "name": "heading",
                    "settings": {
                        "text": "One-time offer",
                        "tag": "h4"
                    }
                },
                {
                    "name": "bfbe-offer-checkbox",
                    "settings": {}
                }
            ]
        }
    ]
}
```

`bfbe-offer-checkbox` (BFB Offer Checkbox), 57 controls, schema `../bfbe-schemas/references/elements/bfbe-offer-checkbox.json`.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Offer (`bfbeOffer`)
- `product` (select) **Product**: placeholder Pick a product
- `priceMode` (select) **Price**: options: `price` A price (default), `percent` Percent off
- `price` (number) **Offer price**: placeholder 9.90; only when `priceMode` is not `percent`
- `percent` (number) **Percent off**: placeholder 15; only when `priceMode` is `percent`. Off the current price, 1 to 99.
- `updateWord` (text) **Button**: placeholder Update

### Show when (`bfbeWhen`)
- `minTotal` (number) **Cart total at least**: placeholder 0
- `withProduct` (text) **A product in the cart**: placeholder Id or SKU
- `withCategory` (text) **A category in the cart**: placeholder Category slug

### Card (`bfbeCard`)
Styling only, every key in the schema file: `chosenBorder`, `chosenBackground`, `chosenShadow`.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<form id="brxe-{id}" class="brxe-bfbe-offer bfbe-offer bfbe-offer--js" method="post" data-bfbe-offer="{post}:{element}"
      data-bfbe-shop-need="cart" hidden>
  <input type="hidden" name="bfbe_shop_act" value="offer_add"> <!-- + _bfbe_back, post, el; _bfbe_nonce when signed in -->
  <!-- the children, Bricks' own elements and BFB Offer Checkbox -->
  <img class="brxe-image" src="{the offer product's picture}" alt="…">
  <div class="brxe-block">
    <h4 class="brxe-heading">Save 15%</h4>
    <label class="brxe-bfbe-offer-checkbox bfbe-offer__choice" for="…">
      <input type="checkbox" class="bfbe-offer__box bfbe-tick" name="on" value="1">
      <span class="bfbe-offer__sentence">Add <span class="bfbe-offer__name">Woven Belt</span> for
        <span class="bfbe-offer__price">29,00 €</span> instead of <s class="bfbe-offer__regular">39,00 €</s></span>
    </label>
  </div>
  <button type="submit" class="bfbe-offer__update">Update</button>
</form>
```

- The root is a real `form`, `display: flex; align-items: center` with the tokens' gap: the children sit in a row as they come. It carries `hidden` while the offer's conditions do not hold; the script lifts or sets it after every live cart answer. In the canvas it always shows.
- `bfbe-offer--js` is added by the script, which hides `.bfbe-offer__update` and posts on each change of a `.bfbe-offer__box`. The Update button (**Button** `updateWord`) is the no-script path and is not printed in the canvas.
- An offer still missing its product or price in the canvas adds `bfbe-empty` and a notice, and its children print a sample product.
- Where controls write: the Card group's **Border**, **Background** and **Shadow** (`chosenBorder`, `chosenBackground`, `chosenShadow`) write the root while ticked, `&:has(.bfbe-offer__box:checked)`. On the checkbox, `nameTypography`, `priceTypography` with `priceColor`, `regularTypography` with `regularColor` and `percentTypography` reach the sentence's spans; `boxColor`, `boxSize` and the drawn box's controls reach `.bfbe-offer__box`. Everything else is Bricks' Style tab: the root draws the card, the checkbox's root is the label row.

## Wiring to other elements

- **Bricks' own elements print the offer through tags.** Inside a BFB Offer, **Offer: the product name** `{bfbe_offer_name}`, **the offer price** `{bfbe_offer_price}`, **the regular price** `{bfbe_offer_regular}`, **the percent off** `{bfbe_offer_percent}` ("15%"), **the product link** `{bfbe_offer_link}` and **the product image** `{bfbe_offer_image}` (an Image element's `useDynamicData`) read the offer around them. See `bfbe-shop-tags-and-conditions`.
- **BFB Offer Checkbox is the tick and its sentence**, anywhere inside the offer, in any container. **Sentence** `sentence` takes `{product}`, `{price}`, `{regular}` (struck through) and `{percent}`. Schema: `../bfbe-schemas/references/elements/bfbe-offer-checkbox.json`.
- **The headline is a Bricks Heading** inside the offer: "Save {bfbe_offer_percent}" says the percent off.
- **The cart page.** Place the offer beside Bricks' Cart items (`woocommerce-cart-items`), never inside it: after a tick the script reloads that cart's form and totals, or runs WooCommerce's `update_checkout` on the checkout. It also swaps the shop's cart fragments, so Bricks' Mini cart follows.
- **A popup**: an offer in a Bricks popup works where the popup's conditions include the page it opens on, the mini cart's popup included.
- See `bfbe-shop` for the shop's switches. For your own CSS give the offer a class in `_cssClasses`, never `_cssId`: component instances share ids.

## Verified patterns

**On the cart page, beside Bricks' Cart items** (the 2.4 demo shop's cart template in `dev/demo/shop/15-templates-buy.php`, "a candle at 9, from a cart of 40", with the dev site's candles; the fixture template `bfbe-shop-cart` places its offer the same way). **Offer price** `price` sets the line's price; **Cart total at least** `minTotal` shows it from 40. The root draws the card with Bricks' Style tab; the image and the Block sit in the root's own row.

```json
{
  "name": "block",
  "settings": { "_rowGap": "24px" },
  "children": [
    { "name": "woocommerce-cart-items", "settings": {} },
    {
      "name": "bfbe-offer",
      "settings": {
        "product": "79103", "price": "9.00", "minTotal": "40", "_cssClasses": "cart-offer", "_width": "100%",
        "_padding": { "top": "20", "right": "20", "bottom": "20", "left": "20" },
        "_background": { "color": { "hex": "#f0ecff" } },
        "_border": { "radius": { "top": "20", "right": "20", "bottom": "20", "left": "20" } }
      },
      "children": [
        { "name": "image", "settings": { "image": { "useDynamicData": "{bfbe_offer_image}", "size": "woocommerce_thumbnail" }, "_width": "88px", "_aspectRatio": "1 / 1", "_objectFit": "cover", "_flexShrink": "0" } },
        { "name": "block", "settings": { "_rowGap": "6px", "_flexGrow": "1", "_flexShrink": "1", "_flexBasis": "0", "_widthMin": "0" }, "children": [
          { "name": "heading", "settings": { "text": "Just for this order", "tag": "h4" } },
          { "name": "bfbe-offer-checkbox", "settings": { "sentence": "Add a {product} for {price} instead of {regular}" } }
        ] }
      ]
    }
  ]
}
```

**A percent off, said in the headline, marked while ticked** (fixture page `fixture-shop-q4-offer`, `.q4-offer`, with the demo's Chosen look from `dev/demo/shop/20-pages.php`). `priceMode: "percent"` with `percent` takes 15% off the product's current price; the Heading's `{bfbe_offer_percent}` and the sentence's `{percent}` print "15%". `chosenBorder` and `chosenBackground` show only while the box is ticked.

```json
{
  "name": "bfbe-offer",
  "settings": {
    "product": "79348", "priceMode": "percent", "percent": "15", "_cssClasses": "q4-offer",
    "chosenBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#6e44ff" } },
    "chosenBackground": { "color": { "hex": "#f0ecff" } }
  },
  "children": [
    { "name": "image", "settings": { "image": { "useDynamicData": "{bfbe_offer_image}", "size": "woocommerce_thumbnail" }, "_width": "96px" } },
    { "name": "block", "settings": { "_rowGap": "8px", "_flexGrow": "1" }, "children": [
      { "name": "heading", "settings": { "text": "Save {bfbe_offer_percent}", "tag": "h4" } },
      { "name": "bfbe-offer-checkbox", "settings": { "sentence": "Add {product} for {price} instead of {regular} ({percent} off)" } }
    ] }
  ]
}
```

The product ids are the dev site's; read the target site's simple products first.

## Gotchas

- **`_display` on the root shows an offer the cart does not qualify for.** Bricks writes it on the element's id, which outranks `.bfbe-offer[hidden]`: measured, a hidden offer stayed on screen as `display: flex`. Leave `_display` unset (the root is a flex row already) and stack children in a Bricks Block inside. <!-- src: src/elements/offer/offer.css:3-4 ; dev/demo/shop/lib.php:869 ; measured 2026-10-30 on bfb-elements-24.local /bfb-demo-shop/your-cart/ with the offer's product in the cart: hidden true, display flex, 118px tall -->
- **A simple product and a price, or nothing.** **Product** `product` takes a simple product, or a variation by its id; variable, grouped and external products are refused. With no **Offer price** `price` (or no **Percent off** `percent`, 1 to 99, with `priceMode: "percent"`) the site prints nothing and the canvas a notice. <!-- src: plugins/bfb-elements-pro/includes/shop/class-offer.php:153-205 ; plugins/bfb-elements-pro/elements/offer.php:232-241 -->
- **Every condition that is set must hold.** **Cart total at least** `minTotal` (after coupons, the offer's own line left out), **A product in the cart** `withProduct` (an id or a SKU) and **A category in the cart** `withCategory` (a slug). The offer never shows while its product is already in the cart on its own, and its line goes when the conditions stop holding. <!-- src: plugins/bfb-elements-pro/includes/shop/class-offer.php:249-330 ; docs/elements/offer.md "Show when" -->
- **The canvas always shows it.** The builder draws the offer whatever the cart; the page prints it with `hidden` and the script asks the server again after every live answer, so a cached page still decides right. <!-- src: plugins/bfb-elements-pro/elements/offer.php:246-254 ; src/elements/offer/offer.js:33-51 -->
- **Tags preview the page's first offer.** In the canvas each child renders on its own, so a `{bfbe_offer_*}` tag reads the first BFB Offer saved on the page (or a sample: the shop's first simple product at 20% off). A second offer's children preview the first one's product there; the page is right. Outside an offer the tags print nothing. <!-- src: plugins/bfb-elements-pro/includes/shop/class-offer.php:392-452 ; plugins/bfb-elements/includes/abstract-element.php:505-521 -->
- **The checkbox reads its own parent.** In the canvas BFB Offer Checkbox reads its offer's saved settings, a sample while it has none, and is disabled. Outside an offer it prints nothing on the page and "Place BFB Offer Checkbox inside a BFB Offer." in the builder. <!-- src: plugins/bfb-elements-pro/elements/offer-checkbox.php:149-162 ; plugins/bfb-elements-pro/includes/shop/class-offer.php:478-482 -->
- **An offer with no children still works.** Saved empty, it prints the tick and its sentence on their own, with a builder note asking for the picture, a headline and BFB Offer Checkbox. <!-- src: plugins/bfb-elements-pro/elements/offer.php:270-275 -->
- **The headline and the look moved to children.** `headline`, `sentence`, the card's Layout and the box and word controls were removed from `bfbe-offer` on 29 October: the headline is a Bricks Heading, the sentence and the box are BFB Offer Checkbox's. <!-- src: docs/SHOP-LABELS-2.0.0.md "BFB Offer (`bfbe-offer`)" layout round ; plugins/bfb-elements-pro/elements/offer.php:12-15 -->
- **It is a form.** Keep it out of Bricks' Cart items, a Bricks Form or any other form: a form inside a form is dropped by the browser. The cart fixtures place it beside the cart's form. <!-- src: plugins/bfb-elements-pro/elements/offer.php:260 ; dev/fixtures/shop-p7b.php:250-265 ; plugins/bfb-elements-pro/elements/bought-together.php:217-218 -->
- **Where it is read from matters.** The offer is read only from a page the visitor may see: a draft offers nothing, a popup needs its conditions to include the page it opens on, and one inside a query loop is not decided per row. One product per element. <!-- src: docs/elements/offer.md "Limits" ; plugins/bfb-elements-pro/includes/shop/class-offer.php:101-115 -->

## Never do

- Do not set `_display` on `bfbe-offer`; lay its children out in a Bricks Block inside it.
- Do not pick a variable, grouped or external product, or leave the price (or `percent`) empty.
- Do not set `headline`, `sentence` or box keys on `bfbe-offer`; use a Bricks Heading and BFB Offer Checkbox.
- Do not place a BFB Offer inside Bricks' Cart items, a Bricks Form or another form.
- Do not use the `{bfbe_offer_*}` tags or BFB Offer Checkbox outside a BFB Offer.
- Do not place an offer in a query loop to offer each row's product.
