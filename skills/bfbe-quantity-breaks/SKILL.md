---
name: bfbe-quantity-breaks
description: "Use when showing tiered or bulk prices as a price-by-quantity table on a product page, its current row following the quantity and the chosen variation (BFB Quantity Breaks, `bfbe-quantity-breaks`). Read before writing its settings."
---

# BFB Quantity Breaks (`bfbe-quantity-breaks`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-quantity-breaks.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/quantity-breaks/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Table (`bfbeTable`)
Styling only, every key in the schema file: `headTypography`, `headBackground`, `cellTypography`, `cellPadding`, `numberAlign`, `line`, `currentBg`, `currentColor`.
<!-- bfbe:generated:end -->

## Rendered DOM

The element's root is the table itself:

```html
<table id="brxe-{id}" class="brxe-bfbe-quantity-breaks bfbe-qb" data-bfbe-qb='{"rows":[…],"base":44,"ratio":1,…}' data-bfbe-qb-product="123">
  <caption class="bfbe-sr">Price by quantity</caption>
  <thead><tr><th scope="col">Quantity</th><th scope="col">Price per item</th><th scope="col">You save</th></tr></thead>
  <tbody>
    <tr data-bfbe-qb-from="1" aria-current="true"><th scope="row">1 to 2</th><td data-bfbe-qb-price>44,00 €</td><td data-bfbe-qb-save></td></tr>
    <tr data-bfbe-qb-from="3"><th scope="row">3 to 5</th><td data-bfbe-qb-price>39,60 €</td><td data-bfbe-qb-save>10% off</td></tr>
    <tr data-bfbe-qb-from="6"><th scope="row">6 or more</th><td data-bfbe-qb-price>35,20 €</td><td data-bfbe-qb-save>20% off</td></tr>
  </tbody>
</table>
```

- The first row runs from 1 to the first break at the full price; each saved break adds a row. A fixed price row's saving reads "Save 3,00 € each", empty when nothing is saved.
- `data-bfbe-qb` carries the rule, the product's own price, the shown-price ratio (tax), each variation's price and WooCommerce's money format; the script draws from it.
- State: `aria-current="true"` on the row the quantity falls in, moved by the script; the stylesheet fills that row and adds a small arrow after its first cell (`th::after`).
- Where controls write: `headTypography` and `headBackground` to `thead th`; `cellTypography` to `td` and `tbody th`; `cellPadding` to every `th` and `td`; `numberAlign` to the price cells and their headers; `line` to each cell's bottom border; `currentBg` and `currentColor` to the current row's cells.
- The stylesheet sets `.bfbe-qb` to the full width with collapsed borders. Bricks' Style tab writes the table's margin, width, background, outer border and shadow.
- In the builder, a product with no breaks shows a sample (from 3, 10% off; from 6, 20% off) with the note as a visible `caption.bfbe-notice`.

## Wiring to other elements

- **It follows the product's own Add to cart form**, found by the product's id wherever each stands: the form's `bfbe-cart-{id}` id, its `data-product_id`, or its `add-to-cart` value. No class or id is needed on either.
- It listens to the form's quantity: typing, changes and presses on Bricks' − and + steppers.
- **The chosen variation** comes from the Variation data feature's follower (`bfbe:shop:variation` on `document.body`); the table redraws from that variation's price by the same rule, and a reset goes back.
- **The price per item beside the quantity** is not this element: it is Bricks' Add to cart, group BFB Quantity breaks, **Show** `bfbeShopQbEach` (skill `bfbe-shop-add-to-cart`). Both read the same rule.
- **The rule** lives on the product edit screen (Product data, tab Quantity breaks) or on BFB Elements, Shop, card Quantity breaks by category. The cart line is priced from the same rows on the server.
- Nothing targets it. See `bfbe-shop` for the switches.

## Verified patterns

**The table under the price it lowers.** From the 2.4 site's demo shop, template "Fernhouse: product page" (`bfb-demo-product`). Small capitals for the header on a tint, roomy cells, a tinted current row, and the demo's rounded outer border. Further down the same summary column, Bricks' Add to cart shows the price per item. Trimmed: the demo's colour variables and the summary's other elements.

```json
{
  "name": "block",
  "settings": { "_rowGap": "16px" },
  "children": [
    { "name": "product-price", "settings": {} },
    {
      "name": "bfbe-quantity-breaks",
      "settings": {
        "headTypography": { "font-size": "12px", "font-weight": "700", "color": { "hex": "#667085" }, "text-transform": "uppercase", "letter-spacing": "0.06em" },
        "headBackground": { "hex": "#f7f8fa" },
        "cellTypography": { "font-size": "14px", "font-weight": "600", "color": { "hex": "#101828" } },
        "cellPadding": { "top": "10", "right": "14", "bottom": "10", "left": "14" },
        "line": { "hex": "#e9ecf1" },
        "currentBg": { "hex": "#f0ecff" },
        "currentColor": { "hex": "#101828" },
        "_width": "100%",
        "_border": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "14", "right": "14", "bottom": "14", "left": "14" } },
        "_overflow": "hidden"
      }
    },
    { "name": "product-add-to-cart", "settings": { "bfbeShopQbEach": true } }
  ]
}
```

**The table in another column than the form.** From the template "Shop P5a: single product" (`bfbe-shop-product-p5a`), the block "Elsewhere" in the gallery's column, with a BFB Buy Now under it. The table still moves its current row with the summary's quantity, since it finds the form by the product.

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

## Gotchas

- **No rows, no table.** A product without breaks of its own or from a category prints nothing on the page; the builder's sample is there only to style by. <!-- src: plugins/bfb-elements-pro/elements/quantity-breaks.php:147-156 -->
- **It needs the Quantity breaks switch** (`shop-quantity-breaks`, BFB Elements, Elements); off, the canvas says so and the page prints nothing. <!-- src: plugins/bfb-elements-pro/elements/quantity-breaks.php:136 -->
- **Place it on a product template.** It reads the page's product and follows that product's form; with no such form on the page the table stays as the server drew it. <!-- src: plugins/bfb-elements-pro/elements/quantity-breaks.php:141 ; src/elements/shop-quantity-breaks/shop-quantity-breaks.js:45-52 ; docs/elements/quantity-breaks.md "Limits" -->
- **Variation prices follow only with Variation data on.** The redraw waits for the follower's event; with that switch off a variable product's table keeps the price WooCommerce shows before a choice, the lowest variation's. <!-- src: plugins/bfb-elements-pro/includes/shop/class-quantity-breaks.php:416-419 ; plugins/bfb-elements-pro/includes/shop/class-variation.php:37-40 ; docs/elements/shop-quantity-breaks.md "On the product page" -->
- **Without JavaScript it is the server's table.** One item, the first row current; the cart is still right, as the server prices every line from the saved rows. <!-- src: docs/elements/quantity-breaks.md "What it shows" -->
- **The highest break reached applies.** With breaks at 3 and 6, five items take the 3 row; rows below 2, percentages of 0 or above 100 and negative prices are dropped on save. <!-- src: docs/elements/shop-quantity-breaks.md "The rule" -->
- **A product's own rows win.** A category rule applies only where the product has none, and the first listed category the product is in decides; a child category counts as its parent. <!-- src: plugins/bfb-elements-pro/includes/shop/class-quantity-breaks.php:90-111 -->
- **The current row carries an arrow you cannot switch off.** The stylesheet adds a faint left arrow after the current row's first cell and makes the row bold; `currentBg` and `currentColor` restyle it but keep both. <!-- src: src/elements/shop-quantity-breaks/shop-quantity-breaks.css:10-11 -->
- **Prices are as shown.** In a shop that shows prices with tax, every number is WooCommerce's shown price, the one the cart line shows. <!-- src: plugins/bfb-elements-pro/includes/shop/class-quantity-breaks.php:357-366 ; docs/elements/quantity-breaks.md "What it shows" -->

## Never do

- Do not place it outside a product template, or on a page without the product's Add to cart.
- Do not look for the price per item here; set `bfbeShopQbEach` on Bricks' Add to cart.
- Do not count on variation prices without the Variation data switch on.
- Do not wire it with a class or an id; it finds the form by the product.
