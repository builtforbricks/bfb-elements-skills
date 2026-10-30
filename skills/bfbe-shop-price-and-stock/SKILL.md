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

The feature adds no wrapper to either host: its lines and the bar are written into WooCommerce's own price and stock HTML while that one element renders.

```html
<div class="brxe-product-price">
  <p class="price">
    <span class="bfbe-legal bfbe-legal--lowest">Lowest price in the last 30 days: <span class="bfbe-shop-follow" data-bfbe-shop-follow="lowest_price">36,00 €</span></span>  <!-- Position: above -->
    <del>…</del> <ins>…</ins>
    <span class="bfbe-legal bfbe-legal--unit"><span class="bfbe-shop-follow" data-bfbe-shop-follow="unit_price">24,00 €</span> / <span class="bfbe-shop-follow" data-bfbe-shop-follow="meta:_bfbe_net_unit">l</span></span>
  </p>
</div>
<div class="brxe-product-stock">
  <p class="stock low-stock">2 in stock</p>                                      <!-- gone with Position: instead -->
  <div class="bfbe-stock" data-bfbe-stock data-bfbe-stock-base="start" data-bfbe-stock-left="2" data-bfbe-stock-start="3">
    <div class="bfbe-stock__bar" role="progressbar" aria-valuemin="0" aria-valuemax="3" aria-valuenow="2" aria-valuetext="2 of 3 left" aria-labelledby="{text id}" style="--bfbe-stock-pct:67%"><span class="bfbe-stock__fill"></span></div>
    <p class="bfbe-stock__text" id="{text id}">Only <span class="bfbe-shop-follow" data-bfbe-shop-follow="stock_left">2</span> left</p>
  </div>
  <p class="bfbe-stock__sold" data-bfbe-stock-sold="12">12 sold in the last 7 days</p>
</div>
```

- `.bfbe-legal` is a block at 0.875em inside `p.price`; **Lowest price typography** and **Unit price typography** write to `.bfbe-legal--lowest` and `.bfbe-legal--unit`. A line whose follower marker the chosen variation has emptied hides itself (`:has(> .bfbe-shop-follow:empty)`).
- With BFB Tax Switch active, the price paragraph holds `span.bfbe-tax` with an `__incl` and an `__excl` half, and each half carries its own lines.
- The bar: **Height** `bfbeShopStockBarHeight` (8px), **Track colour** and **Border** write to `.bfbe-stock__bar`, **Fill colour** to `.bfbe-stock__fill` (unset, the text colour), **Text typography** to `.bfbe-stock__text`, **Space above** `bfbeShopStockSpace` (.5em) to `.bfbe-stock`. The fill's width is `--bfbe-stock-pct`, and the fill takes the bar's corners.
- States: `bfbe-stock--none` empties the fill at 0 left; `hidden` on `.bfbe-stock` for a chosen variation that does not manage stock. The script rewrites `aria-valuenow`, `aria-valuemax`, `aria-valuetext` and `--bfbe-stock-pct` per variation.
- The sold line is plain text, **Typography** on `.bfbe-stock__sold`, its count in `data-bfbe-stock-sold`.

## Wiring to other elements

- **The product.** Both hosts read the product of the page or of the loop item, and the lines and bar attach to that product's own price and stock alone; a grouped product's children keep theirs.
- **The product's fields.** The unit price needs **Net quantity** and **Unit** on the product's Inventory tab (`_bfbe_net_quantity`, `_bfbe_net_unit`; a variation's own, else the product's). The lowest price reads the price log that **Record price history** on the Shop page keeps (`_bfbe_price_log`).
- **The chosen variation.** With BFB Elements Pro's **Variation data** (`shop-variation`) on, the `bfbe-shop-follow` markers and the bar follow the variation picked in Bricks' Add to cart form; a reset brings the product's figures back. Off, the product's figures stand.
- **BFB Tax Switch** (`bfbe-tax-switch`, skill `bfbe-tax-switch`). It prints both halves of the price with their lines, so the lowest and unit prices switch with it.
- **The same figures as tags.** `{bfbe_product_lowest_price}`, `{bfbe_product_unit_price}`, `{bfbe_product_net_unit}`, `{bfbe_product_stock_left}`, `{bfbe_product_stock_percent}` and `{bfbe_product_sold:30}` print them anywhere, and they also work inside **Text** `bfbeShopStockBarText` and `bfbeShopStockSoldText`. Skill `bfbe-shop-tags-and-conditions`; hub skill `bfbe-shop`.

## Verified patterns

**A product page's price and stock, every line on** (the demo shop's product template, `dev/demo/shop/10-templates.php`, "Price (lowest of 30 days, unit price)" and "Stock (a bar, sold recently)"). The lowest price line has its own words, the unit price reads "per"; the bar is the brand's purple on a tint, 6px high, and the sold line counts 30 days. The demo's typographies and colour variables are left out; colours are plain hex.

```json
{
  "name": "block",
  "settings": { "_rowGap": "12px" },
  "children": [
    { "name": "product-price", "settings": { "bfbeShopLowest": true, "bfbeShopLowestText": "Lowest price in the 30 days before this offer: {price}", "bfbeShopUnit": true, "bfbeShopUnitText": "{price} per {unit}" } },
    { "name": "product-stock", "settings": { "bfbeShopStockBar": true, "bfbeShopStockBarText": "Only {left} left", "bfbeShopStockBarHeight": "6px", "bfbeShopStockBarColor": { "hex": "#6e44ff" }, "bfbeShopStockBarTrack": { "hex": "#f0ecff" }, "bfbeShopStockSold": true, "bfbeShopStockSoldDays": 30, "bfbeShopStockSoldText": "{sold} sold in the last {days} days" } }
  ]
}
```

**Both price lines above the price, in the shop's own words** (template `bfbe-shop-product-p3-off`, the P3 fixture). `bfbeShopLowestPlace` and `bfbeShopUnitPlace` set to `above` put the lines over WooCommerce's price, lowest first.

```json
{ "name": "product-price", "settings": { "bfbeShopLowest": true, "bfbeShopLowestText": "Was at least {price} in the 30 days before this sale", "bfbeShopLowestPlace": "above", "bfbeShopUnit": true, "bfbeShopUnitText": "{price} per {unit}", "bfbeShopUnitPlace": "above" } }
```

**A bar that says the share, and a sold line even at zero** (templates `bfbe-shop-product-p4` and `-p4-reviews`, the P4 fixture, `.p4-stock`). `{percent}` in the bar's text, a year's window for the sold count, and `bfbeShopStockSoldZero` so "0 sold" prints too.

```json
{ "name": "product-stock", "settings": { "bfbeShopStockBar": true, "bfbeShopStockBarText": "Only {left} left ({percent}%)", "bfbeShopStockSold": true, "bfbeShopStockSoldDays": 365, "bfbeShopStockSoldZero": true, "_cssClasses": "p4-stock" } }
```

## Gotchas

- **The lowest price shows only while discounted.** The line prints while the product is on sale in WooCommerce or below its highest price of the last 30 days; otherwise nothing, and `{bfbe_product_lowest_price}` is empty. <!-- src: plugins/bfb-elements/includes/shop/class-legal.php:357-361 ; docs/elements/shop-legal.md "The lowest price of the last 30 days" -->
- **The figure stands on what was recorded.** **Record price history** keeps 60 days from the day it is turned on, so the figure is complete 30 days later; until the log holds a price from before the sale, the regular price stands in. A price changed at display time by another plugin is not in the log. <!-- src: plugins/bfb-elements/includes/shop/class-legal.php:86-90 ; docs/elements/shop-legal.md "What it does not do" -->
- **No net quantity, no unit price.** `bfbeShopUnit` prints nothing for a product without **Net quantity**; the figure is the displayed price over that quantity, so it follows WooCommerce's tax display. <!-- src: plugins/bfb-elements/includes/shop/class-legal.php:123-160 ; plugins/bfb-elements/includes/shop/class-legal.php:177-179 -->
- **The price lines take no dynamic data.** **Lowest price text** fills `{price}` and **Unit price text** `{price}` and `{unit}`; any other brace prints as written. The stock texts do render dynamic data first, then fill `{left}`, `{percent}`, `{start}`, `{sold}` and `{days}`. <!-- src: plugins/bfb-elements/includes/shop/class-legal.php:379-386 ; plugins/bfb-elements-pro/includes/shop/class-stock.php:282-295 ; plugins/bfb-elements-pro/includes/shop/class-stock.php:319-324 -->
- **A variable product speaks for its cheapest variation.** Until a variation is chosen, the lowest price is the cheapest discounted variation's and the unit price the cheapest variation's. They follow the choice only with **Variation data** (`shop-variation`) on. <!-- src: plugins/bfb-elements/includes/shop/class-legal.php:185-198 ; plugins/bfb-elements/includes/shop/class-legal.php:389-394 -->
- **No managed stock, no bar.** `bfbeShopStockBar` draws nothing for a product that does not manage stock, and a chosen variation without stock of its own answers with its parent's. <!-- src: plugins/bfb-elements-pro/includes/shop/class-stock.php:272-276 ; plugins/bfb-elements-pro/includes/shop/class-stock.php:48-57 -->
- **Full means decides the 100%.** The starting stock is the stock the shop first saw (`_bfbe_stock_start`), so after a restock a bar can read "2 of 30 left"; `bfbeShopStockBase: "sold"` measures against stock plus WooCommerce's total sales instead. A variation is always measured against its own starting stock. <!-- src: docs/elements/shop-stock.md "BFB Stock, on Bricks' Product stock" ; plugins/bfb-elements-pro/includes/shop/class-stock.php:60-72 -->
- **No sale, no sold line.** A window with nothing sold prints no line unless **Show when none sold** `bfbeShopStockSoldZero` is ticked. **Days** outside 1 to 365 reads as 7, and the count is paid orders across all variations, recounted at most every ten minutes. <!-- src: plugins/bfb-elements-pro/includes/shop/class-stock.php:309-316 ; docs/elements/shop-stock.md "Sold recently" -->
- **In place of the stock text removes WooCommerce's words.** `bfbeShopStockBarPlace: "instead"` drops "2 in stock" and Bricks' own in-stock, low-stock and out-of-stock texts and typographies with it; the bar's text is then the only words. <!-- src: plugins/bfb-elements-pro/includes/shop/class-stock.php:260-264 -->
- **Each group has its switch.** BFB Price information needs **EU price and product information** (`shop-legal`); BFB Stock is Pro and needs **Stock** (`shop-stock`). Off, the group and its keys leave the panel. <!-- src: plugins/bfb-elements/includes/shop/class-legal.php:46-50 ; plugins/bfb-elements-pro/includes/shop/class-stock.php:37-41 -->
- **Tools, not compliance.** The lines print what is recorded and typed; whether a product counts as reduced under a country's rules is the shop's call. <!-- src: plugins/bfb-elements/includes/shop/class-legal.php:16 ; docs/elements/shop-legal.md -->

## Never do

- Do not expect a lowest price line on a product that is not discounted.
- Do not set `bfbeShopUnit` for products without **Net quantity** and **Unit**; fill the fields first.
- Do not put dynamic data tags in `bfbeShopLowestText` or `bfbeShopUnitText`; use `{price}` and `{unit}` alone.
- Do not set `bfbeShopStockBar` on products that do not manage stock and expect a bar.
- Do not set `bfbeShopStockBarPlace: "instead"` where Bricks' own stock texts must still show.
- Do not tick `bfbeShopStockSoldZero` unless "0 sold" is meant to be said.
- Do not count on the lines or the bar following a variation without **Variation data** (`shop-variation`) on.
