---
name: bfbe-review-sort
description: "Use when letting shoppers sort a product's reviews (newest, highest rated, most helpful, with photos) with `bfbe-review-sort`, a dropdown or radio chips placed anywhere on the product page."
---

# BFB Review Sort (`bfbe-review-sort`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-review-sort.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/review-sort/

## What it is
The shopper's choice of review order, as a dropdown or radio buttons, placed wherever you like on a product page: beside the rating summary, above the reviews, in a sticky bar. It sorts Bricks' Product reviews (and the Reviews tab of Product tabs) and a BFB Shop reviews loop of this product's reviews, wherever they sit on the page. It is a real form, so it works without JavaScript, and each order has its own address.

**Not for:** It sorts this product's reviews only: a reviews loop of all products, or of chosen products, keeps its own order. The order a list opens in belongs to the list, so set that on Bricks' Product reviews or the loop.

**Costs a page:** CSS none, JS none (gzipped), plus shop-reviews, loaded only on pages that use it.

**Nestable:** no · **In a query loop:** no · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** no

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Sort (`bfbeSort`)
- `as` (select) **Show as**: options: `select` A dropdown (default), `radios` Radio buttons. A dropdown by default, or Radio buttons, the choices side by side.
- `label` (text) **Label**: placeholder Sort reviews; dynamic data accepted. Sort reviews when empty; dynamic data works.
Styling, in the schema file: `labelTypography`, `gap`.

### Dropdown (`bfbeDropdown`)
The whole group shows only when `as` is not `radios`.
- `look` (select) **Open list**: options: `native` As the browser draws it (default), `custom` Styled with the controls below. As the browser draws it by default, or Styled with the controls below; phones keep their own list either way.
Styling, in the schema file: `ddTypography`, `ddBackground`, `ddBorder`, `ddPadding`, `ddChevron`, `ddPanelBg`, `ddPanelBorder`, `ddPanelShadow`, `ddPanelPadding`, `ddOptTypography`, `ddOptPadding`, `ddOptHover`, `ddHoverText`, `ddOptOnBg`, `ddOptOnColor`, `ddTick`.

### Radio buttons (`bfbeChoices`)
The whole group shows only when `as` is `radios`.
Styling only, every key in the schema file: `chipTypography`, `chipBackground`, `chipBorder`, `chipPadding`, `chipHover`, `chipOnBackground`, `chipOnColor`, `chipOnBorder`.

## What it guarantees for accessibility (do not undo)
- A real form: a labelled select, or a group of radios under its legend.
- Choosing a sort fetches the sorted reviews and puts them in place; the form stays where it is with the focus on it, the address bar follows, and the change is said once, such as Reviews sorted: Oldest first.
- Without JavaScript it is a GET form with a Sort button, which is hidden once the script runs.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<div id="brxe-{id}" class="brxe-bfbe-review-sort bfbe-rv-sort">
  <form class="bfbe-rv__sort bfbe-rv__sort--select is-js" method="get" action="{product URL}#reviews" data-bfbe-rv-sort data-bfbe-rv-sorted="Reviews sorted: %s">
    <input type="hidden" name="bfbe_stars" value="5"><!-- only while a star filter is on -->
    <label class="bfbe-rv__sort-label" for="{uid}">Sort reviews</label>
    <span class="bfbe-dd bfbe-dd__field" data-bfbe-dd><!-- only with look: "custom" -->
      <select class="bfbe-rv__sort-select" id="{uid}" name="bfbe_reviews">
        <option value="">Default order</option><option value="newest">Newest first</option>…<option value="photos">With photos</option>
      </select>
    </span>
    <button type="submit" class="bfbe-rv__sort-go bfbe-chip">Sort</button>
  </form>
</div>
```

- Root `div.bfbe-rv-sort`, holding a real GET form named `bfbe_reviews`. The choices are fixed: Default order (value empty), Newest first, Oldest first, Highest rated, Lowest rated, Most helpful, With photos.
- **Show as** `as: "radios"` swaps the label and select for `fieldset.bfbe-rv__sort-set` (`display: contents`) with a `legend.bfbe-rv__sort-label` and one `label.bfbe-rv__sort-opt.bfbe-chip` per choice, each holding its radio, unseen over the chip, and a `span`. The chosen chip matches `:has(input:checked)`.
- The script adds `is-js`, which hides the **Sort** button, and sets `aria-busy="true"` (opacity .6) while it fetches the sorted page.
- **Open list** `look: "custom"` wraps the select in the shop's styled list (`.bfbe-dd`, its panel `.bfbe-dd__panel` and options `.bfbe-dd__opt`); phones keep the browser's list.
- Where controls write: `labelTypography` to `.bfbe-rv__sort-label`; `gap` to `.bfbe-rv__sort` (between the label and the field, and between chips; 8 px when empty); `ddTypography`, `ddBackground`, `ddBorder` and `ddPadding` to `.bfbe-rv__sort-select`; `ddPanel*` to `.bfbe-dd__panel`; `ddOpt*` to `.bfbe-dd__opt`; `chip*` to `.bfbe-rv__sort-opt`, the chosen ones to `.bfbe-rv__sort-opt:has(input:checked)`.
- No file of its own: the Reviews feature's stylesheet and script (`shop-reviews`) and the shop's shared script.

## Wiring to other elements

- **What it sorts.** Every list of this product's reviews on the page: Bricks' Product reviews (its `#comments`), the Reviews tab of Product tabs, and each BFB Shop reviews loop whose **Reviews of** (`bfbeShopReviewsProduct`) is This product (skill `bfbe-shop-reviews`). The lists may sit anywhere; the sort needs no setting to find them.
- **In place.** With the script, a choice fetches the page with `?bfbe_reviews=…`, replaces Bricks' list and each loop's rows (found by `data-bfbe-rv-row`), moves the address bar and says "Reviews sorted: Oldest first" once. The focus stays on the sort.
- **Default order** is each list's own: **Default order** (`bfbeShopReviewsDefault`) on Product reviews, **Order** (`bfbeShopReviewsOrder`) on a reviews loop. A chosen sort replaces either.
- **BFB Rating Summary.** A star filter in the address (`bfbe_stars`) rides the form as a hidden field, so a sorted list stays filtered.
- **A second sort on the page** follows the first's choice after each sort.
- Give it a class in `_cssClasses` for your own CSS. Nothing targets it by attribute.

## Verified patterns

**Above the list, beside the rating summary.** From the demo shop's product template (Fernhouse product page, section "Reviews", the summary and sort column). A dropdown with the shop's styled open list, under the rating summary in the column beside the list. Trimmed: the brand's colour variables (hex kept) and the open list's colours.

```json
{
  "name": "block",
  "settings": { "_rowGap": "20px", "_cssClasses": "reviews-aside" },
  "children": [
    { "name": "bfbe-rating-summary", "settings": { "stars": true, "figure": "count" } },
    { "name": "bfbe-review-sort", "settings": { "as": "select", "look": "custom", "label": "Sort reviews", "ddBackground": { "hex": "#ffffff" }, "ddBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "12", "right": "12", "bottom": "12", "left": "12" } }, "ddPadding": { "top": "9", "right": "36", "bottom": "9", "left": "12" }, "ddPanelBg": { "hex": "#ffffff" }, "ddOptOnBg": { "hex": "#f0ecff" }, "_cssClasses": "reviews-sort" } }
  ]
}
```

**Away from the list, in the product summary.** From the fixture template `bfbe-shop-product-p4-reviews` ("Review sort, away from the list"): the sort sits in the summary column under the price and buy box, the list far below, and still sorts it in place. Shown here with radio chips (`as: "radios"`, from the schema) and a label of its own.

```json
{
  "name": "block",
  "settings": { "_rowGap": "12px", "_cssClasses": "product-summary" },
  "children": [
    { "name": "product-title", "settings": {} },
    { "name": "product-rating", "settings": {} },
    { "name": "product-price", "settings": {} },
    { "name": "bfbe-review-sort", "settings": { "as": "radios", "label": "Read the reviews", "chipOnBackground": { "hex": "#101828" }, "chipOnColor": { "hex": "#ffffff" }, "_cssClasses": "reviews-sort" } }
  ]
}
```

## Gotchas

- **No list, no sort.** With no Bricks review list and no reviews loop of this product on the page, the fetched page has nothing to swap: the address bar does not move and nothing is said. <!-- src: src/elements/shop-reviews/shop-reviews.js:57-69 ; src/elements/shop-reviews/shop-reviews.js:90 -->
- **One Bricks list per page.** The script replaces the first `#comments` it finds, so Product tabs' Reviews tab above a Product reviews element is the one sorted; leave that tab out. <!-- src: src/elements/shop-reviews/shop-reviews.js:58-59 -->
- **A loop of all or chosen products keeps its order.** Only a reviews loop of **This product** follows the sort. <!-- src: plugins/bfb-elements-pro/includes/shop/class-reviews.php:1067-1081 -->
- **It needs the Reviews feature and a product.** Without the feature, or off a product, the page gets nothing; the canvas says which. <!-- src: plugins/bfb-elements-pro/elements/review-sort.php:179-190 -->
- **Idle in the builder.** The script does not run on the canvas, so choosing there sorts nothing; check the order on the page. <!-- src: src/elements/shop-reviews/shop-reviews.js:81 -->
- **Without a script it is a GET to the product.** The form's address is the product's own with `#reviews`, and the **Sort** button shows; a page cache keeps each order apart. <!-- src: plugins/bfb-elements-pro/includes/shop/class-reviews.php:1725 ; plugins/bfb-elements-pro/includes/shop/class-reviews.php:1747 -->
- **Most helpful and the ratings keep every review.** Reviews with no vote or no rating sort last; **With photos** shows only reviews with photos. <!-- src: plugins/bfb-elements-pro/includes/shop/class-reviews.php:961-966 ; plugins/bfb-elements-pro/includes/shop/class-reviews.php:1018-1041 -->
- **A sort starts a reviews loop over.** The loop's rows become the sorted list's first page, and Bricks' Load more and infinite scroll then count that list's pages (since Pro 2.1.1; before, a sort after Load more skipped a page). A loop that **With photos** leaves empty keeps its place, so the next choice fills it again. A Bricks Pagination element beside the loop keeps the links it was drawn with. <!-- src: src/elements/shop-reviews/shop-reviews.js:57-98 ; docs/elements/review-sort.md "What it does not do" -->
- **Each look has its own group.** The **Dropdown** group shows only while `as` is not `radios`, the **Radio buttons** group only with it; `ddChevron`, `ddPanel*`, `ddOpt*`, `ddHoverText` and `ddTick` need `look: "custom"`. <!-- src: plugins/bfb-elements-pro/elements/review-sort.php:46-47 ; plugins/bfb-elements-pro/elements/review-sort.php:106-109 -->

## Never do

- Do not place a sort on a page without Product reviews, Product tabs' Reviews tab or a reviews loop of this product.
- Do not keep Product tabs' Reviews tab above a Product reviews element the sort should reach.
- Do not expect it to reorder a reviews loop whose `bfbeShopReviewsProduct` is `all` or `chosen`.
- Do not set `chip*` keys with `as` unset or `select`, nor `dd*` keys with `as: "radios"`.
- Do not set `ddPanel*`, `ddOpt*`, `ddChevron` or `ddTick` without `look: "custom"`.
- Do not put it on a page that is not a product.
