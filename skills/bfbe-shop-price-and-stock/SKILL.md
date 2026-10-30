---
name: bfbe-shop-price-and-stock
description: "Use for the shop's settings on Bricks' Product price and Product stock: the lowest price of 30 days, the unit price, tax notes, the stock bar and the sold count (BFB Shop price and stock, `shop-price-and-stock`). Read before writing these settings."
---

# BFB Shop price and stock (`shop-price-and-stock`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 2.0.0 or later, and BFB Elements Pro 2.0.0 or later for the groups marked Pro, WooCommerce active, the feature switches on (WordPress menu BFB Elements, Elements): `shop-legal`, `shop-stock`. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/shop-price-and-stock.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/shop-price-and-stock/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

## Where it lives
A feature, not an element: its groups are added to Bricks' own elements, on the Content tab after Bricks' own groups. By element:
- Product price (`product-price`): BFB Price information (`bfbeShopPriceInfo`).
- Product stock (`product-stock`): BFB Stock (`bfbeShopStock`).

## Settings that decide the build

### Product price (`product-price`)

#### BFB Price information (`bfbeShopPriceInfo`)
Free, switch `shop-legal`.
- `bfbeShopLowest` (checkbox) **Lowest price (30 days)**
- `bfbeShopLowestText` (text) **Lowest price text**: placeholder Lowest price in the last 30 days: {price}; only when `bfbeShopLowest` is set
- `bfbeShopLowestPlace` (select) **Lowest price position**: options: `below` Below the price (default), `above` Above the price; only when `bfbeShopLowest` is set
- `bfbeShopUnit` (checkbox) **Unit price**
- `bfbeShopUnitText` (text) **Unit price text**: placeholder {price} / {unit}; only when `bfbeShopUnit` is set
- `bfbeShopUnitPlace` (select) **Unit price position**: options: `below` Below the price (default), `above` Above the price; only when `bfbeShopUnit` is set
Styling, in the schema file: `bfbeShopLowestTypography`, `bfbeShopUnitTypography`.

### Product stock (`product-stock`)

#### BFB Stock (`bfbeShopStock`)
Pro, switch `shop-stock`.
- `bfbeShopStockBar` (checkbox) **Show**
- `bfbeShopStockBase` (select) **Full means**: options: `start` The starting stock (default), `sold` Stock plus sold; only when `bfbeShopStockBar` is set
- `bfbeShopStockBarText` (text) **Text**: placeholder Only {left} left; dynamic data accepted; only when `bfbeShopStockBar` is set. {left}, {percent} and {start} are filled in.
- `bfbeShopStockBarPlace` (select) **Position**: options: `below` Below the stock text (default), `above` Above the stock text, `instead` In place of the stock text; only when `bfbeShopStockBar` is set
- `bfbeShopStockSold` (checkbox) **Show**
- `bfbeShopStockSoldDays` (number) **Days**: placeholder 7; only when `bfbeShopStockSold` is set
- `bfbeShopStockSoldText` (text) **Text**: placeholder {sold} sold in the last {days} days; dynamic data accepted; only when `bfbeShopStockSold` is set
- `bfbeShopStockSoldZero` (checkbox) **Show when none sold**: only when `bfbeShopStockSold` is set
Styling, in the schema file: `bfbeShopStockBarHeight`, `bfbeShopStockBarColor`, `bfbeShopStockBarTrack`, `bfbeShopStockBarBorder`, `bfbeShopStockBarTypography`, `bfbeShopStockSpace`, `bfbeShopStockSoldTypography`.
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
