---
name: bfbe-shop-add-to-cart
description: "Use for the shop's settings on Bricks' Add to cart and Products (BFB Shop add to cart, `shop-add-to-cart`): swatches and add to cart on product cards, preselect the first variation, sold-out options, a styled options list, the quantity as one piece, the price per item, ask for a price. Read before writing these settings."
---

# BFB Shop add to cart (`shop-add-to-cart`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 2.0.0 or later, and BFB Elements Pro 2.0.0 or later for the groups marked Pro, WooCommerce active, the feature switches on (WordPress menu BFB Elements, Elements): `shop-product-page`, `shop-buy`, `shop-cards`, `shop-quantity-breaks`. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/shop-add-to-cart.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/shop/ (the Shop), and a page for each feature this skill spans: https://builtforbricks.com/bfb-elements/docs/shop-product-page/, https://builtforbricks.com/bfb-elements/docs/shop-buy/, https://builtforbricks.com/bfb-elements/docs/shop-cards/, https://builtforbricks.com/bfb-elements/docs/shop-quantity-breaks/

## What it is
The website documents this by feature; each line is the approved summary from that feature's page.
- `shop-product-page` (https://builtforbricks.com/bfb-elements/docs/shop-product-page/): A free feature for Bricks single product templates, not an element. It makes sure WooCommerce's own product data for search engines is printed once on every product page, even on a template built only from Bricks' product elements, and it has Bricks' Product gallery load the main picture at once with high priority, whatever sits above it. It also adds look controls to Bricks' Product gallery and to the buying form inside Bricks' Add to cart.
- `shop-buy` (https://builtforbricks.com/bfb-elements/docs/shop-buy/): A Pro feature with two sides. It is what sends a BFB Buy Now press on to the checkout, setting the shopper's cart aside when the item goes alone, and it adds catalogue mode: rules on the Shop page that show chosen products without selling them online, with an Ask for a price button where the add to cart was. Catalogue mode is decided on the server, so the cart refuses those products too.
- `shop-cards` (https://builtforbricks.com/bfb-elements/docs/shop-cards/): Swatches and an add to cart button on product cards, on Bricks' own Add to cart element in a product loop and on Bricks' Products element: a shopper picks colour and size on the card, the picture and price follow, and the exact variation goes in the cart without leaving the page. On the product page the same group sets how Bricks' Add to cart picker behaves: preselect an in-stock variation, the earliest in the list,, and hide or cross out sold-out options.
- `shop-quantity-breaks` (https://builtforbricks.com/bfb-elements/docs/shop-quantity-breaks/): A price per item that falls as the quantity rises, set per product or per category. One rule prices the cart line on the server and draws the table on the product page, so the page and the cart show the same number. This page is the rule, the cart and the price per item beside the quantity; the table is the BFB Quantity Breaks element.

## Where it lives
A feature, not an element: its groups are added to Bricks' own elements, on the Content tab after Bricks' own groups. By element:
- Add to cart (`product-add-to-cart`): BFB Buying form (`bfbeShopBuyForm`), BFB Options list (`bfbeShopOptsList`), BFB Ask for a price (`bfbeShopAsk`), BFB Product cards (`bfbeShopCards`), BFB Quantity breaks (`bfbeShopQb`).
- Products (`woocommerce-products`): BFB Product cards (`bfbeShopCards`).

## Settings that decide the build

### Add to cart (`product-add-to-cart`)

#### BFB Buying form (`bfbeShopBuyForm`)
Free, switch `shop-product-page`.
- `bfbeShopQtyButtons` (select) **Quantity buttons**: options: `bricks` The − and + Bricks adds (default), `browser` The browser's arrows, `none` None
Styling, in the schema file: `bfbeShopVarStack`, `bfbeShopVarGap`, `bfbeShopVarLabelGap`, `bfbeShopVarClearTypography`, `bfbeShopSwatchFill`, `bfbeShopQtyOne`, `bfbeShopQtyHeight`, `bfbeShopQtyBorder`, `bfbeShopQtyTypography`, `bfbeShopQtyButtonWidth`, `bfbeShopQtyButtonColor`, `bfbeShopQtyButtonHover`, `bfbeShopQtyDisabled`, `bfbeShopRowStack`, `bfbeShopRowWide`, `bfbeShopRowHeight`.

#### BFB Options list (`bfbeShopOptsList`)
Free, switch `shop-product-page`.
- `bfbeShopOptsListLook` (select) **Open list**: options: `native` As the browser draws it (default), `custom` Styled with the controls below. Selects shown as Bricks' swatches keep them.
Styling, in the schema file: `bfbeShopOptsListTypography`, `bfbeShopOptsListBackground`, `bfbeShopOptsListBorder`, `bfbeShopOptsListPadding`, `bfbeShopOptsListChevron`, `bfbeShopOptsListPanelBg`, `bfbeShopOptsListPanelBorder`, `bfbeShopOptsListPanelShadow`, `bfbeShopOptsListPanelPadding`, `bfbeShopOptsListOptTypography`, `bfbeShopOptsListOptPadding`, `bfbeShopOptsListOptHover`, `bfbeShopOptsListHoverText`, `bfbeShopOptsListOptOnBg`, `bfbeShopOptsListOptOnColor`, `bfbeShopOptsListTick`.

#### BFB Ask for a price (`bfbeShopAsk`)
Pro, switch `shop-buy`.
Styling only, every key in the schema file: `bfbeShopAskWidth`.

#### BFB Product cards (`bfbeShopCards`)
Pro, switch `shop-cards`.
- `bfbeShopCardSwatches` (checkbox) **Swatches on the card**. Inside a product loop.
- `bfbeShopCardSimple` (select) **On simple products**: options: `swatch` Show its swatch (default), `none` Nothing; only when `bfbeShopCardSwatches` is set
- `bfbeShopCardSimpleAttr` (select) **Attribute**: options: `pa_colour` Colour, `pa_material` Material, `pa_q5-finish` Q5 Finish, `pa_q5-pattern` Q5 Pattern, `pa_size` Size, `pa_warmth` Warmth; only when `bfbeShopCardSwatches` is set and `bfbeShopCardSimple` is not `none`
- `bfbeShopCardAddText` (text) **Label**: placeholder Add to cart; only when `bfbeShopCardSwatches` is set
- `bfbeShopFirst` (checkbox) **Preselect first variation**
- `bfbeShopSoldOut` (select) **Sold-out options**: options: `hidden` Hidden, `crossed` Crossed out
Styling, in the schema file: `bfbeShopCardLegendTypography`, `bfbeShopCardSwatchBorder`, `bfbeShopCardSwatchOn`, `bfbeShopCardSwatchSize`, `bfbeShopCardLabelPadding`, `bfbeShopCardLabelBackground`, `bfbeShopCardSwatchGap`, `bfbeShopCardSwatchScroll`, `bfbeShopCardBtnTypography`, `bfbeShopCardBtnBackground`, `bfbeShopCardBtnBorder`, `bfbeShopCardBtnPadding`, `bfbeShopCardBtnWidth`, `bfbeShopCardBtnShadow`, `bfbeShopCardBtnHover`, `bfbeShopCardBtnHoverColor`.

#### BFB Quantity breaks (`bfbeShopQb`)
Pro, switch `shop-quantity-breaks`.
- `bfbeShopQbEach` (checkbox) **Show**
Styling, in the schema file: `bfbeShopQbEachTypography`.

### Products (`woocommerce-products`)

#### BFB Product cards (`bfbeShopCards`)
Pro, switch `shop-cards`.
- `bfbeShopCardSwatches` (checkbox) **Swatches on the card**. Place them in a field with {bfbe_card_swatches}.
- `bfbeShopSoldOut` (select) **Sold-out options**: options: `hidden` Hidden, `crossed` Crossed out (default); only when `bfbeShopCardSwatches` is set
Styling, in the schema file: `bfbeShopCardLegendTypography`, `bfbeShopCardSwatchBorder`, `bfbeShopCardSwatchOn`, `bfbeShopCardSwatchSize`, `bfbeShopCardLabelPadding`, `bfbeShopCardLabelBackground`, `bfbeShopCardSwatchGap`, `bfbeShopCardSwatchScroll`, `bfbeShopCardBtnTypography`, `bfbeShopCardBtnBackground`, `bfbeShopCardBtnBorder`, `bfbeShopCardBtnPadding`, `bfbeShopCardBtnWidth`, `bfbeShopCardBtnShadow`, `bfbeShopCardBtnHover`, `bfbeShopCardBtnHoverColor`.
<!-- bfbe:generated:end -->

## Rendered DOM

The feature adds no element. It writes CSS at the host's id, attributes on the host's root, and markup inside WooCommerce's own form or in place of the loop button.

On the product page (Bricks' Add to cart outside a query loop):

- **BFB Buying form** writes CSS only, unset changes nothing: `table.variations` rows (**Label above the choice** `bfbeShopVarStack`), `.reset_variations`, `.bricks-variation-swatches.bricks-swatch-label` (**Label swatches fill the row** `bfbeShopSwatchFill`), `.cart .quantity` with its `.qty` and Bricks' `.action` buttons, and `.cart .single_add_to_cart_button`. **Quantity buttons** `bfbeShopQtyButtons: "browser"` or `"none"` writes `data-bfbe-qty` on the root instead.
- **Quantity first, buttons below** (`bfbeShopRowStack`) makes the form a wrapping flex row: the quantity, then the price per item, then a line break (`::before`), then the buttons.
- **BFB Options list** with `bfbeShopOptsListLook: "custom"` adds `bfbe-dd` and `data-bfbe-dd=".variations select"` to the root. The script wraps each shown select in `span.bfbe-dd__field` and lays a `ul.bfbe-dd__panel[role="listbox"]` of `li.bfbe-dd__opt[role="option"]` under it; the select stays the control, with `aria-expanded` and `aria-controls`.
- **Preselect first variation** and **Sold-out options** write `data-bfbe-shop-first="1"` and `data-bfbe-shop-soldout="hidden|crossed"` on the root, for a variable product only. Sold-out choices take `bfbe-soldout` on Bricks' swatch `li` and on the `option`.
- **BFB Quantity breaks** `bfbeShopQbEach` prints `span.bfbe-qb__each[data-bfbe-qb-each]` ("44,00 € each") right after the quantity.
- With the Buying switch on, the `form.cart` takes `id="bfbe-cart-{product id}"` unless it has one.
- **BFB Ask for a price**: under a catalogue rule, `a.button.bfbe-ask[data-bfbe-ask]` stands where the add button would (`bfbe-ask--loop` on a card); `bfbeShopAskWidth` writes `.bfbe-ask`.

In a product loop (Bricks' Add to cart in a query loop, or the Products element's loop button), **Swatches on the card** turns a variable product's button into a form:

```html
<form id="bfbe-cart-{id}-{loop element id}-{row}" class="cart bfbe-cardsw" method="post" data-bfbe-cardsw
      data-product_id="{id}" data-product_variations="[…]">
  <fieldset class="bfbe-cardsw__group" data-attribute="attribute_pa_colour">
    <legend class="bfbe-cardsw__legend">Colour</legend>
    <ul class="bricks-variation-swatches bricks-swatch-color bfbe-cardsw__list">
      <li class="bfbe-cardsw__opt" data-value="ink" data-balloon="Ink">
        <input type="radio" class="bfbe-cardsw__radio" name="attribute_pa_colour" value="ink">
        <label class="bricks-swatch-button bfbe-cardsw__swatch"><span aria-hidden="true" style="background-color: …"></span><span class="bfbe-sr">Ink</span></label>
      </li>
    </ul>
  </fieldset>
  <input type="hidden" name="add-to-cart"> <input type="hidden" name="variation_id" class="variation_id"> <input type="hidden" name="quantity" value="1">
  <button type="submit" class="button add_to_cart_button bfbe-cardsw__add"><span class="bfbe-cardsw__word">Add to cart</span><span class="bfbe-sr"> {product}</span></button>
</form>
```

- The Products element's cards (no query loop) use `id="bfbe-cart-{id}-p{n}"`. With the tag `{bfbe_card_swatches}` in the card, the fieldsets print there instead, in `div.bfbe-cardsw.bfbe-cardsw__choices[data-bfbe-cardsw-for="{form id}"]`, each radio carrying `form="{form id}"`.
- States: the chosen `li` gets `bricks-swatch-selected`, the form `bfbe-cardsw--ready` once a variation matches, the button `aria-busy="true"` while adding and `added` with the word "Added" for two seconds.
- A simple product with **On simple products** `swatch` gets `ul.bfbe-cardsw__list.bfbe-cardsw__shown` of `li.bfbe-cardsw__static` before Bricks' own button: a list, not radios.
- The `bfbeShopCard*` swatch controls write `.bfbe-cardsw__legend`, `.bfbe-cardsw__opt`, `.bfbe-cardsw__swatch` and `.bfbe-cardsw__list`; the button controls write `.bfbe-cardsw__add`; **Chosen border** also sets `--bfbe-cardsw-on`.

## Wiring to other elements

- **Hub and neighbours.** Start at `bfbe-shop`. Product loops are `bfbe-shop-loops`; the tag `{bfbe_card_swatches}` and the shop's conditions are `bfbe-shop-tags-and-conditions`.
- **The product's form is what others find.** BFB Buy Now joins it through the HTML `form` attribute (`bfbe-cart-{id}`); BFB Quantity Breaks and BFB Sticky Buy Bar find it by the product's id. Keep one Add to cart per product on a product template.
- **A card's form and its row.** In a query loop the form id carries the loop element and the row, so a BFB Buy Now in the same row joins that card. Put both in the same looping element.
- **Swatches placed apart.** On the Products element, put `{bfbe_card_swatches}` in a field of its own (`fields`); on Bricks' Add to cart in a query loop, in any element of the same loop (a Basic Text). The form then holds the button alone.
- **The card's picture and price follow the choice.** The script takes the first `img` and the first `.price` outside the form, in the nearest ancestor that holds an image, so keep Bricks' Image and Product price in the same card as the Add to cart.
- **Bricks' swatch settings.** Colours, pictures and words come from WooCommerce, Attributes, under Bricks' swatch type, and Bricks' own swatch controls on the Add to cart (`colorSwatchSize`, `labelSwatchTypography`) reach the card's swatches.
- **Catalogue mode.** Ask for a price follows the rules on BFB Elements, Shop, card Catalogue mode; the element only sizes the button.
- No `_cssId` or class is needed for any of this: everything goes by product and by loop row, and component instances share ids.

## Verified patterns

**A product page form with every buying setting.** From the 2.4 site's demo shop, template "Fernhouse: product page" (`bfb-demo-product`). Choices stacked with their labels, size words sharing the row, the quantity as one rounded piece, the price per item beside it and the button below at 52px, a styled options list, the first available variation chosen and sold-out choices crossed out. Trimmed: Bricks' own swatch, button and typography settings and the demo's colour variables.

```json
{
  "name": "product-add-to-cart",
  "settings": {
    "bfbeShopVarStack": true,
    "bfbeShopVarGap": "14px",
    "bfbeShopVarLabelGap": "8px",
    "bfbeShopSwatchFill": true,
    "bfbeShopQtyOne": true,
    "bfbeShopQtyHeight": "48px",
    "bfbeShopQtyBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "999", "right": "999", "bottom": "999", "left": "999" } },
    "bfbeShopQtyButtonWidth": "42px",
    "bfbeShopQtyDisabled": "0.35",
    "bfbeShopRowStack": true,
    "bfbeShopRowWide:mobile_landscape": true,
    "bfbeShopRowHeight": "52px",
    "bfbeShopOptsListLook": "custom",
    "bfbeShopOptsListPanelBg": { "hex": "#ffffff" },
    "bfbeShopOptsListOptOnBg": { "hex": "#f0ecff" },
    "bfbeShopOptsListTick": { "hex": "#6e44ff" },
    "bfbeShopFirst": true,
    "bfbeShopSoldOut": "crossed",
    "bfbeShopQbEach": true
  }
}
```

**Product cards with swatches in a query loop.** From the fixture "PRO: Shop cards, swatches on the card" (`fixture-shop-cards`). Each looping block is a card; its Add to cart becomes the swatch form with the button word "Add", and the card's picture and price follow the choice. The fixture's `post__in` list is left out (set the target site's own query), and its grid is moved onto a wrapper, since Bricks repeats the looping element itself.

```json
{
  "name": "block",
  "settings": { "_display": "grid", "_gridTemplateColumns": "repeat(3, minmax(0, 1fr))", "_gridGap": "24px" },
  "children": [
    {
      "name": "block",
      "settings": { "hasLoop": true, "query": { "objectType": "post", "post_type": ["product"], "posts_per_page": 6 } },
      "children": [
        { "name": "image", "settings": { "image": { "useDynamicData": "{featured_image}", "size": "woocommerce_thumbnail" } } },
        { "name": "product-title", "settings": { "tag": "h3" } },
        { "name": "product-price", "settings": {} },
        { "name": "product-add-to-cart", "settings": { "bfbeShopCardSwatches": true, "bfbeShopCardAddText": "Add" } }
      ]
    }
  ]
}
```

**The Products element with the swatches above the title.** From the fixture "PRO: Shop cards, the swatches placed apart from the button" (`fixture-shop-cards-split`). The tag's field puts the radios above the title, `{woo_add_to_cart}` keeps the button last, and sold-out choices are hidden. The fixture's `categories` (a site term id) is left out.

```json
{
  "name": "woocommerce-products",
  "settings": {
    "columns": 3,
    "posts_per_page": 6,
    "bfbeShopCardSwatches": true,
    "bfbeShopSoldOut": "hidden",
    "fields": [
      { "id": "f1img", "dynamicData": "{featured_image:woocommerce_thumbnail:link}" },
      { "id": "f2swa", "dynamicData": "{bfbe_card_swatches}" },
      { "id": "f3tit", "dynamicData": "{post_title:link}", "tag": "h3" },
      { "id": "f4pri", "dynamicData": "{woo_product_price}" },
      { "id": "f5add", "dynamicData": "{woo_add_to_cart}" }
    ]
  }
}
```

## Gotchas

- **Swatches on the card act in a product loop only.** They replace WooCommerce's loop button, so Bricks' Add to cart on a product page ignores `bfbeShopCardSwatches`; place it inside a query loop or use the Products element. <!-- src: plugins/bfb-elements-pro/includes/shop/class-cards.php:338 -->
- **Only a variable product that can be bought gets the form.** Out of stock, not purchasable, grouped and external products keep Bricks' own button; a simple product gets its display swatch on Bricks' Add to cart only, never on the Products element. <!-- src: plugins/bfb-elements-pro/includes/shop/class-cards.php:487 ; plugins/bfb-elements-pro/includes/shop/class-cards.php:657 ; docs/elements/shop-cards.md "On simple products" -->
- **Colour and picture swatches need Bricks' Variation swatches setting.** With it off (Bricks, Settings, WooCommerce), every attribute draws as words, on cards and in the simple product's swatch alike. <!-- src: plugins/bfb-elements-pro/includes/shop/class-cards.php:691 -->
- **Swatch look controls reach only the swatches the element prints.** Swatches placed by `{bfbe_card_swatches}` in a Basic Text take Bricks' swatch classes and `.bfbe-cardsw__opt`, not the Add to cart's `bfbeShopCard*` look: style them with a class of your own. <!-- src: docs/elements/shop-cards.md "The swatches and the button, placed apart" -->
- **Every card carries its variation list.** The list rides each card's form up to WooCommerce's threshold of 30 variations; above it each choice asks `wc-ajax=get_variation`. A grid of many products with many variations is a heavy page. <!-- src: plugins/bfb-elements-pro/includes/shop/class-cards.php:460 ; docs/elements/shop-cards.md "Swatches on the card" -->
- **Sold-out defaults differ by host.** On Add to cart, unset `bfbeShopSoldOut` means as WooCommerce; on the Products element, unset means crossed out. Above 30 variations the product page keeps WooCommerce's behaviour, and Preselect takes each attribute's first option. <!-- src: plugins/bfb-elements-pro/includes/shop/class-cards.php:284-312 ; docs/elements/shop-cards.md "The variation picker's behaviour" -->
- **Preselect first variation is for the product page.** It writes its attribute for a variable product only, the Products element does not offer it, and on a card it does nothing. <!-- src: plugins/bfb-elements-pro/includes/shop/class-cards.php:377-381 ; src/elements/shop-cards/shop-cards.js:118 ; docs/elements/shop-cards.md "On simple products" -->
- **The styled options list is for a mouse.** A phone, or any pointer that cannot hover, keeps the browser's picker, and a select behind Bricks' swatches is left alone. The Arrow colour and every Open list and Options control show only with `bfbeShopOptsListLook: "custom"`. <!-- src: src/elements/shop-sorting/shop-sorting.js:28-44 ; plugins/bfb-elements/includes/shop/class-sorting.php:239-270 -->
- **The Buttons controls stop at the form.** `bfbeShopRowStack`, `bfbeShopRowWide` and `bfbeShopRowHeight` write `.cart .single_add_to_cart_button`; BFB Buy Now is its own element outside the form, so give it `_height` on its Style tab, as the demo sets 52px on both. <!-- src: plugins/bfb-elements/includes/shop/class-product-page.php:243 ; dev/demo/shop/lib.php:855 -->
- **Quantity buttons browser or none hide the button look.** `bfbeShopQtyButtonWidth`, `bfbeShopQtyButtonColor`, `bfbeShopQtyButtonHover` and `bfbeShopQtyDisabled` apply to Bricks' − and + only, and Bricks' `.action` buttons are hidden for the other two. <!-- src: plugins/bfb-elements/includes/shop/class-product-page.php:355-383 ; src/elements/spin/spin.css:43 -->
- **The price per item needs rows.** `bfbeShopQbEach` prints nothing for a product without quantity breaks of its own or from a category, and needs the Quantity breaks switch. <!-- src: plugins/bfb-elements-pro/includes/shop/class-quantity-breaks.php:448-458 -->
- **Ask for a price needs a rule with a target.** The button prints only when a catalogue rule applies with Instead set to a page or a popup and its address or popup id filled; Bricks' own Width reaches the add button alone. <!-- src: plugins/bfb-elements-pro/includes/shop/class-catalogue.php:290-300 ; plugins/bfb-elements-pro/includes/shop/class-buy-now.php:98 -->
- **Without a script the card still sells.** The form posts the radios to the page it is on and WooCommerce adds the matching variation; a variation set to "Any" on an attribute also adds through that post, and the page reloads with WooCommerce's notice. <!-- src: plugins/bfb-elements-pro/includes/shop/class-cards.php:395 ; src/elements/shop-cards/shop-cards.js:229 ; docs/elements/shop-cards.md "Swatches on the card" -->

## Never do

- Do not set `bfbeShopCardSwatches` on an Add to cart outside a query loop and expect swatches.
- Do not put a card's BFB Buy Now in another looping element than its Add to cart.
- Do not place two Add to cart elements for the same product on a product template.
- Do not style tag-placed swatches with the Add to cart's `bfbeShopCard*` controls; give them a class.
- Do not set the Options list's panel or option colours without `bfbeShopOptsListLook: "custom"`.
- Do not size BFB Buy Now with `bfbeShopRowHeight`; set its own `_height`.
- Do not set `bfbeShopQtyButtonWidth` or its siblings with `bfbeShopQtyButtons` set to `browser` or `none`.
