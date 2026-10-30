---
name: bfbe-review-votes
description: "Use when adding Helpful yes or no votes to a review list built with the BFB Shop reviews query loop, with `bfbe-review-votes` placed in the loop's row."
---

# BFB Review Votes (`bfbe-review-votes`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-review-votes.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/review-votes/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Buttons (`bfbeVotes`)
Styling only, every key in the schema file: `typography`, `countTypography`, `gap`, `buttonTypography`, `buttonBackground`, `buttonBorder`, `buttonPadding`, `hoverBackground`, `hoverColor`, `onBackground`, `onColor`.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<div class="brxe-{id} brxe-bfbe-review-votes bfbe-rv-votes"><!-- in a loop row: no id, the element id as a class -->
  <form class="bfbe-rv__vote" method="post" data-bfbe-review="{comment id}" data-bfbe-rv-one="…" data-bfbe-rv-many="…" data-bfbe-rv-thanks="…">
    <input type="hidden" name="bfbe_shop_act" value="review_vote"><input type="hidden" name="comment" value="{comment id}">
    <span class="bfbe-rv__count" data-bfbe-rv-count>3 people found this helpful</span>
    <span class="bfbe-rv__ask" id="bfbe-rv-ask-{comment id}">Helpful?</span>
    <span class="bfbe-rv__btns" role="group" aria-labelledby="bfbe-rv-ask-{comment id}">
      <button type="submit" class="bfbe-rv__btn bfbe-chip" name="bfbe_vote" value="yes" aria-pressed="false">Yes</button>
      <button type="submit" class="bfbe-rv__btn bfbe-chip" name="bfbe_vote" value="no" aria-pressed="false">No</button>
    </span>
  </form>
</div>
```

- Root `div.bfbe-rv-votes` around the Reviews feature's own vote form, the same markup Bricks' Product reviews prints under each review. A signed-in visitor's form also carries a `_bfbe_nonce` field.
- The count comes first and is empty (hidden by `:empty`) until someone says yes. The question's id gains a number when the same review's form is printed twice on a page.
- After a vote both buttons get `aria-disabled="true"`, never `disabled`, so the focus stays; the chosen one gets `aria-pressed="true"`. The vote is kept in the visitor's browser (`bfbe_shop_review_votes`, kind needed), so a reload or a cached page shows it pressed.
- Where controls write: `typography` to `.bfbe-rv__vote`; `countTypography` to `.bfbe-rv__count`; `gap` to `.bfbe-rv__vote` and `.bfbe-rv__btns` (8 px when empty); `buttonTypography`, `buttonBorder` and `buttonPadding` to `.bfbe-rv__btn`, `buttonBackground` to the unpressed ones; `hover*` to `.bfbe-rv__btn:not([aria-disabled="true"]):hover`; `onBackground` and `onColor` to `[aria-pressed="true"]`.
- No file of its own: the Reviews feature's stylesheet and script (`shop-reviews`) and the shop's shared script.

## Wiring to other elements

- **It lives in a row of a BFB Shop reviews loop.** Place it inside the Container, Block or Div that carries `hasLoop: true` and `query.objectType: "bfbeShopReviews"`, at any depth in the row (skill `bfbe-shop-loops`). It reads the row's review from the loop, not from a parent element: there is no parent to nest it in.
- **Any reviews loop.** **Reviews of** This product, All products or Chosen products all work; each row votes on its own review.
- **One vote with Bricks' list.** When the same review shows in Product reviews and in a loop, a vote on either presses both at once and counts once (skill `bfbe-shop-reviews`).
- **The rest of the row** is Bricks' own elements with the review tags: `{bfbe_review_stars:svg}`, `{bfbe_review_author}`, `{bfbe_review_date}`, `{bfbe_review_text}`, and `{bfbe_review_photos}` in a Basic Text or as the images of Bricks' Image Gallery (skill `bfbe-shop-tags-and-conditions`).
- **BFB Review Sort** re-renders the loop's rows in place; the new rows bind their votes at once.
- Give it a class in `_cssClasses` for your own CSS. Nothing targets it by attribute.

## Verified patterns

**Helpful votes in a review row of your own.** From the fixture template `bfbe-shop-product-p4-reviews` ("Reviews loop"), the row's words rewritten. The Block loops over this product's reviews; the votes sit last in each row, under the photos in Bricks' Image Gallery. Use on a product template; with `bfbeShopReviewsProduct: "all"` the same row works on any page.

```json
{
  "name": "block",
  "settings": { "_rowGap": "12px", "_cssClasses": "review-rows" },
  "children": [
    { "name": "block", "settings": { "hasLoop": true, "query": { "objectType": "bfbeShopReviews" }, "bfbeShopReviewsCount": 50, "_cssClasses": "review-row" }, "children": [
      { "name": "text-basic", "settings": { "text": "{bfbe_review_author}, {bfbe_review_date}" } },
      { "name": "text-basic", "settings": { "text": "{bfbe_review_text}" } },
      { "name": "image-gallery", "settings": { "items": { "useDynamicData": "{bfbe_review_photos}" }, "columns": 4 } },
      { "name": "bfbe-review-votes", "settings": { "_cssClasses": "review-votes" } }
    ] }
  ]
}
```

**The votes beside the author, styled as pills.** Built from the schema. A row of the shop's latest praise from every product (`bfbeShopReviewsProduct: "all"`, `bfbeShopReviewsMinRating` 4), the stars and author on the left and the votes on the right of a Bricks row; the pressed button turns dark.

```json
{
  "name": "block",
  "settings": { "hasLoop": true, "query": { "objectType": "bfbeShopReviews" }, "bfbeShopReviewsProduct": "all", "bfbeShopReviewsMinRating": 4, "bfbeShopReviewsCount": 6, "_rowGap": "8px", "_cssClasses": "praise-row" },
  "children": [
    { "name": "block", "settings": { "_direction": "row", "_justifyContent": "space-between", "_alignItems": "center", "_columnGap": "16px" }, "children": [
      { "name": "text-basic", "settings": { "text": "{bfbe_review_stars:svg} {bfbe_review_author} on {bfbe_review_product}" } },
      { "name": "bfbe-review-votes", "settings": { "gap": "6px", "buttonBorder": { "radius": { "top": "999", "right": "999", "bottom": "999", "left": "999" } }, "onBackground": { "hex": "#101828" }, "onColor": { "hex": "#ffffff" }, "_cssClasses": "praise-votes" } }
    ] },
    { "name": "text-basic", "settings": { "text": "{bfbe_review_text}" } }
  ]
}
```

## Gotchas

- **Outside a reviews loop it prints nothing.** It needs the loop's review; dropped anywhere else, the page gets nothing and the canvas says "Place this inside a BFB Shop reviews loop." <!-- src: plugins/bfb-elements-pro/elements/review-votes.php:92-96 -->
- **Helpful votes off, nothing at all.** With **Helpful votes** off on the Shop page (BFB Elements, Shop, Products, card **Reviews**), every Review Votes is empty and the server refuses a vote. <!-- src: plugins/bfb-elements-pro/elements/review-votes.php:87-91 ; plugins/bfb-elements-pro/includes/shop/class-reviews.php:1244-1246 -->
- **It needs the Reviews feature and the reviews loop.** With **Reviews** (`shop-reviews`) or **Reviews loop** (`shop-reviews-loop`) off, it prints nothing. <!-- src: plugins/bfb-elements-pro/elements/review-votes.php:82-86 -->
- **Approved reviews only.** A review WooCommerce has not approved gets no votes; the loop lists approved reviews only anyway. <!-- src: plugins/bfb-elements-pro/elements/review-votes.php:93 ; plugins/bfb-elements/includes/shop/class-reviews-loop.php:131 -->
- **One vote per visitor per review, decided on the server.** A signed-in customer is their account; a guest is a hash of the address and browser. One address may cast 60 votes an hour and 5 a day on one review, then gets "Too many votes from this address for now." <!-- src: plugins/bfb-elements-pro/includes/shop/class-reviews.php:1213-1220 ; plugins/bfb-elements-pro/includes/shop/class-reviews.php:1255-1258 -->
- **Its look is its own.** Product reviews' `bfbeShopReviewsVote*` keys style the votes in Bricks' list only; a Review Votes takes its own `button*`, `hover*` and `on*` keys. <!-- src: plugins/bfb-elements-pro/elements/review-votes.php:45-64 ; plugins/bfb-elements-pro/includes/shop/class-reviews.php:256-315 -->
- **A voted button keeps its look under the pointer.** `hoverBackground` and `hoverColor` skip `aria-disabled` buttons, so after a vote neither button changes on hover. <!-- src: plugins/bfb-elements-pro/elements/review-votes.php:49 -->
- **Without a script the form posts to the page.** The page reloads with the vote counted and WooCommerce's notice "Thank you for your vote." <!-- src: docs/elements/review-votes.md "What works without JavaScript" -->

## Never do

- Do not place it outside a row of a BFB Shop reviews loop; it prints nothing there.
- Do not place it on a page whose shop has Helpful votes off.
- Do not style its buttons with Product reviews' `bfbeShopReviewsVote*` keys; use its own `button*`, `hover*` and `on*` keys.
- Do not add `disabled` or `tabindex` to its buttons; the script marks a vote with `aria-disabled` and `aria-pressed`.
