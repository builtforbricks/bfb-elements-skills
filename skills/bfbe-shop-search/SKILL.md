---
name: bfbe-shop-search
description: "Use for the shop's settings on Bricks' Search and Filter - Search: recent and popular searches, product suggestions and the search field's look (BFB Shop search, `shop-search`). Read before writing these settings."
---

# BFB Shop search (`shop-search`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the feature switch on (WordPress menu BFB Elements, Elements): `shop-search`. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/shop-search.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/shop-search/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

## Where it lives
A feature, not an element: its groups are added to Bricks' own elements, on the Content tab after Bricks' own groups. By element:
- Filter - Search (`filter-search`): BFB Search suggestions (`bfbeShopSearch`).
- Search (`search`): BFB Search suggestions (`bfbeShopSearch`), BFB Search field (`bfbeShopSearchLook`).

## Settings that decide the build

### Filter - Search (`filter-search`)

#### BFB Search suggestions (`bfbeShopSearch`)
Pro, switch `shop-search`.
- `bfbeShopSuggest` (checkbox) **Recent and popular searches**
Styling, in the schema file: `bfbeShopSuggestBackground`, `bfbeShopSuggestBorder`, `bfbeShopSuggestShadow`, `bfbeShopSuggestPadding`, `bfbeShopSuggestTitleTypography`, `bfbeShopSuggestItemTypography`, `bfbeShopSuggestItemBackground`, `bfbeShopSuggestItemBorder`, `bfbeShopSuggestItemPadding`, `bfbeShopSuggestItemGap`, `bfbeShopSuggestItemHover`, `bfbeShopSuggestClearTypography`.

### Search (`search`)

#### BFB Search suggestions (`bfbeShopSearch`)
The same 15 controls as on `filter-search`.

#### BFB Search field (`bfbeShopSearchLook`)
Pro, switch `shop-search`.
Styling only, every key in the schema file: `bfbeShopSearchFieldPadding`, `bfbeShopSearchFieldMinHeight`, `bfbeShopSearchInside`, `bfbeShopSearchInset`.
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
