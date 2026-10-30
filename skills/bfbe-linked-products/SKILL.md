---
name: bfbe-linked-products
description: "Use when separate products sold as one family (one product per colour) should show as swatches that link to each other, on a product page or a card (BFB Linked Products, `bfbe-linked-products`). Read before writing its settings."
---

# BFB Linked Products (`bfbe-linked-products`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-linked-products.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/linked-products/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Linked products (`bfbeLinked`)
- `linkedBy` (select) **Linked by**: options: `field` The Linked products field (default), `attribute` A shared attribute
- `attribute` (select) **Attribute**: options: `pa_colour` Colour, `pa_material` Material, `pa_size` Size, `pa_warmth` Warmth. Its swatch colours the links.
- `label` (text) **Label**: placeholder The attribute name; dynamic data accepted
Styling, in the schema file: `labelTypography`, `currentTypography`, `swatchSize`, `gap`, `swatchBorder`, `currentColor`.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<div id="brxe-{id}" class="brxe-bfbe-linked-products bfbe-linked">
  <span class="bfbe-linked__label">Colour: <span class="bfbe-linked__current">Ink</span></span>
  <ul class="bricks-variation-swatches bricks-swatch-color bfbe-linked__list">
    <li class="bfbe-linked__item bricks-swatch-selected" data-value="ink" data-balloon="Oxford Shirt, Ink">
      <a class="bricks-swatch-button bfbe-linked__link" href="…/oxford-shirt-ink/" aria-current="page">
        <span aria-hidden="true" style="background-color: #1f2a44"></span><span class="bfbe-sr">Oxford Shirt, Ink</span></a>
    </li>
    <li class="bfbe-linked__item" data-value="sand" data-balloon="Oxford Shirt, Sand">…</li>
  </ul>
</div>
```

- Plain links in Bricks' swatch classes: `bricks-swatch-{color|image|label}` on the list follows the attribute's swatch type in Bricks' settings. No script.
- The face is, in order: the term's swatch colour (`span[aria-hidden]`), else the term's swatch picture (image type), else the other product's own picture (`img`, thumbnail), else the term's or the product's name in `span.bfbe-linked__word`.
- State: the current product's item takes `bricks-swatch-selected` and its link `aria-current="page"`; the stylesheet rings it.
- Where controls write: `labelTypography` to `.bfbe-linked__label`, `currentTypography` to `.bfbe-linked__current`, `swatchSize` to `--bfbe-linked-size` on the root (32px; the face inside follows it), `gap` to `.bfbe-linked__list`, `swatchBorder` to `.bfbe-linked__item`, `currentColor` to `--bfbe-linked-on` (the ring and border, the accent until set).
- The root is a flex column with a 6px gap; its margin and place are Bricks' Style tab's.

## Wiring to other elements

- **The family comes from the products, not from other elements.** **Linked by** `linkedBy: "field"` reads the product's own Linked products field (product edit screen, Linked Products tab, WooCommerce's product search, saved as `_bfbe_linked_products`). `linkedBy: "attribute"` finds the products in the same categories whose other attributes all match and whose value of **Attribute** (`attribute`) differs.
- **Bricks' swatch settings colour it.** The colour or picture is the term's in WooCommerce, Attributes, under Bricks' swatch type, the same values Bricks' own Add to cart swatches use.
- **Product context.** It reads the page's product, or the loop's in a query loop row, so it works on a product template and on cards.
- It is the separate-products counterpart of a variation picker: for variations of one product, use Bricks' Add to cart and `bfbe-shop-add-to-cart`.
- Stands alone otherwise; nothing targets it and it targets nothing. See `bfbe-shop`.

## Verified patterns

**Other colours as their own products, picked by hand.** From the 2.4 site's demo shop, template "Fernhouse: product page" (`bfb-demo-product`), under the price. The field's family, coloured by Colour, labelled "Also in", with round 30px swatches ringed in ink for the current one. Shown in the summary column it sits in; trimmed: the demo's colour variables and the summary's other elements.

```json
{
  "name": "block",
  "settings": { "_rowGap": "16px" },
  "children": [
    { "name": "product-title", "settings": { "tag": "h1" } },
    { "name": "product-price", "settings": {} },
    {
      "name": "bfbe-linked-products",
      "settings": {
        "linkedBy": "field",
        "attribute": "pa_colour",
        "label": "Also in",
        "labelTypography": { "font-size": "14px", "font-weight": "700", "color": { "hex": "#101828" } },
        "currentTypography": { "font-size": "14px", "font-weight": "500", "color": { "hex": "#667085" } },
        "swatchSize": "30px",
        "gap": "8px",
        "swatchBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "999", "right": "999", "bottom": "999", "left": "999" } },
        "currentColor": { "hex": "#101828" }
      }
    }
  ]
}
```

**A family found by a shared attribute.** From the template "Shop P2: single product (linked by the shared Colour attribute …)" (`bfbe-shop-product-p2-b`), the summary column. New colours join by themselves when they share every other attribute and a category; the label is the attribute's name. Trimmed: the template's badges and its Add to cart settings.

```json
{
  "name": "block",
  "settings": { "_rowGap": "16px" },
  "children": [
    { "name": "product-title", "settings": { "tag": "h1" } },
    { "name": "product-price", "settings": {} },
    { "name": "bfbe-linked-products", "settings": { "linkedBy": "attribute", "attribute": "pa_colour" } },
    { "name": "product-stock", "settings": {} },
    { "name": "product-add-to-cart", "settings": {} }
  ]
}
```

## Gotchas

- **The field is one way.** Each product shows the products its own field lists, so a family of four needs the other three listed on every one of them. <!-- src: plugins/bfb-elements-pro/includes/shop/class-cards.php:769-773 -->
- **The current product always comes first.** Its swatch leads the list and the others follow (in the field's order, or by title for an attribute), so the order changes from page to page. <!-- src: plugins/bfb-elements-pro/includes/shop/class-cards.php:878 ; plugins/bfb-elements-pro/includes/shop/class-cards.php:788 -->
- **A shared attribute is strict.** Every other attribute and its values must match exactly, the products must share a category, and only the first 80 published products of those categories are read. One extra size on one product leaves it out. <!-- src: plugins/bfb-elements-pro/includes/shop/class-cards.php:781-806 -->
- **No family, no element.** A product with no linked products prints nothing on the page; the builder says so. Only published products count. <!-- src: plugins/bfb-elements-pro/elements/linked-products.php:157-161 ; plugins/bfb-elements-pro/includes/shop/class-cards.php:773 -->
- **Colour swatches need Bricks' Variation swatches setting.** Without it (Bricks, Settings, WooCommerce) the type reads as words, so each link shows the other product's picture, or its name when it has none. <!-- src: plugins/bfb-elements-pro/includes/shop/class-cards.php:691 ; plugins/bfb-elements-pro/includes/shop/class-cards.php:899-909 -->
- **Attribute empty takes the first with colour or picture swatches**, else the product's first global attribute; with none the label reads "Also available" and the current value is the product's name. <!-- src: plugins/bfb-elements-pro/includes/shop/class-cards.php:846-860 ; plugins/bfb-elements-pro/includes/shop/class-cards.php:879 -->
- **Every link loads another page.** Separate products are separate pages, unlike a variation, which changes in place. <!-- src: docs/elements/linked-products.md "Limits" -->
- **The Product cards switch is not needed.** The field and the element work with or without `shop-cards`; the element needs WooCommerce only. <!-- src: plugins/bfb-elements-pro/includes/shop/class-cards.php:57-60 ; plugins/bfb-elements-pro/elements/linked-products.php:146 -->

## Never do

- Do not fill the field on one product of a family and expect the others to show it.
- Do not use `linkedBy: "attribute"` for products that differ in more than the one attribute.
- Do not use it for the variations of one product; use Bricks' Add to cart.
- Do not count on colour swatches with Bricks' Variation swatches setting off.
