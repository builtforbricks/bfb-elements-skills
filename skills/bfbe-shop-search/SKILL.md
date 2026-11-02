---
name: bfbe-shop-search
description: "Use for the shop's settings on Bricks' Search and Filter - Search: recent and popular searches under the field, the field's padding and the search button set inside it (BFB Shop search, `shop-search`). Read before writing these settings."
---

# BFB Shop search (`shop-search`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the feature switch on (WordPress menu BFB Elements, Elements): `shop-search`. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/shop-search.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/shop-search/

## What it is
A Pro feature with two things for the shop's search: recent and popular searches that open under an empty search box, and synonyms, so a search for one word also finds products holding another. Suggestions go on Bricks' Search and Filter - Search elements and, with a Shop page switch, on WooCommerce's own product search form. Popular searches come from the free Search insights feature, which counts the words shoppers search for, never who searched.

**Not for:** It does not suggest products as the visitor types (Bricks' live search shows results for that) and does not correct spelling. Synonyms do not reach Filter - Search's custom search criteria or the admin's product list.

**Nestable:** no · **In a query loop:** no · **Dynamic data:** no · **Keyboard:** yes · **Reduced motion:** no

## Where it lives
A feature, not an element: its groups are added to Bricks' own elements, on the Content tab after Bricks' own groups. By element:
- Filter - Search (`filter-search`): BFB Search suggestions (`bfbeShopSearch`).
- Search (`search`): BFB Search suggestions (`bfbeShopSearch`), BFB Search field (`bfbeShopSearchLook`).

## Settings that decide the build

### Filter - Search (`filter-search`)

#### BFB Search suggestions (`bfbeShopSearch`)
Pro, switch `shop-search`.
- `bfbeShopSuggest` (checkbox) **Recent and popular searches**. On Bricks' Search and Filter - Search, off by default; ticked, a list opens under the box when it gets the focus while empty, and closes as soon as the visitor types.
Styling, in the schema file: `bfbeShopSuggestBackground`, `bfbeShopSuggestBorder`, `bfbeShopSuggestShadow`, `bfbeShopSuggestPadding`, `bfbeShopSuggestTitleTypography`, `bfbeShopSuggestItemTypography`, `bfbeShopSuggestItemBackground`, `bfbeShopSuggestItemBorder`, `bfbeShopSuggestItemPadding`, `bfbeShopSuggestItemGap`, `bfbeShopSuggestItemHover`, `bfbeShopSuggestClearTypography`.

### Search (`search`)

#### BFB Search suggestions (`bfbeShopSearch`)
The same 15 controls as on `filter-search`.

#### BFB Search field (`bfbeShopSearchLook`)
Pro, switch `shop-search`.
Styling only, every key in the schema file: `bfbeShopSearchFieldPadding`, `bfbeShopSearchFieldMinHeight`, `bfbeShopSearchInside`, `bfbeShopSearchInset`.

## What it guarantees for accessibility (do not undo)
- The list sits right after the box, so Tab reaches it in order, and each search is a button.
- Down from the box goes to the list; Up and Down move, Home and End go to the ends, and Escape closes it and gives the box its focus back.
- Each group is named, Recent searches and Popular searches; the page says once how many suggestions are below the box, and Clear says it cleared.
<!-- bfbe:generated:end -->

## Rendered DOM

The feature adds no element. With **Recent and popular searches** (`bfbeShopSuggest`) on, the server writes `data-bfbe-search` on the host's root: the popular words and the panel's words, as JSON. The script then lays the panel right after the field, inside Bricks' own markup, so Tab reaches it in order:

```html
<div id="brxe-{id}" class="brxe-search" data-bfbe-search='{"popular":["linen","mug"],"words":{…}}'>
  <form role="search" method="get" class="bricks-search-form" action="/">
    <input type="search" name="s" id="search-input-{id}">
    <div class="bfbe-srch" id="bfbe-srch-1" hidden>
      <div class="bfbe-srch__group" role="group" aria-labelledby="{title id}">
        <div class="bfbe-srch__head"><span class="bfbe-srch__title" id="{title id}">Recent searches</span>
          <button type="button" class="bfbe-srch__clear" data-bfbe-srch-clear>Clear</button></div>
        <ul class="bfbe-srch__list"><li><button type="button" class="bfbe-srch__item" data-bfbe-srch-term="linen">linen</button></li></ul>
      </div>
      <div class="bfbe-srch__group" role="group" aria-labelledby="{title id}">…Popular searches, no Clear…</div>
    </div>
    <input type="hidden" name="post_type" value="product">
    <button type="submit" aria-label="Search">…</button>
  </form>
</div>
```

- On Filter - Search the root is Bricks' `div.brxe-filter-search` and the panel follows its `input[data-brx-filter]`. A field whose parent is not positioned gets `bfbe-srch-host` (`position: relative`) on that parent.
- States: `hidden` on the panel while closed; `bfbe-srch--open` on the root while open. The panel is absolute under the field (`z-index: 50`), as wide as the field's positioned parent (Bricks' search form, or the Filter - Search root).
- Where controls write: the Panel controls (`bfbeShopSuggestBackground`, `Border`, `Shadow`, `Padding`) on `.bfbe-srch`, `TitleTypography` on `.bfbe-srch__title`; the Searches controls (`bfbeShopSuggestItem*`) on `.bfbe-srch .bfbe-srch__list .bfbe-srch__item`, with `:hover` and `:focus-visible` for **Hover background**; `bfbeShopSuggestItemGap` on `.bfbe-srch__list`; `ClearTypography` on `.bfbe-srch .bfbe-srch__head .bfbe-srch__clear`.
- **BFB Search field**, on Search only: **Field padding** (`bfbeShopSearchFieldPadding`) and **Field min height** (`bfbeShopSearchFieldMinHeight`) on `input[type=search]`; **Button inside the field** (`bfbeShopSearchInside`) sets `position: absolute; top: 50%; transform: translateY(-50%)` on `button[type=submit]`, and **Button inset** (`bfbeShopSearchInset`) its `right`.

## Wiring to other elements

- **Hub.** Start at `bfbe-shop`. The grid a live search filters is a product loop (`bfbe-shop-loops`); its sort, filters and promo tiles are `bfbe-shop-catalogue`.
- **Filter - Search drives a loop by Bricks' own `filterQueryId`**, the looping element's id; a loop for live search sets `query.is_live_search: true`. A chosen suggestion fills the field and fires the input and Enter Bricks listens for, so the loop re-queries at once.
- **Search sends a form.** A chosen suggestion submits it. Give it `additionalParams` with `paramKey: "post_type"` and `paramValue: "product"`, so the results page is a product search and search insights counts it.
- **Popular searches come from search insights** (the free feature `shop-search-insights`): the most searched words that found something, read once an hour and printed into the page, the same for every visitor and for a cached page.
- **The Shop page** (BFB Elements, Shop, card Search) holds **Show popular searches**, **Popular searches shown** (1 to 10), **Suggestions on the WooCommerce search form** for WooCommerce's own form, and the **Synonyms** rows (Word, Also finds) every product search uses.
- **Recent searches** are the visitor's own last five, kept in their browser (`localStorage`, `bfbe_shop_searches`) as necessary storage, shared by every search box on the site.
- Give the host a class in `_cssClasses` for your own CSS; nothing of the feature targets an element by class or id.

## Verified patterns

**A header search with suggestions and the button inside the field.** From the 2.4 site's demo shop, template "Fernhouse: header" (`bfb-demo-header`): a product search, a pill field with room on the right, the round button set inside it 4px from the end. The demo's `ti-search` icon, uploaded there as an SVG, is written as Bricks' Themify icon; trimmed: the field's and button's colours and typography.

```json
{
  "name": "search",
  "settings": {
    "searchType": "input",
    "placeholder": "Search sofas, rugs, linen, mugs...",
    "additionalParams": [ { "id": "fhsptp", "paramKey": "post_type", "paramValue": "product" } ],
    "inputWidth": "100%",
    "inputHeight": "44",
    "inputBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "999", "right": "999", "bottom": "999", "left": "999" } },
    "icon": { "library": "themify", "icon": "ti-search" },
    "iconWidth": "36",
    "iconHeight": "36",
    "iconBorder": { "width": { "top": "0", "right": "0", "bottom": "0", "left": "0" }, "style": "solid", "radius": { "top": "999", "right": "999", "bottom": "999", "left": "999" } },
    "buttonAriaLabel": "Search",
    "bfbeShopSuggest": true,
    "bfbeShopSearchFieldPadding": { "top": "0", "right": "60", "bottom": "0", "left": "22" },
    "bfbeShopSearchFieldMinHeight": "44px",
    "bfbeShopSearchInside": true,
    "bfbeShopSearchInset": "4px",
    "_cssClasses": "fh-search"
  }
}
```

**A live search over a product loop.** From the fixture "FREE + PRO: Shop search, insights, suggestions and synonyms" (`fixture-shop-search`): Bricks' Filter - Search with suggestions, roomier chips and a wider gap, over a loop set for live search. Set `filterQueryId` to the loop's own element id.

```json
[
  {
    "name": "filter-search",
    "settings": {
      "filterQueryId": "7cdd6c",
      "filterNiceName": "q",
      "placeholder": "Search products",
      "bfbeShopSuggest": true,
      "bfbeShopSuggestItemPadding": { "top": "9px", "right": "15px", "bottom": "9px", "left": "15px" },
      "bfbeShopSuggestItemGap": "11px",
      "_cssClasses": "p10-live"
    }
  },
  {
    "name": "block",
    "settings": { "hasLoop": true, "query": { "objectType": "post", "post_type": ["product"], "is_live_search": true, "posts_per_page": 20 }, "_cssClasses": "p10-search-loop" },
    "children": [ { "name": "product-title", "settings": { "tag": "h3", "linkToProduct": true } } ]
  }
]
```

## Gotchas

- **The panel opens on an empty field with something to show.** It opens on focus while the field is empty, closes as soon as the visitor types, and stays shut when the browser has no recent searches and the shop no popular ones. <!-- src: src/elements/shop-search/shop-search.js:63-68 ; src/elements/shop-search/shop-search.js:92-93 -->
- **Testing as an administrator shows no popular searches.** Administrators, bots and prefetches are never counted, popular words are read once an hour, and a word that only ever found nothing is never offered. Check with a visitor's session. <!-- src: plugins/bfb-elements/includes/shop/class-search-insights.php:61-81 ; plugins/bfb-elements-pro/includes/shop/class-search.php:279-292 ; docs/elements/shop-search.md "What it does not do" -->
- **Popular searches need two switches.** The free feature Search insights must be on (Elements page) and **Show popular searches** on (Shop page, on by default); off, the panel shows recent searches only. <!-- src: plugins/bfb-elements-pro/includes/shop/class-search.php:279-283 ; docs/elements/shop-search.md "Recent and popular searches" -->
- **A Search without the product parameter is not a product search.** Without `additionalParams` `post_type` = `product` WordPress searches every post type, and search insights counts nothing from it. <!-- src: plugins/bfb-elements/includes/shop/class-search-insights.php:95-105 ; docs/elements/shop-search-insights.md "What is counted" -->
- **Bricks' Button settings do not reach the chips.** The chips and Clear are buttons inside Bricks' Search, and their defaults weigh one id and two classes, so `#brxe-… button` rules (Bricks' icon and button controls) stop at the submit button. Style them with the Searches controls; your own CSS needs an id and three classes, as those are written. <!-- src: src/elements/shop-search/shop-search.css:23-47 ; plugins/bfb-elements-pro/includes/shop/class-search.php:185-187 -->
- **Button inside the field needs a submit button and room.** It and **Button inset** target `button[type=submit]` only, which Bricks prints only with an `icon` or `buttonText`; the inset is the button's `right`. Give **Field padding** a right side wider than the button, or the words run under it. <!-- src: plugins/bfb-elements-pro/includes/shop/class-search.php:156-174 ; Bricks searchform.php "if ( $icon || $button_text )" ; dev/demo/shop/10-templates.php:132 -->
- **BFB Search field is the Search element's alone.** Filter - Search has the suggestions group but no field group: size its field with Bricks' own controls. <!-- src: plugins/bfb-elements-pro/includes/shop/class-search.php:49-50 -->
- **A live search counts as the visitor types.** Bricks searches after its pause and minimum length, so "lin" and "linen" may both be counted; a Filter - Search set to apply on Enter counts only what was sent. <!-- src: docs/elements/shop-search-insights.md "What is counted" -->
- **Synonyms reach WordPress' own search only.** They work for the shop's search page, product loops with a search and Bricks' live search on its default engine, not for Bricks' custom search criteria on Filter - Search, and not for exact or sentence searches. Every word of a search is still needed. <!-- src: plugins/bfb-elements-pro/includes/shop/class-search.php:397-411 ; docs/elements/shop-search.md "Synonyms" -->
- **WooCommerce's own form has a switch, its block has nothing.** The form a theme prints through `get_product_search_form()` takes suggestions from the Shop page switch; WooCommerce's product search block draws a form this does not reach. <!-- src: plugins/bfb-elements-pro/includes/shop/class-search.php:340-352 ; docs/elements/shop-search.md "Recent and popular searches" -->
- **It suggests words, not products.** Results as the visitor types are Bricks' live search; the feature does not correct spelling. <!-- src: docs/elements/shop-search.md "What it does not do" -->

## Never do

- Do not leave `additionalParams` `post_type` = `product` off a Search meant for products.
- Do not style the chips with Bricks' Search button controls; use the `bfbeShopSuggestItem*` controls.
- Do not set `bfbeShopSearchInside` on a Search with no `icon` and no `buttonText`.
- Do not set `bfbeShopSearchInside` without a right `bfbeShopSearchFieldPadding` wider than the button.
- Do not look for `bfbeShopSearchFieldPadding` or `bfbeShopSearchInside` on Filter - Search.
- Do not judge the popular searches from an administrator's session.
