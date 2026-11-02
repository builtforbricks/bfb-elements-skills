---
name: bfbe-bundle-builder
description: "Use when building a mix and match bundle, build a box or any 3 for a price offer with `bfbe-bundle-builder`: products from a category, a tag or a list, tick boxes or steppers, a progress bar, and a set price or a percentage off."
---

# BFB Bundle Builder (`bfbe-bundle-builder`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-bundle-builder.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/bundle-builder/

## What it is
A pick your own bundle, such as Choose any 3 for 30,00 € or 3 for 20% off: the shopper picks a set number of products from a category, a tag or a list of your own, sees how far along they are, and adds the bundle once it is complete. It is a nestable form with three parts placed in Bricks' own containers. The bundle's price is worked out on your server from the element's settings, and its lines add up to it exactly.

**Not for:** Not for variable products, which need a choice the cards do not offer, so they are not shown. For a fixed set of companions to one product, use BFB Bought Together.

**Costs a page:** CSS 0.91 KB, JS 1.45 KB (gzipped), plus shop-live, loaded only on pages that use it.

**Nestable:** yes · **In a query loop:** no · **Dynamic data:** no · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Nestable. Its own children: `bfbe-bundle-title`, `bfbe-bundle-progress`, `bfbe-bundle-products`.
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-bundle-builder",
    "settings": {},
    "children": [
        {
            "name": "bfbe-bundle-title",
            "settings": {}
        },
        {
            "name": "bfbe-bundle-progress",
            "settings": {}
        },
        {
            "name": "bfbe-bundle-products",
            "settings": {}
        },
        {
            "name": "button",
            "settings": {
                "text": "Add the bundle",
                "tag": "button",
                "style": "primary",
                "_cssClasses": "bfbe-bundle__add",
                "_attributes": [
                    {
                        "id": "bfbebb",
                        "name": "type",
                        "value": "submit"
                    }
                ]
            }
        }
    ]
}
```

`bfbe-bundle-title` (BFB Bundle Title), 43 controls, schema `../bfbe-schemas/references/elements/bfbe-bundle-title.json`.

`bfbe-bundle-progress` (BFB Bundle Progress), 51 controls, schema `../bfbe-schemas/references/elements/bfbe-bundle-progress.json`.

`bfbe-bundle-products` (BFB Bundle Products), 71 controls, schema `../bfbe-schemas/references/elements/bfbe-bundle-products.json`.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Bundle (`bfbeBundle`)
- `source` (select) **Products from**: options: `category` A category (default), `tag` A tag, `ids` Products chosen here. A category (the default), A tag, or Products chosen here, with **Category slug**, **Tag slug** or **Products** naming them. Only simple products that can be bought now are offered, never one whose options require an answer.
- `category` (text) **Category slug**: placeholder kitchen; only when `source` is not `tag` or `ids`
- `tag` (text) **Tag slug**: placeholder gift; only when `source` is `tag`
- `products` (select) **Products**: placeholder Pick the products; only when `source` is `ids`
- `most` (number) **Products shown**: placeholder 12. How many cards, 12 unless set, at most 24.
- `count` (number) **Products to choose**: placeholder 3
- `kind` (select) **Bundle price**: options: `price` A set price (default), `percent` A percentage off each. A set price (the default) with **Set price**, split across the bundle's lines to the cent, or A percentage off each with **Percentage off**, 1 to 90.
- `price` (number) **Set price**: placeholder 30; only when `kind` is not `percent`
- `percent` (number) **Percentage off**: placeholder 20; only when `kind` is `percent`

### Button (`bfbeButton`)
Styling only, every key in the schema file: `disabledOpacity`.

## What it guarantees for accessibility (do not undo)
- Cards carry a real checkbox, or a stepper whose two buttons are named for the product, such as One more Wool Beanie and One fewer Wool Beanie; a stepper stops at the bundle's count.
- The progress is a real progress bar named by the offer, its value and its words following each choice, said once.
- The add button stays reachable but is marked aria-disabled until exactly the bundle's count is chosen; pressed early it says what is missing, such as Choose 1 more.
- Under reduced motion the progress bar fills without moving.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<form id="brxe-{id}" class="brxe-bfbe-bundle-builder bfbe-bundle" method="post" data-bfbe-shop-need="cart"
      data-bfbe-bundle='{"n":3,"words":{"more":"Choose %d more.","less":"Take %d out.",…}}'>
  <input type="hidden" name="bfbe_shop_act" value="bundle_add"> <!-- + _bfbe_back, post, el; _bfbe_nonce when signed in -->
  <!-- the parts, anywhere inside, in any Bricks container -->
  <h3 class="brxe-bfbe-bundle-title bfbe-bundle__title">Choose any 3 for 30,00 €</h3>
  <div class="brxe-bfbe-bundle-progress bfbe-bundle__progress" data-bfbe-bundle-words="{chosen} of {count} chosen">
    <div class="bfbe-bundle__bar" role="progressbar" aria-labelledby="{title id}" aria-valuemin="0" aria-valuemax="3"
         aria-valuenow="0" aria-valuetext="0 of 3 chosen" style="--bfbe-bundle-done:0"><span class="bfbe-bundle__fill"></span></div>
    <p class="bfbe-bundle__count" aria-hidden="true">0 of 3 chosen</p>
    <p class="bfbe-bundle__note" hidden></p>
  </div>
  <ul class="brxe-bfbe-bundle-products bfbe-bundle__grid bfbe-bundle__grid--box">
    <li class="bfbe-bundle__card">
      <input type="checkbox" class="bfbe-bundle__box bfbe-tick" name="ids[]" value="123">
      <label class="bfbe-bundle__label" for="…"><span class="bfbe-bundle__media"><img …></span>
        <span class="bfbe-bundle__name">…</span><span class="bfbe-bundle__price">…</span></label>
    </li>
  </ul>
  <button class="brxe-button bricks-button bfbe-bundle__add" type="submit" aria-disabled="true">Add the bundle</button>
</form>
```

- The parent's root is a real `form`, a flex column (`gap: var(--bfbe-gap)`) until Bricks' Style tab lays it out.
- With **Each card has** `pick: "stepper"` a card holds the picture, a `label.bfbe-bundle__name`, the price and `span.bfbe-bundle__step`: `button.bfbe-bundle__minus` and `.bfbe-bundle__plus` (`data-bfbe-step`, named "One fewer …" and "One more …") around `input.bfbe-bundle__qty` (`name="q_{id}"`). The browser's spin arrows are hidden.
- The script sets `is-chosen` on a ticked card or one above 0, the bar's `aria-valuenow`, `aria-valuetext` and `--bfbe-bundle-done` (the fill's `scaleX`), the count's words, each stepper's `max`, and `aria-disabled="true"` on `.bfbe-bundle__add` until exactly the count is chosen (`aria-busy` while posting).
- Where controls write: on Products, `columns` to `--bfbe-bundle-cols` and `gap` to `--bfbe-bundle-gap` on the grid, `card*` to `.bfbe-bundle__card` (`chosen*` to `.is-chosen`), `image*` to `.bfbe-bundle__media img`, `tickInset` to `--bfbe-bundle-tick-inset`, `step*` to the stepper's buttons and number. On Progress, `bar*` and `trackColor` to `.bfbe-bundle__bar`, `barColor` to `--bfbe-bundle-bar`, `note*` to the note. On the parent, `disabledOpacity` to `--bfbe-bundle-dim`. The Title's look is Bricks' Style tab.

## Wiring to other elements

- **The parent holds the bundle; the parts print it.** Title, Progress and Products find the nearest `bfbe-bundle-builder` above them and read its settings; the server adds and prices from the parent's saved settings only. Place them anywhere inside it, in Bricks' own containers. Schemas: `../bfbe-schemas/references/elements/bfbe-bundle-title.json`, `../bfbe-schemas/references/elements/bfbe-bundle-progress.json`, `../bfbe-schemas/references/elements/bfbe-bundle-products.json`.
- **BFB Bundle Title**: **Words** `title` with `{count}`, `{price}` and `{percent}` filled in, and **HTML tag** `titleTag` (`p` unless set). The script names the progress bar by it (`aria-labelledby`) wherever the two sit in the form.
- **BFB Bundle Progress**: **Words** `progressText` with `{chosen}` and `{count}`, the Bar and Message controls. It is where "Choose 1 more." and the add's sentence show.
- **BFB Bundle Products**: `pick` (`box` or `stepper`), **Columns** `columns` per breakpoint, **Gap** `gap`, and the Card, Picture, Words, Tick box and Stepper controls.
- **The add button is Bricks' Button, found by class.** Put `bfbe-bundle__add` in its `_cssClasses`, with `tag: "button"` and the seeded `_attributes` type `submit`. **Disabled opacity** `disabledOpacity` on the parent dims it while the bundle is not complete.
- **The products** come from **Products from** `source`: `category` with **Category slug** `category`, `tag` with **Tag slug** `tag` (a comma list of slugs works), or `ids` with **Products** `products`.
- **The cart**: each product is its own line marked "Bundle: 3 for 30,00 €" in the cart, the checkout and the order; the script swaps the shop's cart fragments and fires `wc_fragment_refresh`, so Bricks' Mini cart follows. See `bfbe-shop`.
- For your own CSS give the parent a class in `_cssClasses`, never `_cssId`: component instances share ids.

## Verified patterns

**Any three for a set price, the title and the progress side by side** (the 2.4 site's demo shop, Sets page in `dev/demo/shop/20-pages.php`, trimmed of the brand's look; the category and price are the dev fixture's, `fixture-shop-bundle`). The parent is a flex column; a Block puts Title and Progress on one wrapping row; Products sets four, three and two columns per breakpoint. Use the target site's category slug.

```json
{
  "name": "bfbe-bundle-builder",
  "settings": { "source": "category", "category": "accessories", "count": 3, "kind": "price", "price": 30, "most": 12, "_display": "flex", "_flexDirection": "column", "_gap": "22px" },
  "children": [
    { "name": "block", "settings": { "_direction": "row", "_flexWrap": "wrap", "_justifyContent": "space-between", "_alignItems": "center", "_columnGap": "24px", "_rowGap": "12px" }, "children": [
      { "name": "bfbe-bundle-title", "settings": { "title": "Choose any {count} for {price}", "titleTag": "h2" } },
      { "name": "bfbe-bundle-progress", "settings": { "progressText": "{chosen} of {count} chosen", "barHeight": "8px", "_width": "320px", "_width:mobile_landscape": "100%" } }
    ] },
    { "name": "bfbe-bundle-products", "settings": { "pick": "box", "columns": 4, "columns:tablet_portrait": 3, "columns:mobile_landscape": 2, "gap": "20px" } },
    { "name": "button", "settings": { "text": "Add the set to my cart", "tag": "button", "style": "primary", "_cssClasses": "bfbe-bundle__add", "_attributes": [ { "id": "bfbebb", "name": "type", "value": "submit" } ], "_alignSelf": "flex-start" } }
  ]
}
```

**A percentage off each, with steppers** (fixture page `fixture-shop-bundle`, "3 for 20% off", `.p5b-bundle-pct`). `kind: "percent"` with `percent` takes 20% off each product's own price, and the Title's default words become "Choose any 3 for 20% off". `pick: "stepper"` lets one product count twice; the phone value `columns:mobile_portrait` is added here, as a base `columns` applies on phones too.

```json
{
  "name": "bfbe-bundle-builder",
  "settings": { "source": "category", "category": "kitchen", "count": 3, "kind": "percent", "percent": 20, "_cssClasses": "p5b-bundle-pct" },
  "children": [
    { "name": "bfbe-bundle-title", "settings": {} },
    { "name": "bfbe-bundle-progress", "settings": {} },
    { "name": "bfbe-bundle-products", "settings": { "pick": "stepper", "columns": 4, "columns:mobile_portrait": 2 } },
    { "name": "button", "settings": { "text": "Add the bundle", "tag": "button", "style": "primary", "_cssClasses": "bfbe-bundle__add", "_attributes": [ { "id": "bfbebb", "name": "type", "value": "submit" } ] } }
  ]
}
```

## Gotchas

- **The bundle lives on the parent, the look on the parts.** `pick`, `columns`, `gap`, `title`, `progressText` and the card controls were removed from `bfbe-bundle-builder` on 29 October and belong to Products, Title and Progress; the parent keeps the Bundle group and `disabledOpacity`. <!-- src: docs/SHOP-LABELS-2.0.0.md "BFB Bundle Builder (`bfbe-bundle-builder`)" layout round ; plugins/bfb-elements-pro/elements/bundle-builder.php:11-16 -->
- **No price or fewer than two products, no bundle.** Without **Set price** `price` (with `kind: "price"`) or **Percentage off** `percent` (with `kind: "percent"`), or with fewer than two products to offer, the site gets no markup and no file; the canvas shows a notice. <!-- src: plugins/bfb-elements-pro/elements/bundle-builder.php:228 ; plugins/bfb-elements-pro/elements/bundle-builder.php:245-249 ; plugins/bfb-elements-pro/includes/shop/class-bundle-builder.php:104-108 -->
- **Simple products only.** Variable, grouped and external products, drafts and out-of-stock products are left out without a word; **Products shown** `most` caps the cards at 12 unless set, 24 at most. <!-- src: plugins/bfb-elements-pro/includes/shop/class-bundle-builder.php:163-200 ; docs/elements/bundle-builder.md "Limits" -->
- **Tick boxes need as many cards as the count.** Each box is one product, so with fewer cards shown than **Products to choose** `count` the button never comes on. Use `pick: "stepper"` to let one product fill several places. <!-- src: src/elements/bundle-builder/bundle-builder.js:31-36 ; src/elements/bundle-builder/bundle-builder.js:57 ; plugins/bfb-elements-pro/includes/shop/class-bundle-builder.php:224-240 -->
- **A base Columns value reaches phones.** Unset, the grid shows three columns and two below 768px; a `columns` you set is written on the element's id and outranks that phone rule, so set `columns:mobile_portrait` or `columns:mobile_landscape` as well. <!-- src: src/elements/bundle-builder/bundle-builder.css:14 ; src/elements/bundle-builder/bundle-builder.css:31-32 ; plugins/bfb-elements-pro/elements/bundle-products.php:76-80 ; measured 2026-10-30 on bfb-elements.local /fixture-shop-bundle/ at 500px: `columns: 4` with no phone value drew 4 columns -->
- **The button is marked, not disabled.** Until exactly the count is chosen it carries `aria-disabled="true"` and stays focusable; pressed early it says "Choose 1 more." (or "Take 1 out."). It must be Bricks' Button with `tag: "button"` and no `link`, or it is a `span` or an `a` that submits nothing. <!-- src: src/elements/bundle-builder/bundle-builder.js:57 ; src/elements/bundle-builder/bundle-builder.js:82-89 ; themes/bricks/includes/elements/button.php:11 ; themes/bricks/includes/elements/button.php:169-171 -->
- **Without the Progress, nobody sees the messages.** "Choose 1 more." and the add's sentence are written into `.bfbe-bundle__note`, which only BFB Bundle Progress prints; without it they reach the shop's visually hidden live region alone. <!-- src: src/elements/bundle-builder/bundle-builder.js:38-43 ; plugins/bfb-elements-pro/elements/bundle-progress.php:178-180 -->
- **Each token fills for one kind.** In the Title `{price}` is empty with `kind: "percent"` and `{percent}` is empty with a set price. The set price is entered as the shop enters prices (with or without tax) and shown as it shows them. <!-- src: plugins/bfb-elements-pro/includes/shop/class-bundle-builder.php:135-150 ; docs/elements/bundle-builder.md "Limits" -->
- **A broken bundle goes back to its own prices.** Removing a bundle line or changing a quantity in the cart puts the other lines back to their own prices with WooCommerce's notice; a quantity break on a product gives way to the bundle's price while it is whole. <!-- src: plugins/bfb-elements-pro/includes/shop/class-bundle-builder.php:452-500 ; docs/elements/bundle-builder.md "What the visitor gets" ; docs/elements/bundle-builder.md "Limits" -->
- **The canvas shows the bundle as last saved.** Each part renders on its own in the builder and reads its parent from the saved page: save after changing the bundle. Boxes and steppers are disabled, the note shows a sample, and a press posts nothing. <!-- src: plugins/bfb-elements/includes/abstract-element.php:505-521 ; plugins/bfb-elements-pro/elements/bundle-products.php:300-304 ; plugins/bfb-elements-pro/elements/bundle-progress.php:178-180 ; src/elements/bundle-builder/bundle-builder.js:84 -->
- **No form inside the form, and flex keys need `_display`.** A Bricks Form, Search, Product add to cart, BFB Advanced Forms form or a Bought Together inside it is dropped on the site. The parent takes `_flexDirection`, `_alignItems` and `_gap` only with `_display: "flex"`; nest a Bricks Block for wrapping rows or grids. <!-- src: plugins/bfb-elements-pro/elements/bundle-builder.php:287-288 ; plugins/bfb-elements-pro/includes/shop/class-bought-together.php:253-254 ; themes/bricks/includes/elements/base.php:888-1004 -->

## Never do

- Do not set `pick`, `columns`, `title`, `progressText` or card keys on `bfbe-bundle-builder`; set them on its parts.
- Do not set `count` above the products the source offers with `pick: "box"`.
- Do not set a base `columns` without a phone value when two columns are wanted there.
- Do not give the add button a `link`, or leave out `tag: "button"` and the class `bfbe-bundle__add`.
- Do not leave out BFB Bundle Progress where the visitor must see what is missing or what the add did.
- Do not place another form, Bought Together or Product add to cart inside it.
- Do not set `_flexDirection`, `_alignItems` or `_gap` on the parent without `_display: "flex"`.
- Do not place BFB Bundle Title, Progress or Products outside a `bfbe-bundle-builder`.
