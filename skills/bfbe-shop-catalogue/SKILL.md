---
name: bfbe-shop-catalogue
description: "Use for the shop's catalogue settings on Bricks' Products, Products orderby, Filter - Checkbox and Filter - Radio, Breadcrumbs and looping Containers: promo tiles in a product grid, extra sort orders and the sort dropdown's look, child terms and swatch filters, the brand in the breadcrumbs (BFB Shop catalogue, `shop-catalogue`). Read before writing these settings."
---

# BFB Shop catalogue (`shop-catalogue`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 2.0.0 or later, and BFB Elements Pro 2.0.0 or later for the groups marked Pro, WooCommerce active, the feature switches on (WordPress menu BFB Elements, Elements): `shop-promo-tiles`, `shop-sorting`, `shop-filters`, `shop-swatch-filters`, `shop-brands`. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/shop-catalogue.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/shop/ (the Shop), and a page for each feature this skill spans: https://builtforbricks.com/bfb-elements/docs/shop-promo-tiles/, https://builtforbricks.com/bfb-elements/docs/shop-sorting/, https://builtforbricks.com/bfb-elements/docs/shop-filters/, https://builtforbricks.com/bfb-elements/docs/shop-swatch-filters/, https://builtforbricks.com/bfb-elements/docs/shop-brands/

## What it is
The website documents this by feature; each line is the approved summary from that feature's page.
- `shop-promo-tiles` (https://builtforbricks.com/bfb-elements/docs/shop-promo-tiles/): A Bricks template of your own placed as a card at chosen places in a product grid: a shipping promise after the second product, an editorial tile at the tenth, a gift card tile every eighth card. It works on Bricks' Products element and on a looping Container, Block or Div, and the tile wears the product cards' own classes, so the grid's columns, gaps and card styling reach it.
- `shop-sorting` (https://builtforbricks.com/bfb-elements/docs/shop-sorting/): Five product orders Bricks and WooCommerce lack (SKU, Stock quantity, Total sales, Sale start and Sale end) wherever Bricks offers its own, plus A meta key of your own on the Products element, and a switch that keeps sold-out products at the end of every list whatever the sort. It also gives Bricks' Products orderby element a sort dropdown whose open list you can style.
- `shop-filters` (https://builtforbricks.com/bfb-elements/docs/shop-filters/): Folds the child terms of a hierarchical filter away under their parent, in Bricks' own Filter - Checkbox and Filter - Radio. The filter stays Bricks': its inputs, its counts and its live filtering are untouched, and a branch holding a chosen term opens by itself.
- `shop-swatch-filters` (https://builtforbricks.com/bfb-elements/docs/shop-swatch-filters/): Draws Bricks' Filter - Checkbox and Filter - Radio over a product attribute as swatches: a colour as its colour, a size as its label, a material as its picture, from the swatches you already set in Bricks. A pill look works on any taxonomy. The filter stays Bricks': the same inputs, the same counts, the same live filtering.
- `shop-brands` (https://builtforbricks.com/bfb-elements/docs/shop-brands/): WooCommerce keeps brands in its own Brands taxonomy (Products, Brands). This feature adds the product's brand to Bricks' Breadcrumbs (WooCommerce) element on a product page, and gives any element the brand's names, logo, description and link as dynamic data tags under BFB Shop.

## Where it lives
A feature, not an element: its groups are added to Bricks' own elements, on the Content tab after Bricks' own groups. By element:
- Block, Container and Div (`block`, `container`, `div`): BFB Promo tiles (`bfbeShopPromo`), BFB Sorting (`bfbeShopSorting`).
- Filter - Checkbox and Filter - Radio (`filter-checkbox`, `filter-radio`): BFB Child terms (`bfbeShopFilters`), BFB Swatch look (`bfbeShopSwatchFilters`).
- Breadcrumbs (WooCommerce) (`woocommerce-breadcrumbs`): BFB Brand (`bfbeShopBrand`).
- Products (`woocommerce-products`): BFB Promo tiles (`bfbeShopPromo`), BFB Sorting (`bfbeShopSorting`).
- Products orderby (`woocommerce-products-orderby`): BFB Dropdown (`bfbeShopDropdown`).

## Settings that decide the build

### Block, Container and Div (`block`, `container`, `div`)

#### BFB Promo tiles (`bfbeShopPromo`)
Free, switch `shop-promo-tiles`.
The whole group shows only when `hasLoop` is set.
- `bfbeShopTiles` (repeater) **Tiles**: placeholder Tile; only when `hasLoop` is set
- `bfbeShopTilesFirst` (checkbox) **First page only**: only when `hasLoop` is set and `bfbeShopTiles` is set

#### BFB Sorting (`bfbeShopSorting`)
Free, switch `shop-sorting`.
The whole group shows only when `hasLoop` is set and `query.objectType` is `post`.
- `bfbeShopSoldOutLast` (checkbox) **Sold-out products last**: only when `hasLoop` is set and `query.objectType` is `post`

### Filter - Checkbox and Filter - Radio (`filter-checkbox`, `filter-radio`)

#### BFB Child terms (`bfbeShopFilters`)
Free, switch `shop-filters`.
- `bfbeShopCollapse` (checkbox) **Collapse**: only when `filterSource` is `taxonomy` and `filterHierarchical` is `1`. Folds each parent term's children behind a button.
Styling, in the schema file: `bfbeShopCollapseSize`, `bfbeShopCollapseIconSize`, `bfbeShopCollapseIconColor`, `bfbeShopCollapseBackground`, `bfbeShopCollapseBorder`, `bfbeShopCollapseHover`.

#### BFB Swatch look (`bfbeShopSwatchFilters`)
Pro, switch `shop-swatch-filters`.
- `bfbeShopSwatchLook` (select) **Look**: options: `bricks` As Bricks draws it (default), `swatches` As swatches, `pills` As pills; only when `filterSource` is `taxonomy`. Swatches for an attribute, pills for any taxonomy.
Styling, in the schema file: `bfbeShopSwatchGap`, `bfbeShopSwatchSize`, `bfbeShopSwatchRing`, `bfbeShopSwatchLabelTypography`, `bfbeShopSwatchTipBackground`, `bfbeShopSwatchTipColor`, `bfbeShopPillTypography`, `bfbeShopPillBackground`, `bfbeShopPillBorder`, `bfbeShopPillHoverBorder`, `bfbeShopPillPadding`, `bfbeShopPillOnBackground`, `bfbeShopPillOnColor`.

### Breadcrumbs (WooCommerce) (`woocommerce-breadcrumbs`)

#### BFB Brand (`bfbeShopBrand`)
Free, switch `shop-brands`.
- `bfbeShopBrand` (checkbox) **Show the brand**
- `bfbeShopBrandPlace` (select) **Where**: options: `after_shop` After the home and shop links (default), `categories` In place of the categories; only when `bfbeShopBrand` is set

### Products (`woocommerce-products`)

#### BFB Promo tiles (`bfbeShopPromo`)
The same 2 controls as on `block`, `container`, `div`.

#### BFB Sorting (`bfbeShopSorting`)
Free, switch `shop-sorting`.
- `bfbeShopOrderMeta` (text) **Meta key to order by**: placeholder _my_field; only when `orderby` is `bfbe_meta`
- `bfbeShopSoldOutLast` (checkbox) **Sold-out products last**

### Products orderby (`woocommerce-products-orderby`)

#### BFB Dropdown (`bfbeShopDropdown`)
Free, switch `shop-sorting`.
- `bfbeShopDropLook` (select) **Open list**: options: `native` As the browser draws it (default), `custom` Styled with the controls below. Phones keep their own picker either way.
Styling, in the schema file: `bfbeShopDropTypography`, `bfbeShopDropBackground`, `bfbeShopDropBorder`, `bfbeShopDropPadding`, `bfbeShopDropChevron`, `bfbeShopDropPanelBg`, `bfbeShopDropPanelBorder`, `bfbeShopDropPanelShadow`, `bfbeShopDropPanelPadding`, `bfbeShopDropOptTypography`, `bfbeShopDropOptPadding`, `bfbeShopDropOptHover`, `bfbeShopDropHoverText`, `bfbeShopDropOptOnBg`, `bfbeShopDropOptOnColor`, `bfbeShopDropTick`.
<!-- bfbe:generated:end -->

## Rendered DOM

The feature adds no element. It writes classes and attributes on the host's root, CSS at the host's id, and a few parts inside Bricks' own markup.

- **Promo tiles** add one cell per tile to the grid, rendered on the server: in Bricks' Products element `<li class="product … bfbe-promo-tile" data-bfbe-promo="5">` inside `ul.products`; in a looping Block, Container or Div an element with the loop item's own tag and classes (its `brxe-{id}` and `_cssClasses` included) plus `bfbe-promo-tile`. The template renders inside through Bricks' `[bricks_template]`; `data-bfbe-promo` holds the card number.
- **Sorting** draws nothing: the orders and **Sold-out products last** (`bfbeShopSoldOutLast`) are SQL on the query.
- **BFB Dropdown** with **Open list** `bfbeShopDropLook: "custom"` adds `bfbe-dd` and `data-bfbe-dd` to the Products orderby root. The `select` stays the control (`aria-haspopup="listbox"`, `aria-expanded`, `aria-controls`); the script appends `ul.bfbe-dd__panel[role="listbox"]` of `li.bfbe-dd__opt[role="option"]` inside `form.woocommerce-ordering`. States: `is-open` on the form, `bfbe-dd--end` when the list opens from the right edge, `.is-active` on the option under the pointer or keys, `aria-selected="true"` on the chosen one.
- Where the dropdown controls write: `bfbeShopDropTypography`, `Background`, `Border`, `Padding` on `.woocommerce-ordering select` in both looks; `Chevron` and `Tick` as `--bfbe-dd-chevron` and `--bfbe-dd-tick` on the root; `Panel*` on `.bfbe-dd__panel`; `Opt*` and `HoverText` on `.bfbe-dd__opt`, `.is-active` and `[aria-selected="true"]`.
- **Collapse** (`bfbeShopCollapse`) adds `bfbe-filt` and `data-bfbe-filt` (the button's words) to the filter's root. The script gives each `li` with child terms the class `bfbe-filt__parent` and a `button.bfbe-filt__toggle[aria-expanded][aria-controls]` named "What is in {term}"; a folded child `li` takes `bfbe-filt__in` (`display: none !important`). `bfbeShopCollapse*` controls write `.bfbe-filt__toggle` and its `svg`.
- **BFB Swatch look** adds `bfbe-swf` and `bfbe-swf--color|label|image|pills` to the filter's root (Bricks 2.4 wraps its list in a fieldset; the class is on Bricks' root either way). Bricks' input stays, visually hidden and focusable; its `span.brx-option-text` becomes the face:

```html
<li><label><input type="checkbox" value="ink">
  <span class="brx-option-text bfbe-swf__face bfbe-swf__face--color" data-bfbe-swf-name="Ink" style="--bfbe-swf-color:#1d2433">Ink <span class="brx-option-count">(3)</span></span>
</label></li>
```

- A swatch is the face's `::before` (`--bfbe-swf-size`, ring `--bfbe-swf-ring`), the tooltip its `::after` (`bfbeShopSwatchTip*`). An image term sets `--bfbe-swf-image`; a label term `bfbe-swf__face--label` with `data-bfbe-swf-label`. Pills: the span takes `bfbe-swf__pill` and keeps Bricks' words and count; `bfbeShopPill*` write `.bfbe-swf__pill` and `input:checked ~ .bfbe-swf__pill`. The radio filter's "All" takes `bfbe-swf__all`. `bfbeShopSwatchGap` sets `--bfbe-swf-gap` on the root.
- **BFB Brand** adds a crumb to WooCommerce's own trail (name and link to the brand archive), so the element's separators, home label and schema stay Bricks' and WooCommerce's.

## Wiring to other elements

- **Hub and neighbours.** Start at `bfbe-shop`. The product sets a query loop can show are `bfbe-shop-loops`; the brand tags (`{bfbe_product_brand}`, `{bfbe_product_brand_logo}`) are `bfbe-shop-tags-and-conditions`; swatches on a card's Add to cart are `bfbe-shop-add-to-cart`; grid, list, columns and per page are `bfbe-view-switch`.
- **Filters find their loop by Bricks' own `filterQueryId`**, the looping element's id or the Products element's id. Collapse, swatches and pills add nothing to that link and are redrawn after every live query, since the output filter runs on Bricks' query result too.
- **The new orders in each place.** Products element: `orderby: "bfbe_sku"` (or `bfbe_stock`, `bfbe_sales`, `bfbe_sale_start`, `bfbe_sale_end`, `bfbe_meta`) with `order`. Looping element: `query.orderby` with the same five keys and `query.order`. Bricks' Sort filter (`filterAction: "sort"`): a `sortOptions` row with `optionSource: "bfbe_sales"` and `optionOrder: "DESC"`.
- **The catalogue dropdown's choices** are `bfbe_sku`, `bfbe_stock-desc`, `bfbe_sales-desc`, `bfbe_sale_start-desc` and `bfbe_sale_end`: in the Products orderby element's `orderby` list, or the Products element's `sortbyOptions` with `beforeGrid: ["orderby"]`.
- **The Shop page** (BFB Elements, Shop, card Sorting) holds what the archive's main query cannot take from an element: sold-out products last on the shop and category pages, and the new choices in WooCommerce's own dropdown.
- **Where Bricks' swatches come from.** Swatch colours, labels and images are the ones set for Bricks' Add to cart (WooCommerce, Products, Attributes, each attribute's swatch type and each term's value). Nothing is set twice.
- Give a host a class in `_cssClasses` for your own CSS; nothing of the feature targets an element by class or id.

## Verified patterns

**A product grid with a promo tile and sold-out products last.** The first tree is the 2.4 site's demo shop archive, template "Fernhouse: product archive" (`bfb-demo-archive`): a looping Block on the archive's main query, sold-out products after the rest, a promo tile as the fifth card on the first page only. Trimmed: the card's look, badges, wishlist and compare. The second is the fixture "FREE: Shop promo tiles" (`fixture-shop-promo`): Bricks' Products element sorted by SKU, tiles at the third and tenth card. Set `template` to a section or content template of the target site.

```json
[
  {
    "name": "block",
    "settings": { "_display": "grid", "_gridTemplateColumns": "repeat(3, minmax(0, 1fr))", "_gridGap": "32px 24px", "_cssClasses": "fh-archive-grid" },
    "children": [
      {
        "name": "block",
        "settings": {
          "hasLoop": true,
          "query": { "objectType": "post", "post_type": ["product"], "is_archive_main_query": true, "posts_per_page": 12 },
          "bfbeShopSoldOutLast": true,
          "bfbeShopTiles": [ { "id": "fhtile", "template": "6445", "position": 5 } ],
          "bfbeShopTilesFirst": true,
          "_cssClasses": "fh-card fh-archive-loop"
        },
        "children": [
          { "name": "image", "settings": { "image": { "useDynamicData": "{featured_image}", "size": "woocommerce_single" }, "link": { "type": "external", "url": "{post_url}" } } },
          { "name": "text-basic", "settings": { "text": "{bfbe_product_brand}", "_cssClasses": "fh-card__brand" } },
          { "name": "product-title", "settings": { "tag": "h3", "linkToProduct": true } },
          { "name": "product-price", "settings": {} },
          { "name": "product-add-to-cart", "settings": { "bfbeShopCardSwatches": true } }
        ]
      }
    ]
  },
  {
    "name": "woocommerce-products",
    "settings": {
      "columns": 3,
      "posts_per_page": 12,
      "orderby": "bfbe_sku",
      "order": "ASC",
      "bfbeShopTiles": [ { "id": "tile01", "template": "80113", "position": 3 }, { "id": "tile02", "template": "80113", "position": 10 } ],
      "_cssClasses": "promo-products"
    }
  }
]
```

**Filters drawn as pills and swatches.** From the same demo archive: categories as pills with their child terms folded, and colours as swatches with Bricks' counts hidden. Both point at the archive loop by `filterQueryId`; use the target loop's own id. Trimmed: the pills' typography and the demo's colour variables.

```json
[
  {
    "name": "filter-checkbox",
    "settings": {
      "filterQueryId": "2c8e19",
      "filterSource": "taxonomy",
      "filterTaxonomy": "product_cat",
      "filterHierarchical": true,
      "filterHideEmpty": true,
      "filterNiceName": "cat",
      "bfbeShopCollapse": true,
      "bfbeShopSwatchLook": "pills",
      "bfbeShopPillBackground": { "hex": "#ffffff" },
      "bfbeShopPillBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "999", "right": "999", "bottom": "999", "left": "999" } },
      "bfbeShopPillOnBackground": { "hex": "#101828" },
      "bfbeShopPillOnColor": { "hex": "#ffffff" }
    }
  },
  {
    "name": "filter-checkbox",
    "settings": {
      "filterQueryId": "2c8e19",
      "filterSource": "taxonomy",
      "filterTaxonomy": "pa_colour",
      "filterHideEmpty": true,
      "filterHideCount": true,
      "filterNiceName": "colour",
      "bfbeShopSwatchLook": "swatches",
      "bfbeShopSwatchSize": "30"
    }
  }
]
```

**The sort dropdown and the brand in the trail.** The dropdown is the demo archive's: Bricks' Products orderby offering two of the new orders, with the styled open list. The breadcrumbs are the demo product template's (`bfb-demo-product`), the brand after the home and shop links. Trimmed: the field's and the options' typography.

```json
[
  {
    "name": "woocommerce-products-orderby",
    "settings": {
      "orderby": ["menu_order", "popularity", "rating", "date", "price", "price-desc", "bfbe_sales-desc", "bfbe_sale_end"],
      "bfbeShopDropLook": "custom",
      "bfbeShopDropBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "999", "right": "999", "bottom": "999", "left": "999" } },
      "bfbeShopDropPadding": { "top": "10", "right": "18", "bottom": "10", "left": "18" },
      "bfbeShopDropPanelBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "16", "right": "16", "bottom": "16", "left": "16" } },
      "bfbeShopDropOptOnBg": { "hex": "#f0ecff" },
      "bfbeShopDropOptOnColor": { "hex": "#6e44ff" },
      "bfbeShopDropTick": { "hex": "#6e44ff" }
    }
  },
  {
    "name": "woocommerce-breadcrumbs",
    "settings": { "separatorType": "text", "separatorText": "/", "bfbeShopBrand": true, "bfbeShopBrandPlace": "after_shop" }
  }
]
```

## Gotchas

- **The loop groups need a loop.** BFB Promo tiles shows on a Block, Container or Div only with `hasLoop`; BFB Sorting also needs `query.objectType: "post"`. Tiles go into a Posts loop only, never a terms or users loop, nor Bricks' Carousel or Slider. <!-- src: plugins/bfb-elements/includes/shop/class-promo-tiles.php:111 ; plugins/bfb-elements/includes/shop/class-promo-tiles.php:306 ; plugins/bfb-elements/includes/shop/class-sorting.php:357 ; docs/elements/shop-promo-tiles.md "What it does not do" -->
- **Card numbers count cells, tiles included.** A tile at 3 and one at 10 put eight products between them; a tile falling straight after the page's last product is placed after it, one further out is not drawn, and a page with no products draws none. A template that is not published is skipped. <!-- src: plugins/bfb-elements/includes/shop/class-promo-tiles.php:145 ; plugins/bfb-elements/includes/shop/class-promo-tiles.php:165-187 ; docs/elements/shop-promo-tiles.md "The controls" -->
- **A tile has no product.** Dynamic data in its template resolves against the page. The tile wears the cards' classes, so the card's look reaches it; set the template's section to fill the cell if the tile should. On Bricks 2.3 the canvas shows a tile change after a save and reload. <!-- src: docs/elements/shop-promo-tiles.md "What the visitor gets" ; src/elements/shop-promo-tiles/shop-promo-tiles.css:5-7 -->
- **The archive's main query ignores the element's switch on first load.** A loop with `is_archive_main_query` reuses WooCommerce's query, which carries no element settings: turn on **Sold-out products last on shop archives** on the Shop page too. The element's switch then covers Bricks' live re-queries. <!-- src: Bricks includes/query.php:1248 ; plugins/bfb-elements/includes/shop/class-sorting.php:481-487 ; dev/demo/shop/30-settings.php:141 -->
- **A meta key order is the Products element's alone.** `orderby: "bfbe_meta"` with **Meta key to order by** (`bfbeShopOrderMeta`) exists only there, and the key is lower-cased by `sanitize_key`; a looping element uses Bricks' own Meta value orders. <!-- src: plugins/bfb-elements/includes/shop/class-sorting.php:139-150 ; plugins/bfb-elements/includes/shop/class-sorting.php:470-474 -->
- **A product without the value sorts last, either way.** No SKU, no managed stock or no sale date puts it after the rest in both directions. A variable product's sale dates live on its variations, which the sale orders do not read. <!-- src: plugins/bfb-elements/includes/shop/class-sorting.php:546-554 ; docs/elements/shop-sorting.md "The orders" -->
- **Sold out means WooCommerce's out-of-stock status.** A product on back-order is not moved, and with WooCommerce's **Hide out of stock items from the catalog** on there is nothing to move. <!-- src: plugins/bfb-elements/includes/shop/class-sorting.php:539 ; docs/elements/shop-sorting.md "Sold-out products last" -->
- **The styled open list is the Products orderby element's, for a mouse.** The Products element's own toolbar dropdown takes the new choices but not the BFB Dropdown look. Field controls apply in both looks; the arrow, list and option controls show only with `bfbeShopDropLook: "custom"`; a phone or any pointer that cannot hover keeps the browser's picker. <!-- src: plugins/bfb-elements/includes/shop/class-sorting.php:61 ; plugins/bfb-elements/includes/shop/class-sorting.php:212-243 ; src/elements/shop-sorting/shop-sorting.js:44 -->
- **Collapse needs a tree.** It shows only with `filterSource: "taxonomy"` and Bricks' `filterHierarchical`, does nothing on a list with no child term, and folds nothing without the script. With Bricks' **Visible options limit** also on, Bricks counts the folded children in its "Show more" number. <!-- src: plugins/bfb-elements/includes/shop/class-filters.php:49 ; plugins/bfb-elements/includes/shop/class-filters.php:108-113 ; docs/elements/shop-filters.md "Show more is Bricks' own" -->
- **Swatches are for product attributes.** `bfbeShopSwatchLook: "swatches"` on a taxonomy that is not a `pa_` attribute leaves the filter as Bricks draws it; use `pills` for categories, brands or tags. Colours and pictures need Bricks' variation swatches switched on (Bricks, Settings, WooCommerce); off, every term is a label. <!-- src: plugins/bfb-elements-pro/includes/shop/class-swatch-filters.php:177 ; plugins/bfb-elements-pro/includes/shop/class-cards.php:691 -->
- **Each look's controls show only with that look.** `bfbeShopSwatchSize`, `Ring`, `LabelTypography` and `Tip*` need `swatches`; `bfbeShopPill*` need `pills`; `bfbeShopSwatchGap` takes either. Filter - Select is never drawn as swatches. <!-- src: plugins/bfb-elements-pro/includes/shop/class-swatch-filters.php:48-77 ; docs/elements/shop-swatch-filters.md "What it does not do" -->
- **The brand is a single product's.** It needs WooCommerce's Brands taxonomy (`product_brand`), shows on a product page only, takes the first brand by name (filter `bfbe_shop_brand_term`), and leaves a product without a brand, and every archive trail, as it was. <!-- src: plugins/bfb-elements/includes/shop/class-brands-breadcrumbs.php:59 ; plugins/bfb-elements/includes/shop/class-brands-breadcrumbs.php:93-98 ; docs/elements/shop-brands.md "The brand in the shop breadcrumbs" -->

## Never do

- Do not rely on `bfbeShopSoldOutLast` alone on a loop with `is_archive_main_query`; switch on the Shop page's archive setting too.
- Do not set `orderby: "bfbe_meta"` on a looping element's query; it is the Products element's order.
- Do not set `bfbeShopSwatchLook: "swatches"` on a taxonomy that is not a `pa_` attribute; use `pills`.
- Do not set `bfbeShopDropChevron`, `bfbeShopDropPanel*`, `bfbeShopDropOpt*` or `bfbeShopDropTick` without `bfbeShopDropLook: "custom"`.
- Do not expect the BFB Dropdown look on the Products element's toolbar dropdown; place Bricks' Products orderby element.
- Do not set `bfbeShopCollapse` without `filterSource: "taxonomy"` and `filterHierarchical: true`.
- Do not put product dynamic data in a promo tile's template.
