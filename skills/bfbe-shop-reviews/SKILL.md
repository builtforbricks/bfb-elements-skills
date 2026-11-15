---
name: bfbe-shop-reviews
description: "Use when building a product page's reviews with Bricks' Product reviews or Product tabs: review photos, helpful votes, the list and form look, hiding Bricks' form for a BFB Review Form, extra tabs from templates, and review lists of your own with the BFB Shop reviews query loop (`shop-reviews`)."
---

# BFB Shop reviews (`shop-reviews`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 2.0.0 or later, and BFB Elements Pro 2.0.0 or later for the groups marked Pro, WooCommerce active, the feature switches on (WordPress menu BFB Elements, Elements): `shop-reviews-loop`, `shop-reviews`, `shop-tabs`. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/shop-reviews.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/shop-reviews/

## What it is
A Pro feature on WooCommerce's own reviews, not an element: photos on the review form, a Helpful yes or no under each review, and a default order, on Bricks' Product reviews (and inside Bricks' Product tabs) and on a review list built with the BFB Shop reviews loop. Everything rides WordPress' and WooCommerce's own comment form, moderation and comment query, so a review is still a WooCommerce review in the admin, the emails and the REST API. Shoppers pick the sort with BFB Review Sort; the form and votes can also stand alone as BFB Review Form and BFB Review Votes.

**Not for:** It does not send review reminder emails, import reviews or show reviews from another service. It does not moderate photos for you: a photo is approved with its review, so read both.

**Nestable:** no · **In a query loop:** yes · **Dynamic data:** no · **Keyboard:** yes · **Reduced motion:** no

## Where it lives
A feature, not an element: its groups are added to Bricks' own elements, on the Content tab after Bricks' own groups. By element:
- Product reviews (`product-reviews`): BFB Reviews (`bfbeShopReviews`), BFB Review list (`bfbeShopReviewList`), BFB Review form (`bfbeShopReviewForm`).
- Product tabs (`product-tabs`): BFB Review list (`bfbeShopReviewList`), BFB Review form (`bfbeShopReviewForm`), BFB Tabs (`bfbeShopTabs`).

## Settings that decide the build

### Product reviews (`product-reviews`)

#### BFB Reviews (`bfbeShopReviews`)
Free, with Pro keys, switch `shop-reviews-loop`, `shop-reviews`. Pro adds `bfbeShopReviewsSepOrder`, `bfbeShopReviewsDefault`, `bfbeShopReviewsSepPhotos`, `bfbeShopReviewsPhotos`, `bfbeShopReviewsPhotoSize`, `bfbeShopReviewsPhotoWidth`, `bfbeShopReviewsPhotoBorder`, `bfbeShopReviewsPhotoGap`, `bfbeShopReviewsSepVotes`, `bfbeShopReviewsVotes`, `bfbeShopReviewsVoteTypography`, `bfbeShopReviewsVoteBtnBackground`, `bfbeShopReviewsVoteBtnBorder`, `bfbeShopReviewsVoteBtnPadding`, `bfbeShopReviewsVoteBtnHover`, `bfbeShopReviewsVoteBtnHoverText`, `bfbeShopReviewsVoteBtnOn`, `bfbeShopReviewsVoteBtnOnText`.
- `bfbeShopReviewsDefault` (select) **Default order**: options: `newest` Newest first, `oldest` Oldest first, `highest` Highest rated, `lowest` Lowest rated, `helpful` Most helpful, `photos` With photos
- `bfbeShopReviewsPhotos` (select) **Show**: options: `show` Shown (default), `hide` Hidden
- `bfbeShopReviewsPhotoSize` (select) **Size**: options: `woocommerce_gallery_thumbnail` Gallery thumbnail (default), `thumbnail` Thumbnail, `medium` Medium; only when `bfbeShopReviewsPhotos` is not `hide`
- `bfbeShopReviewsVotes` (select) **Show**: options: `show` Shown (default), `hide` Hidden
Styling, in the schema file: `bfbeShopReviewsPhotoWidth`, `bfbeShopReviewsPhotoBorder`, `bfbeShopReviewsPhotoGap`, `bfbeShopReviewsVoteTypography`, `bfbeShopReviewsVoteBtnBackground`, `bfbeShopReviewsVoteBtnBorder`, `bfbeShopReviewsVoteBtnPadding`, `bfbeShopReviewsVoteBtnHover`, `bfbeShopReviewsVoteBtnHoverText`, `bfbeShopReviewsVoteBtnOn`, `bfbeShopReviewsVoteBtnOnText`.

#### BFB Review list (`bfbeShopReviewList`)
Pro, switch `shop-reviews`.
- `bfbeShopReviewsFormShow` (select) **Review form**: options: `show` Shown (default), `hide` Hidden. Hidden: place a BFB Review Form elsewhere.
- `bfbeShopReviewsListTitle` (select) **List title**: options: `show` Shown (default), `hide` Hidden; writes CSS. Shown by default or Hidden. Then **Gap**, and each review's **Review background**, **Review border**, **Review padding** and **Text border**.
Styling, in the schema file: `bfbeShopReviewsListGap`, `bfbeShopReviewsItemBackground`, `bfbeShopReviewsItemBorder`, `bfbeShopReviewsItemPadding`, `bfbeShopReviewsTextBorder`.

#### BFB Review form (`bfbeShopReviewForm`)
Pro, switch `shop-reviews`.
- `bfbeShopReviewsUploadLook` (select) **Look**: options: `native` As the browser draws it (default), `custom` A drop area with previews
- `bfbeShopReviewsDropTitle` (text) **Words**: placeholder Drag your photos here; only when `bfbeShopReviewsUploadLook` is `custom`
- `bfbeShopReviewsDropButtonWords` (text) **Button words**: placeholder Choose photos; only when `bfbeShopReviewsUploadLook` is `custom`
Styling, in the schema file: `bfbeShopReviewsFormSpace`, `bfbeShopReviewsFormAreaBackground`, `bfbeShopReviewsFormAreaBorder`, `bfbeShopReviewsFormAreaPadding`, `bfbeShopReviewsFormBackground`, `bfbeShopReviewsFormBorder`, `bfbeShopReviewsFormPadding`, `bfbeShopReviewsFormTitleGap`, `bfbeShopReviewsFormColumns`, `bfbeShopReviewsFormRowGap`, `bfbeShopReviewsFormColumnGap`, `bfbeShopReviewsFormNotes`, `bfbeShopReviewsFormLabelGap`, `bfbeShopReviewsFormRequired`, `bfbeShopReviewsFormConsentGap`, `bfbeShopReviewsFormConsent`, `bfbeShopReviewsFormTextHeight`, `bfbeShopReviewsFormTextPadding`, `bfbeShopReviewsFormTextBorder`, `bfbeShopReviewsFormTextTypography`, `bfbeShopReviewsFormStarSize`, `bfbeShopReviewsFormStarGap`, `bfbeShopReviewsFormStarColor`, `bfbeShopReviewsFormStarOn`, `bfbeShopReviewsUploadBackground`, `bfbeShopReviewsUploadBorder`, `bfbeShopReviewsUploadButton`, `bfbeShopReviewsUploadButtonHover`, `bfbeShopReviewsUploadButtonText`, `bfbeShopReviewsUploadHelp`, `bfbeShopReviewsDropBackground`, `bfbeShopReviewsDropBorder`, `bfbeShopReviewsDropPadding`, `bfbeShopReviewsDropGap`, `bfbeShopReviewsDropOver`, `bfbeShopReviewsDropOverLine`, `bfbeShopReviewsDropIconSize`, `bfbeShopReviewsDropIconColor`, `bfbeShopReviewsDropTypography`, `bfbeShopReviewsDropButtonBackground`, `bfbeShopReviewsDropButtonColor`, `bfbeShopReviewsDropButtonHover`, `bfbeShopReviewsDropButtonHoverColor`, `bfbeShopReviewsDropButtonBorder`, `bfbeShopReviewsDropButtonPadding`, `bfbeShopReviewsDropButtonTypography`, `bfbeShopReviewsPickedSize`, `bfbeShopReviewsPickedBorder`, `bfbeShopReviewsPickedRemove`, `bfbeShopReviewsFormButtonPadding`, `bfbeShopReviewsFormButtonTypography`.

### Product tabs (`product-tabs`)

#### BFB Review list (`bfbeShopReviewList`)
The same 7 controls as on `product-reviews`.

#### BFB Review form (`bfbeShopReviewForm`)
Pro, switch `shop-reviews`.
- `bfbeShopReviewsFormTextResize` (select) **Resize**: options: `none` None, `vertical` Vertical, `horizontal` Horizontal, `both` Both (default); writes CSS
- `bfbeShopReviewsUploadLook` (select) **Look**: options: `native` As the browser draws it (default), `custom` A drop area with previews
- `bfbeShopReviewsDropTitle` (text) **Words**: placeholder Drag your photos here; only when `bfbeShopReviewsUploadLook` is `custom`
- `bfbeShopReviewsDropButtonWords` (text) **Button words**: placeholder Choose photos; only when `bfbeShopReviewsUploadLook` is `custom`
Styling, in the schema file: `bfbeShopReviewsFormSpace`, `bfbeShopReviewsFormAreaBackground`, `bfbeShopReviewsFormAreaBorder`, `bfbeShopReviewsFormAreaPadding`, `bfbeShopReviewsFormBackground`, `bfbeShopReviewsFormBorder`, `bfbeShopReviewsFormPadding`, `bfbeShopReviewsFormTitleTypography`, `bfbeShopReviewsFormTitleGap`, `bfbeShopReviewsFormColumns`, `bfbeShopReviewsFormRowGap`, `bfbeShopReviewsFormColumnGap`, `bfbeShopReviewsFormNotes`, `bfbeShopReviewsFormLabel`, `bfbeShopReviewsFormLabelGap`, `bfbeShopReviewsFormRequired`, `bfbeShopReviewsFormConsentGap`, `bfbeShopReviewsFormConsent`, `bfbeShopReviewsFormTextHeight`, `bfbeShopReviewsFormTextPadding`, `bfbeShopReviewsFormTextBorder`, `bfbeShopReviewsFormTextTypography`, `bfbeShopReviewsFormStarSize`, `bfbeShopReviewsFormStarGap`, `bfbeShopReviewsFormStarColor`, `bfbeShopReviewsFormStarOn`, `bfbeShopReviewsUploadBackground`, `bfbeShopReviewsUploadBorder`, `bfbeShopReviewsUploadButton`, `bfbeShopReviewsUploadButtonHover`, `bfbeShopReviewsUploadButtonText`, `bfbeShopReviewsUploadHelp`, `bfbeShopReviewsDropBackground`, `bfbeShopReviewsDropBorder`, `bfbeShopReviewsDropPadding`, `bfbeShopReviewsDropGap`, `bfbeShopReviewsDropOver`, `bfbeShopReviewsDropOverLine`, `bfbeShopReviewsDropIconSize`, `bfbeShopReviewsDropIconColor`, `bfbeShopReviewsDropTypography`, `bfbeShopReviewsDropButtonBackground`, `bfbeShopReviewsDropButtonColor`, `bfbeShopReviewsDropButtonHover`, `bfbeShopReviewsDropButtonHoverColor`, `bfbeShopReviewsDropButtonBorder`, `bfbeShopReviewsDropButtonPadding`, `bfbeShopReviewsDropButtonTypography`, `bfbeShopReviewsPickedSize`, `bfbeShopReviewsPickedBorder`, `bfbeShopReviewsPickedRemove`, `bfbeShopReviewsFormButtonPadding`, `bfbeShopReviewsFormButtonTypography`.

#### BFB Tabs (`bfbeShopTabs`)
Pro, switch `shop-tabs`.
- `bfbeShopTabsLeaveOut` (select) **Leave out WooCommerce's tabs**: options: `description` Description, `additional_information` Additional information, `reviews` Reviews. Reviews: when the page shows its own reviews.
Styling, in the schema file: `bfbeShopTabsGap`, `bfbeShopTabsTabBackground`, `bfbeShopTabsTabBorder`, `bfbeShopTabsLinkPadding`, `bfbeShopTabsActiveBorder`, `bfbeShopTabsHoverBackground`, `bfbeShopTabsHoverColor`, `bfbeShopTabsCellPadding`, `bfbeShopTabsCellBorder`.

## What it guarantees for accessibility (do not undo)
- Helpful? names a group of two real buttons, Yes and No, each with aria-pressed. After a vote the buttons are marked aria-disabled rather than disabled, so the focus stays where it was, and the count updates in place.
- The sort is a real form: a labelled select, or radios under a legend. After a sort the form keeps the focus and the change is said once, such as Reviews sorted: Oldest first.
- A review's photos are a list named Photos from this review, each a link to the full image with alt text naming the reviewer.
- Without JavaScript all of it works: the photos post with the review, the votes are a form posted to the page, and the sort is a form with a Sort button.
<!-- bfbe:generated:end -->

## Rendered DOM

The feature adds no wrapper. It writes into the markup WooCommerce's review template prints inside Bricks' Product reviews, and inside the Reviews tab of Product tabs.

```html
<div class="brxe-product-reviews">
  <div id="reviews" class="woocommerce-Reviews">
    <div id="comments">
      <h2 class="woocommerce-Reviews-title">…</h2>
      <ol class="commentlist">
        <li class="review …">… <div class="description">…</div>
          <ul class="bfbe-rv__photos" aria-label="Photos from this review"><li><a class="bfbe-rv__photo" href="{full image}" target="_blank"><img …></a></li></ul>
          <form class="bfbe-rv__vote" method="post" data-bfbe-review="{comment id}">…</form>
        </li>
      </ol>
    </div>
    <div id="review_form_wrapper"><div id="review_form">
      <form id="commentform" class="comment-form" enctype="multipart/form-data">… <p class="comment-form-bfbe-photos bfbe-rv__upload">…</p> …</form>
    </div></div>
  </div>
</div>
```

- Photos, then the Helpful form, follow each review's text (WooCommerce's `woocommerce_review_after_comment_text`); the vote form shows on approved reviews only. Its markup is BFB Review Votes' (skill `bfbe-review-votes`).
- With **Review form** `bfbeShopReviewsFormShow: "hide"` the form is never printed: `#review_form_wrapper` and `#review_form` stay empty, `hidden` and without their ids, and WooCommerce's verified-owners line is `hidden` too.
- The photo field follows the review box: the browser's file input in `p.bfbe-rv__upload`, or with **Look** `bfbeShopReviewsUploadLook: "custom"` a `div.bfbe-rv__upload--drop` whose `.bfbe-rv__drop` holds the same input, unseen, over the area, and a `ul.bfbe-rv__picked` of previews.
- Where the controls write: `bfbeShopReviewsPhoto*` to `.bfbe-rv__photos` and `.bfbe-rv__photo img` (72 px squares when empty); `bfbeShopReviewsVote*` to `.bfbe-rv__vote` and `.bfbe-rv__btn`; `bfbeShopReviewsItem*` to `.commentlist > li`; `bfbeShopReviewsTextBorder` to `.commentlist .description`; `bfbeShopReviewsListTitle: "hide"` hides `.woocommerce-Reviews-title`.
- The form keys write to `#review_form_wrapper` (area), `.comment-respond` (card), `.comment-reply-title`, `.comment-form` (the **Columns** grid), `.comment-form-comment textarea`, `.comment-form-rating .stars a` and the `.form-submit` button.
- Product tabs: `bfbeShopTabs*` write to `.wc-tabs` and `.wc-tabs li`, the cell keys to `.shop_attributes th` and `td`. Extra tabs are WooCommerce tabs, drawn by Bricks as its own.
- A reviews loop (`query.objectType: "bfbeShopReviews"`) prints Bricks' own row markup; with this feature on, each row carries `data-bfbe-rv-row="{looping element id}"`, which the sort's script uses to put sorted rows in place.

## Wiring to other elements

- **Every part is an element, placed with Bricks' containers.** BFB Rating Summary, BFB Review Sort, BFB Review Form and BFB Review Votes each have a skill. Nothing in this feature has a position or arrangement control.
- **One form per page.** Set `bfbeShopReviewsFormShow: "hide"` on Product reviews (or Product tabs) and place a `bfbe-review-form` where the form belongs. Style it there: it carries the same `bfbeShopReviewsForm*` and upload keys.
- **The sort.** A `bfbe-review-sort` anywhere on the product page sorts Product reviews, the Reviews tab of Product tabs and every reviews loop whose **Reviews of** (`bfbeShopReviewsProduct`) is This product. **Default order** (`bfbeShopReviewsDefault`) on Product reviews is the order before a shopper chooses.
- **The stars filter.** BFB Rating Summary's bars link to `?bfbe_stars=N#reviews`, which the same lists read. `#reviews` is WooCommerce's block inside Product reviews, so the default anchor needs no id of yours.
- **A list of your own.** A Container, Block or Div with `hasLoop: true` and `query.objectType: "bfbeShopReviews"` repeats a row per approved review (skill `bfbe-shop-loops`). The row's current post is the reviewed product. Fill it with the review tags (`{bfbe_review_stars:svg}`, `{bfbe_review_author}`, `{bfbe_review_date}`, `{bfbe_review_text}`, `{bfbe_review_photos}`; skill `bfbe-shop-tags-and-conditions`) and a `bfbe-review-votes`.
- **One review, one vote.** A review shown in Bricks' list and in a loop on the same page shows a vote on both at once.
- **Product tabs beside Product reviews.** When the reviews have a section of their own, set **Leave out WooCommerce's tabs** `bfbeShopTabsLeaveOut: ["reviews"]` on Product tabs, so the page carries one list and one form.
- **Extra tabs** come from the Shop page (BFB Elements, Shop, Products, card **Product tabs**: Title, Bricks template, Shown on, Position) and from a product's own **BFB Extra tab** panel. Product tabs shows them with no setting; each template renders for the product shown.
- The sort's script finds Bricks' list by WooCommerce's `#comments` and a loop's rows by `data-bfbe-rv-row`, never by your classes. Give elements a class in `_cssClasses` for your own CSS; avoid `_cssId`, which component instances share.

## Verified patterns

**The demo's review area: the summary and the sort in one column, the list and the form in the other.** From the demo shop's product template (Fernhouse product page, section "Reviews"). A Bricks grid of 380 px and the rest, one column from `tablet_portrait`. Product reviews hides its form and title and spaces its reviews by `bfbeShopReviewsListGap` alone; BFB Review Form stands under the list, **Columns** 1, its review box opening 120 px tall. Trimmed: the brand's colour variables (hex kept), the open list's look, most of the form's look and the section's `_cssId`. Use on a product template.

```json
{
  "name": "block",
  "settings": { "_display": "grid", "_gridTemplateColumns": "380px minmax(0, 1fr)", "_gridTemplateColumns:tablet_portrait": "minmax(0, 1fr)", "_gridGap": "32px 48px", "_alignItems": "start", "_cssClasses": "reviews-area" },
  "children": [
    { "name": "block", "settings": { "_rowGap": "20px" }, "children": [
      { "name": "heading", "settings": { "text": "What people say", "tag": "h2" } },
      { "name": "bfbe-rating-summary", "settings": { "stars": true, "text": "{average} out of 5, from {count} reviews", "figure": "count", "barHeight": "8", "barColor": { "hex": "#f5a524" }, "trackColor": { "hex": "#e9ecf1" }, "rowGap": "8" } },
      { "name": "bfbe-review-sort", "settings": { "as": "select", "look": "custom", "label": "Sort reviews" } }
    ] },
    { "name": "block", "settings": { "_rowGap": "20px" }, "children": [
      { "name": "product-reviews", "settings": { "bfbeShopReviewsFormShow": "hide", "bfbeShopReviewsListTitle": "hide", "bfbeShopReviewsListGap": "12px", "bfbeShopReviewsItemBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "16", "right": "16", "bottom": "16", "left": "16" } }, "bfbeShopReviewsItemPadding": { "top": "20", "right": "20", "bottom": "20", "left": "20" }, "_cssClasses": "reviews-list" } },
      { "name": "bfbe-review-form", "settings": { "bfbeShopReviewsFormColumns": 1, "bfbeShopReviewsFormRowGap": "20px", "bfbeShopReviewsFormTextHeight": "120px", "bfbeShopReviewsFormStarSize": "32px", "bfbeShopReviewsUploadLook": "custom", "_cssClasses": "reviews-form" } }
    ] }
  ]
}
```

**The same reviews as rows of your own.** From the fixture template `bfbe-shop-product-p4-reviews` ("Reviews loop"), the row's words rewritten. A Block repeats per review of this product, 50 to a page because a product page cannot page through them; each row prints the review's tags, its photos through Bricks' Image Gallery and its votes. A Review Sort or a Rating Summary bar on the page reorders or filters these rows as it does Bricks' list.

```json
{
  "name": "block",
  "settings": { "_rowGap": "12px", "_cssClasses": "review-rows" },
  "children": [
    { "name": "block", "settings": { "hasLoop": true, "query": { "objectType": "bfbeShopReviews" }, "bfbeShopReviewsCount": 50, "_cssClasses": "review-row" }, "children": [
      { "name": "text-basic", "settings": { "text": "{bfbe_review_stars:svg} {bfbe_review_author}, {bfbe_review_date}" } },
      { "name": "text-basic", "settings": { "text": "{bfbe_review_text}" } },
      { "name": "image-gallery", "settings": { "items": { "useDynamicData": "{bfbe_review_photos}" }, "columns": 4 } },
      { "name": "bfbe-review-votes", "settings": { "_cssClasses": "review-row-votes" } }
    ] }
  ]
}
```

**Product tabs without the Reviews tab, drawn as pills.** From the demo shop's product template ("Tabs"). The page's reviews sit in Product reviews below, so `bfbeShopTabsLeaveOut` drops WooCommerce's Reviews tab; BFB Tabs gives every tab a fill, round corners, padding inside the link and a hover fill. Trimmed: Bricks' own tab and panel settings.

```json
{ "name": "product-tabs", "settings": { "bfbeShopTabsLeaveOut": ["reviews"], "bfbeShopTabsGap": "8px", "bfbeShopTabsTabBackground": { "hex": "#f6f6f8" }, "bfbeShopTabsTabBorder": { "radius": { "top": "999", "right": "999", "bottom": "999", "left": "999" } }, "bfbeShopTabsLinkPadding": { "top": "11", "right": "20", "bottom": "11", "left": "20" }, "bfbeShopTabsHoverBackground": { "hex": "#f0ecff" }, "_cssClasses": "product-tabs" } }
```

## Gotchas

- **The switch decides everything.** With **Reviews** (`shop-reviews`) off on the Elements page, Product reviews and Product tabs lose the BFB groups, and BFB Review Form, Sort and Votes print nothing (the canvas says why). The Rating Summary's star filter keeps working. <!-- src: plugins/bfb-elements-pro/includes/shop/class-reviews.php:98-103 ; plugins/bfb-elements-pro/elements/review-form.php:101 ; plugins/bfb-elements-pro/includes/shop/class-rating-summary.php:26-30 -->
- **Product tabs has no BFB Reviews group.** Its Reviews tab shows photos at Gallery thumbnail and the votes, in WooCommerce's order: `bfbeShopReviewsDefault`, `bfbeShopReviewsPhotos` and `bfbeShopReviewsVotes` act on Product reviews only. <!-- src: plugins/bfb-elements-pro/includes/shop/class-reviews.php:103 ; plugins/bfb-elements-pro/includes/shop/class-reviews.php:891-895 ; docs/elements/shop-reviews.md "BFB Review list" -->
- **A hidden form takes its look with it.** With `bfbeShopReviewsFormShow: "hide"`, the element's own BFB Review form keys style nothing; the form's look belongs on the BFB Review Form. <!-- src: plugins/bfb-elements-pro/includes/shop/class-reviews.php:870-886 ; plugins/bfb-elements-pro/includes/shop/class-reviews.php:1668-1686 -->
- **Two forms on a page break the stars.** Each carries WooCommerce's `#commentform` and `#rating`, and its script draws the stars for the first only. <!-- src: docs/elements/review-form.md "Placing it" -->
- **List Gap is the only space.** `bfbeShopReviewsListGap` makes `.commentlist` a grid and zeroes each review's bottom margin, so nothing follows the last review. Unset, Bricks' 30 px stays under every review. <!-- src: plugins/bfb-elements-pro/includes/shop/class-reviews.php:347-357 ; docs/SHOP-LABELS-2.0.0.md "Fixed with no setting changed (30 October)" -->
- **Review box Height is where it opens.** `bfbeShopReviewsFormTextHeight` writes height and min-height, so the box opens that tall and a shopper's drag cannot shrink it below. <!-- src: plugins/bfb-elements-pro/includes/shop/class-reviews.php:540-551 ; docs/SHOP-LABELS-2.0.0.md "BFB Review Form and the Reviews form: the text box height" -->
- **The Shop page's switches come first.** **Photos on the review form** off removes the upload field, the multipart form and the photos under reviews; **Helpful votes** off removes every vote form. The Show keys only hide what the switches allow. <!-- src: plugins/bfb-elements-pro/includes/shop/class-reviews.php:1135-1146 ; plugins/bfb-elements-pro/includes/shop/class-reviews.php:1289-1292 ; plugins/bfb-elements-pro/includes/shop/class-reviews.php:1693-1696 -->
- **The upload's two looks have separate keys.** `bfbeShopReviewsUpload*` colours style the browser's file box, `bfbeShopReviewsDrop*` and `bfbeShopReviewsPicked*` the drop area; the panel offers only the set of the chosen **Look**. <!-- src: plugins/bfb-elements-pro/includes/shop/class-reviews.php:398-403 -->
- **Sorts and the filter are addresses.** `?bfbe_reviews=highest` and `?bfbe_stars=5` are read by each list's own comment query, so a page cache keeps them apart. Highest, Lowest and Most helpful put reviews with no rating or vote last. <!-- src: plugins/bfb-elements-pro/includes/shop/class-reviews.php:899-915 ; plugins/bfb-elements-pro/includes/shop/class-reviews.php:1018-1041 -->
- **Only a loop of this product follows them.** A reviews loop with `bfbeShopReviewsProduct` set to `all` or `chosen` keeps its own **Order** and ignores the stars filter. <!-- src: plugins/bfb-elements-pro/includes/shop/class-reviews.php:1067-1069 -->
- **A reviews loop does not page on a product page.** WordPress sends page two of a single post back to the post, so Bricks' Pagination does nothing there; raise **Reviews per page** (`bfbeShopReviewsCount`). Live filters never reach a reviews loop. <!-- src: docs/elements/shop-reviews-loop.md "Limits" -->
- **Load more and infinite scroll do work there, and follow the address.** A Bricks button with the Load more interaction on the loop, or the loop's own infinite scroll, brings the next reviews of the chosen stars and order (since Pro 2.1.1; before, page two came unfiltered in the default order). <!-- src: plugins/bfb-elements-pro/includes/shop/class-reviews.php:941-958 ; docs/elements/shop-reviews-loop.md "With the Pro Reviews feature" -->
- **The sort reaches one Bricks list.** Its script replaces the first `#comments` on the page, so a Reviews tab left in Product tabs above Product reviews is the one sorted. <!-- src: src/elements/shop-reviews/shop-reviews.js:57-59 -->
- **Removed keys do nothing.** `bfbeShopReviewsSort`, `bfbeShopReviewsSortAs`, `bfbeShopReviewsSortLabel`, `bfbeShopReviewsFormPlace` and `bfbeShopReviewsFormOrder` went on 29 October; a saved value is ignored. <!-- src: docs/SHOP-LABELS-2.0.0.md "layout round", Product reviews and Product tabs tables -->

## Never do

- Do not leave Bricks' form shown when a BFB Review Form is on the page; set `bfbeShopReviewsFormShow: "hide"`.
- Do not style the form on Product reviews' BFB Review form group once its form is hidden; style the BFB Review Form.
- Do not keep WooCommerce's Reviews tab in Product tabs beside a Product reviews element; set `bfbeShopTabsLeaveOut: ["reviews"]`.
- Do not write `bfbeShopReviewsSort`, `bfbeShopReviewsFormPlace` or `bfbeShopReviewsFormOrder`; place a BFB Review Sort and a BFB Review Form.
- Do not rely on Bricks' Pagination for a reviews loop on a product template; set `bfbeShopReviewsCount`.
- Do not expect the sort or the stars filter to reach a loop whose `bfbeShopReviewsProduct` is `all` or `chosen`.
- Do not set `bfbeShopReviewsDefault` or the Show keys for Product tabs; they belong to Product reviews.
