---
name: bfbe-product-layers
description: "Use when a product picture should be built from layers that change as the shopper picks options (a mug's glaze and print, a sofa's fabric and legs), with BFB Product Layers (`bfbe-product-layers`), and when filling a product's BFB Layers tab (`_bfbe_layers`). Read before writing its settings."
---

# BFB Product Layers (`bfbe-product-layers`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.1.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-product-layers.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/product-layers/

## What it is
_The website has no approved words for this yet; the next export after it does fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 0.26 KB, JS 1.03 KB (gzipped), no dependencies, loaded only on pages that use it.

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### View (`bfbeView`)
- `product` (select) **Product**: placeholder The product of the page. Its layer images are on its BFB Layers tab.

### Motion (`bfbeMotion`)
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS
Styling, in the schema file: `duration`, `easingCustom`.
<!-- bfbe:generated:end -->

## Rendered DOM

The layered mug of the demo template with Sage and Fern chosen, trimmed (addresses shortened, one `srcset` shown):

```html
<div id="brxe-abc123" class="brxe-bfbe-product-layers bfbe-layers layermug-picture"
     data-bfbe-layers='{"product":91210,"layers":{"attribute_glaze":{"White":["…white.webp","…"],"Sage":["…sage.webp","…"]},"attribute_print":{"Fern":["…fern.webp","…","…fern-dark.webp","…"]}},"swap":{"attribute_glaze":["White"]}}'>
  <img class="bfbe-layers__base" alt="Layered Mug" loading="eager" decoding="async" src="…mug-base.png" srcset="…" sizes="…">
  <img class="bfbe-layers__layer is-on" data-bfbe-layer="attribute_glaze" data-bfbe-value="Sage" alt="" decoding="async" src="…sage.webp" srcset="…" sizes="…">
  <img class="bfbe-layers__layer is-on" data-bfbe-layer="attribute_print" data-bfbe-value="Fern" alt="" decoding="async" src="…fern.webp" srcset="…" sizes="…">
</div>
```

- Root `.bfbe-layers`, a `div`: `position: relative`, `inline-size: fit-content`, capped at 100% of its container, `overflow: hidden` and the pack's corners (`--bfbe-radius`) until the Style tab's **Border** sets others.
- `.bfbe-layers__base` is the base picture at WooCommerce's single product image size (`woocommerce_single`), never stretched, its `alt` the product's name.
- One `.bfbe-layers__layer` per layered attribute, in the product's attribute order, so the first attribute is the bottom layer. Each covers the base (`inset: 0`, `object-fit: contain`) with `alt=""` and no pointer events.
- States on a layer: `is-on` (opacity 1) while it shows an image; `data-bfbe-value` the value shown, empty when none; `data-bfbe-second="1"` while it shows its second image. A layer with nothing chosen is an `img` with no `src` and no `is-on`.
- `data-bfbe-layers` is the whole map the script reads: per select name (`attribute_<key>`), each value's address and `srcset`, then its second image's when it has one, and `swap`, the values that ask the other layers for their second image.
- Where controls write: `duration` (200 ms unset), `easing` and `easingCustom` set `--bfbe-duration`, `--bfbe-ease` and `--bfbe-ease-custom` on the root, which time each layer's opacity fade. Every Style tab control lands on the root.
- `window.bfbeProductLayers()` reads every variations form on the page again.

## Wiring to other elements

- **The product's options form.** It follows `form.variations_form` whose `data-product_id` is its product: Bricks' **Add to cart** (`product-add-to-cart`) of the same product on the page. A select, Bricks' swatches, the shop's swatches (skill `bfbe-shop-add-to-cart`) and WooCommerce's **Clear** all change the layers, each layer as soon as its own option changes. Every Product Layers of that product on the page follows the same form.
- **Product** `product`: empty reads the product of the page (a product template); set a product id to show another. A variation's id reads its parent's layers, and the form it follows is the parent's.
- **The product's BFB Layers tab** (variable products, the product edit screen) holds the images, stored as product meta `_bfbe_layers`. An agent that builds the shop sets it there or writes the meta in this shape:

```json
{
  "base": 4101,
  "layers": {
    "glaze": { "White": 4102, "Black": 4103, "Sage": 4105 },
    "print": { "Fern": 4110, "Wave": 4111 }
  },
  "second": { "print": { "Fern": 4120, "Wave": 4121 } },
  "swap": { "glaze": [ "White" ] }
}
```

`base` is an attachment id, 0 for the product image. `layers` and `second` map attribute, then value, to an attachment id; `swap` lists per attribute the values whose **Others show their second image** is ticked. The attribute is WooCommerce's field name without `attribute_`: `pa_colour` for a global attribute, the sanitised name (`glaze`, `print`) for the product's own. The value is what the form sends: a term's slug (`moss`) or a custom option's own text (`Sun Rays`). The ids above are illustrative; use the target site's attachments.
- **BFB Text Field, Draw over a picture** (skill `bfbe-form`; the form switched to a product's options carries the words to the cart). On the Text Field set `bfbeShopDraw: true`, `bfbeShopDrawOn: "element"` and **Element id** `bfbeShopDrawEl` to this element's Bricks id (`abc123`; `#` and `brxe-` are stripped). The typed words are drawn over the layered picture, at `bfbeShopDrawX` and `bfbeShopDrawY` per cent of its box.
- Find it by a class in `_cssClasses`, never `_cssId` (component instances share ids). It dispatches no event and is not a slide of Bricks' **Product gallery**: place it where the gallery would go. Hub: skill `bfbe-shop`.

## Verified patterns

**The picture alone, on a product template** (template `bfbe-layers-demo-product`, "Demo: the layered mug"). With `product` empty it shows the page's product; its layers come from that product's BFB Layers tab, and it follows the Add to cart placed beside it.

```json
{ "name": "bfbe-product-layers", "settings": { "_cssClasses": "layermug-picture" } }
```

**The layered picture beside the buy column** (the same template, its layout kept). A grid of two columns, one on Bricks' two mobile breakpoints; Bricks' own title, price, short description and Add to cart on the right. The Add to cart is the variations form the layers follow, so both must show the same product.

```json
{
  "name": "block",
  "settings": { "_display": "grid", "_gridTemplateColumns": "minmax(0, 520px) minmax(0, 1fr)", "_gridTemplateColumns:mobile_landscape": "minmax(0, 1fr)", "_gridTemplateColumns:mobile_portrait": "minmax(0, 1fr)", "_gridGap": "48px", "_gridGap:mobile_portrait": "24px", "_alignItems": "center" },
  "children": [
    { "name": "bfbe-product-layers", "settings": { "_cssClasses": "layermug-picture" } },
    { "name": "block", "settings": { "_rowGap": "18px" }, "children": [
      { "name": "heading", "settings": { "text": "{post_title}", "tag": "h1" } },
      { "name": "product-price", "settings": {} },
      { "name": "product-short-description", "settings": {} },
      { "name": "product-add-to-cart", "settings": { "_cssClasses": "layermug-atc" } }
    ] }
  ]
}
```

## Gotchas

- **The layers are the product's field, not the variations' images.** WooCommerce shows a variation's image in the cart, the order emails and feeds, where a bare transparent layer would stand for the product. Leave the variations' images empty or give them finished pictures. <!-- src: docs/elements/product-layers.md "The product field" ; plugins/bfb-elements-pro/includes/shop/class-product-layers.php:11-12 -->
- **Variable products, attributes used for variations.** The BFB Layers tab shows for variable products; an attribute counts only with **Used for variations** ticked and values. A simple product, or one with no layer images, draws its base picture alone and loads no script. <!-- src: plugins/bfb-elements-pro/includes/shop/class-product-layers.php:72-99, :150 ; plugins/bfb-elements-pro/elements/product-layers.php:100-109 -->
- **A new attribute or value needs a save first.** Its rows show on the tab after the product is saved; a value the screen did not list keeps what it had. In `_bfbe_layers`, a key or value the product does not have, or an id that is not an image attachment, is ignored. <!-- src: docs/elements/product-layers.md "The product field" ; plugins/bfb-elements-pro/includes/shop/class-product-layers.php:109-137, :291-310 -->
- **Same canvas, or they will not line up.** Every layer is stretched over the base with `object-fit: contain`; use transparent PNG or WebP images of the base picture's own size, each drawn where it belongs. A layer of another shape is letterboxed inside the base. <!-- src: src/elements/product-layers/product-layers.css:6 ; docs/elements/product-layers.md "The product field" -->
- **Attribute order is stacking order.** The first attribute on the product's Attributes tab is the bottom layer; reorder the attributes there to reorder the layers. A value with no image shows no layer, which suits a "None" print. <!-- src: plugins/bfb-elements-pro/elements/product-layers.php:126-129 ; docs/elements/product-layers.md "The product field" -->
- **The second image swaps the others, never its own.** While a value in `swap` is chosen, every layer of the other attributes shows its second image if it has one, else its first. One switch, one second image per value: no third look and no image for one exact pairing. <!-- src: plugins/bfb-elements-pro/elements/product-layers.php:175-182 ; src/elements/product-layers/product-layers.js:62-67 ; docs/elements/product-layers.md "What this is not the right tool for" -->
- **The first paint is the server's.** It shows the product's default options, or the options in the address (`?attribute_pa_colour=navy`). With no default and nothing in the address, a layer stays empty until its option is chosen; without JavaScript the first picture stays. <!-- src: plugins/bfb-elements-pro/elements/product-layers.php:136-147 ; docs/elements/product-layers.md "How it follows the choice" -->
- **The canvas does not follow choices.** In the builder each layered attribute with no default shows its first image, so the stack can be styled, and choosing an option changes nothing. Check the swap on the page. <!-- src: plugins/bfb-elements-pro/elements/product-layers.php:143-145 ; src/elements/product-layers/product-layers.js:14-16, :56 -->
- **No product or no picture, nothing on the page.** Off a product page with `product` empty, or with no product image and no base picture, the page gets nothing; the canvas says "Choose a product, or place this on a product page." or asks for an image. <!-- src: plugins/bfb-elements-pro/elements/product-layers.php:115-123 ; plugins/bfb-elements/includes/abstract-element.php:549-552 -->
- **It needs the same product's form on the page.** The script matches the form's `data-product_id` to its product; a Product Layers of one product beside the Add to cart of another never changes. <!-- src: src/elements/product-layers/product-layers.js:57-61 -->
- **The composed picture stays on the product page.** Cards, the cart and the emails show the product's or the variation's own image, and there is no lightbox or zoom of the stack. A layer adds no price; paid extras are product options (skill `bfbe-form`). <!-- src: docs/elements/product-layers.md "What this is not the right tool for" -->
- **Each image's address rides in the page.** About a kilobyte per image before compression, second images included; an image is fetched the first time its value is chosen, and shown once loaded. Under reduced motion a layer changes with no fade. <!-- src: docs/elements/product-layers.md "Cost" ; src/elements/product-layers/product-layers.js:47-51 ; src/elements/product-layers/product-layers.css:8 -->

## Never do

- Do not put layer images on the variations; set them on the product's BFB Layers tab (`_bfbe_layers`).
- Do not use layers of another size or shape than the base picture.
- Do not place it off a product page without `product`, or beside the Add to cart of a different product.
- Do not expect a value's own tick in **Others show their second image** to change its own layer.
- Do not write `_bfbe_layers` with `attribute_` prefixes, term names in place of slugs, or ids that are not image attachments.
- Do not judge the swaps from the builder canvas; check them on the page.
- Do not find it by `_cssId`; use a class in `_cssClasses`, and its Bricks id only for **Element id** `bfbeShopDrawEl`.
