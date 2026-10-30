---
name: bfbe-shop-catalogue
description: "Use for the shop's catalogue settings on Bricks' Products, Products orderby, Filter - Checkbox and Filter - Radio, Breadcrumbs and looping Containers: promo tiles in a product grid, extra sort orders and the sort dropdown's look, child terms and swatch filters, the brand in the breadcrumbs (BFB Shop catalogue, `shop-catalogue`). Read before writing these settings."
---

# BFB Shop catalogue (`shop-catalogue`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 2.0.0 or later, and BFB Elements Pro 2.0.0 or later for the groups marked Pro, WooCommerce active, the feature switches on (WordPress menu BFB Elements, Elements): `shop-promo-tiles`, `shop-sorting`, `shop-filters`, `shop-swatch-filters`, `shop-brands`. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/shop-catalogue.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/shop-catalogue/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

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

_Not written yet._

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
