---
name: bfbe-rating-summary
description: "Use when showing a product's average rating and one bar per star with `bfbe-rating-summary`, each bar filtering the reviews to that rating, or placing the average and the bars apart in Bricks containers."
---

# BFB Rating Summary (`bfbe-rating-summary`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-rating-summary.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/rating-summary/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 0.67 KB, JS none (gzipped), no dependencies, loaded only on pages that use it.

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Summary (`bfbeSummary`)
- `shows` (select) **Shows**: options: `both` Summary and bars (default), `summary` Summary only, `bars` Bars only
- `text` (text) **Text**: placeholder {average} out of 5, from {count} reviews; dynamic data accepted; only when `shows` is not `bars`. {average}, {count} and {max} are filled in.
- `none` (text) **No reviews yet**: placeholder No reviews yet; dynamic data accepted; only when `shows` is not `bars`
- `stars` (checkbox) **Stars**: only when `shows` is not `bars`
Styling, in the schema file: `textTypography`, `averageTypography`, `summaryGap`, `summaryJustify`, `summaryAlign`, `starsSize`, `starsColor`, `starsEmptyColor`.

### Bars (`bfbeBars`)
The whole group shows only when `shows` is not `summary`.
- `order` (select) **Order**: options: `desc` 5 stars first (default), `asc` 1 star first
- `figure` (select) **Beside each bar**: options: `count` The count (default), `percent` The share in percent, `both` Both, `none` Nothing
- `links` (select) **Filter the reviews**: options: `yes` Yes, as links (default), `no` No
- `anchor` (text) **Review list anchor**: placeholder #reviews; only when `links` is not `no`
- `allText` (text) **Show all**: placeholder Show all reviews; dynamic data accepted; only when `links` is not `no`
Styling, in the schema file: `barHeight`, `barColor`, `trackColor`, `barBorder`, `rowGap`, `columnGap`, `labelWidth`, `barTypography`, `figuresTypography`, `rowHoverColor`, `rowHoverFill`, `rowChosenColor`, `allTypography`, `allBackground`, `allBorder`, `allPadding`, `allHoverBackground`, `allHoverColor`.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<div id="brxe-{id}" class="brxe-bfbe-rating-summary bfbe-rating">
  <div class="bfbe-rating__summary" id="{uid}-summary">
    <span class="bfbe-rating__stars" aria-hidden="true"><div class="star-rating" …>…</div></span>
    <span class="bfbe-rating__words"><span class="bfbe-rating__average">4,4</span> out of 5, from <span class="bfbe-rating__count">23</span> reviews</span>
  </div>
  <ul class="bfbe-rating__bars" aria-labelledby="{uid}-summary">
    <li class="bfbe-rating__item">
      <a class="bfbe-rating__row" href="{product URL}?bfbe_stars=5#reviews" title="Show the 5-star reviews" aria-current="true">
        <span class="bfbe-rating__label">5 stars</span>
        <meter class="bfbe-rating__meter" min="0" max="23" value="12" aria-label="5 stars: 12 reviews" style="--bfbe-rating-pct:52%">…</meter>
        <span class="bfbe-rating__figures"><span class="bfbe-rating__n">12</span><span class="bfbe-rating__pct">52%</span></span>
      </a>
    </li>
    …
  </ul>
  <a class="bfbe-rating__all bfbe-chip" href="{product URL}#reviews">Show all reviews</a>
</div>
```

- Root `div.bfbe-rating`. **Shows** (`shows`) `summary` prints the `.bfbe-rating__summary` alone; `bars` prints the list alone, named by an `aria-label` carrying the same sentence instead of `aria-labelledby`.
- A product with no reviews prints `p.bfbe-rating__summary.bfbe-rating__summary--none` with the **No reviews yet** words, and no bars.
- `.bfbe-rating__stars` is WooCommerce's own `.star-rating` markup, only with **Stars** (`stars`) ticked, hidden from screen readers. A star with no reviews gets `bfbe-rating__item--empty` (opacity .6) and keeps a zero bar.
- Each bar is a real `meter`, drawn as a gradient on itself from `--bfbe-rating-pct`. Rows are links with **Filter the reviews** (`links`) at its default, spans with `links: "no"`; the row of the rating being shown carries `aria-current="true"`.
- The **Show all** chip `a.bfbe-rating__all` appears on the page only while a star filter is on.
- Where controls write: `barHeight`, `barColor` and `trackColor` set `--bfbe-rating-h`, `--bfbe-rating-fill` and `--bfbe-rating-track` on the root (fill defaults to `currentColor`); `barBorder` to `.bfbe-rating__meter`; `rowGap` to `.bfbe-rating__bars`; `columnGap` and `barTypography` to `.bfbe-rating__row`; `labelWidth` to `.bfbe-rating__label` (4.5em); `textTypography`, `summaryGap`, `summaryJustify` and `summaryAlign` to `.bfbe-rating__summary`; `averageTypography` to `.bfbe-rating__average`; `stars*` to `.star-rating`; `all*` to `.bfbe-rating__all`.
- No script: every figure and link is printed by the server.

## Wiring to other elements

- **The lists it filters.** Each bar links to the product's address with `?bfbe_stars=N` and the **Review list anchor** (`anchor`, `#reviews` when empty). Bricks' Product reviews, the Reviews tab of Product tabs and every BFB Shop reviews loop of this product read the parameter and show only that rating (skill `bfbe-shop-reviews`).
- **The anchor.** `#reviews` is WooCommerce's block inside Bricks' Product reviews. For a page whose list is a reviews loop, set `anchor` to the id of the loop's section; an anchor link can only land on an id, so this is the one place an id is needed.
- **BFB Review Sort** keeps the stars filter in its form, so sorting a filtered list stays filtered; the bar links drop any sort.
- **Two instances, placed apart.** One with `shows: "summary"` and one with `shows: "bars"` go in any Bricks container, side by side in a grid or far apart; each reads the same product figures.
- **Stars elsewhere.** Leave **Stars** off and place Bricks' own Product rating (`product-rating`) where the stars belong; the summary's stars always come before its words.
- Give an instance a class in `_cssClasses` for your own CSS; nothing targets it by attribute. The bar colours are custom properties, so a global class can set `--bfbe-rating-fill` and `--bfbe-rating-track` too.

## Verified patterns

**The summary and its bars in the review column.** From the demo shop's product template (Fernhouse product page, section "Reviews", the summary and sort column). WooCommerce's stars before the words, the count beside each bar, bars 8 px tall in the star colour on a pale track. Trimmed: the brand's colour variables (hex kept) and the typography.

```json
{
  "name": "block",
  "settings": { "_rowGap": "20px", "_cssClasses": "reviews-aside" },
  "children": [
    { "name": "heading", "settings": { "text": "What people say", "tag": "h2" } },
    { "name": "bfbe-rating-summary", "settings": { "stars": true, "text": "{average} out of 5, from {count} reviews", "figure": "count", "barHeight": "8", "barColor": { "hex": "#f5a524" }, "trackColor": { "hex": "#e9ecf1" }, "barBorder": { "width": { "top": "0", "right": "0", "bottom": "0", "left": "0" }, "style": "solid", "radius": { "top": "999", "right": "999", "bottom": "999", "left": "999" } }, "rowGap": "8", "_cssClasses": "reviews-summary" } },
    { "name": "bfbe-review-sort", "settings": { "label": "Sort reviews" } }
  ]
}
```

**The average beside the bars, two instances.** From the fixture template `bfbe-shop-product-p4-reviews` ("Placed apart: the average beside the bars"). A Bricks grid holds an instance with `shows: "summary"`, its sentence shortened to "{average} of {max}" and centred, and one with `shows: "bars"` showing each bar's share in percent. Use on a product template.

```json
{
  "name": "block",
  "settings": { "_display": "grid", "_gridTemplateColumns": "200px 1fr", "_columnGap": "32px", "_alignItems": "center", "_cssClasses": "rating-apart" },
  "children": [
    { "name": "bfbe-rating-summary", "settings": { "shows": "summary", "stars": true, "text": "{average} of {max}", "summaryJustify": "center", "_cssClasses": "rating-average" } },
    { "name": "bfbe-rating-summary", "settings": { "shows": "bars", "figure": "percent", "_cssClasses": "rating-bars" } }
  ]
}
```

## Gotchas

- **Bars alone print nothing for a product without reviews.** `shows: "bars"` with no reviews leaves the page empty (the canvas says so); the summary placed elsewhere says "No reviews yet". The other two settings print that sentence and no bars. <!-- src: plugins/bfb-elements-pro/elements/rating-summary.php:473-490 -->
- **Not a product, nothing printed.** Off a product template or outside a product's query loop the element prints nothing; in the builder, set the template's preview product. <!-- src: plugins/bfb-elements-pro/elements/rating-summary.php:450-457 -->
- **The bars filter by a page load.** A bar is a plain link to `?bfbe_stars=N` plus the anchor, so the page reloads at the list; the element has no script. <!-- src: plugins/bfb-elements-pro/elements/rating-summary.php:534-537 ; docs/elements/rating-summary.md "What works without JavaScript" -->
- **A wrong anchor lands nowhere.** With the reviews in a loop and no Product reviews on the page, `#reviews` does not exist; set `anchor` to the section's id. The value is cleaned to a class-safe word, the `#` optional. <!-- src: plugins/bfb-elements-pro/elements/rating-summary.php:467-468 -->
- **A loop of all or chosen products ignores the filter.** Only a BFB Shop reviews loop of **This product** and Bricks' review lists read `bfbe_stars`. <!-- src: plugins/bfb-elements-pro/includes/shop/class-reviews.php:1067-1070 -->
- **The canvas shows spans and the chip.** In the builder the rows are not links and the **Show all** chip always shows, so its controls style something; on the page the chip appears only while a filter is on. <!-- src: plugins/bfb-elements-pro/elements/rating-summary.php:534 ; plugins/bfb-elements-pro/elements/rating-summary.php:544-549 -->
- **The figures are WooCommerce's.** The average, the count and the count per star come from WooCommerce's stored product figures, a variation reading its parent's; a review approved straight in the database shows only once WooCommerce recounts. <!-- src: plugins/bfb-elements-pro/includes/shop/class-rating-summary.php:54-63 ; docs/elements/rating-summary.md "What it does not do" -->
- **Text knows three words.** `{average}` (one decimal, the site's separator), `{count}` and `{max}` are filled in; any other brace prints as typed. With `shows: "bars"` the panel hides **Text**, and the list's name is the default sentence. <!-- src: plugins/bfb-elements-pro/elements/rating-summary.php:493-499 ; plugins/bfb-elements-pro/elements/rating-summary.php:516 -->
- **Stars size, colours and Show all need their switches.** `starsSize`, `starsColor` and `starsEmptyColor` show only with `stars` ticked; the `all*`, hover and chosen keys only while `links` is not `no`. <!-- src: plugins/bfb-elements-pro/elements/rating-summary.php:55 ; plugins/bfb-elements-pro/elements/rating-summary.php:329-424 -->
- **The bar is the text colour until coloured.** `--bfbe-rating-fill` defaults to `currentColor` and the track to the pack's surface tone; set `barColor` and `trackColor` for the brand's. <!-- src: src/elements/rating-summary/rating-summary.css:2 -->

## Never do

- Do not place a `shows: "bars"` instance on its own for products that may have no reviews; pair it with a summary instance.
- Do not set `starsSize`, `starsColor` or `starsEmptyColor` without `stars: true`.
- Do not set `anchor`, `allText` or the `all*` keys with `links: "no"`.
- Do not leave `anchor` at `#reviews` on a page whose only list is a reviews loop; point it at that section's id.
- Do not expect the bars to filter a reviews loop of all or chosen products.
- Do not set `text` on a `shows: "bars"` instance; the panel hides it.
