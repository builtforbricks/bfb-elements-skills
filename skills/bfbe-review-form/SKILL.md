---
name: bfbe-review-form
description: "Use when placing WooCommerce's review form anywhere on a product page with `bfbe-review-form`: under or beside the review list, in its own column or a popup, with photo upload, stars and the form's look."
---

# BFB Review Form (`bfbe-review-form`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-review-form.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/review-form/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Form (`bfbeRvf`)
- `title` (text) **Title**: placeholder Add a review; dynamic data accepted. Empty: WooCommerce words it.

### Area and card (`bfbeRvfArea`)
Styling only, every key in the schema file: `bfbeShopReviewsFormSpace`, `bfbeShopReviewsFormAreaBackground`, `bfbeShopReviewsFormAreaBorder`, `bfbeShopReviewsFormAreaPadding`, `bfbeShopReviewsFormBackground`, `bfbeShopReviewsFormBorder`, `bfbeShopReviewsFormPadding`.

### Title and fields (`bfbeRvfFields`)
Styling only, every key in the schema file: `bfbeShopReviewsFormTitleTypography`, `bfbeShopReviewsFormTitleGap`, `bfbeShopReviewsFormColumns`, `bfbeShopReviewsFormRowGap`, `bfbeShopReviewsFormColumnGap`, `bfbeShopReviewsFormNotes`, `bfbeShopReviewsFormLabel`, `bfbeShopReviewsFormLabelGap`, `bfbeShopReviewsFormRequired`, `bfbeShopReviewsFormConsentGap`, `bfbeShopReviewsFormConsent`.

### Review box and stars (`bfbeRvfText`)
- `bfbeShopReviewsFormTextResize` (select) **Resize**: options: `none` None, `vertical` Vertical, `horizontal` Horizontal, `both` Both (default); writes CSS
Styling, in the schema file: `bfbeShopReviewsFormTextHeight`, `bfbeShopReviewsFormTextPadding`, `bfbeShopReviewsFormTextBorder`, `bfbeShopReviewsFormTextTypography`, `bfbeShopReviewsFormStarSize`, `bfbeShopReviewsFormStarGap`, `bfbeShopReviewsFormStarColor`, `bfbeShopReviewsFormStarOn`.

### Photo upload (`bfbeRvfUpload`)
- `bfbeShopReviewsUploadLook` (select) **Look**: options: `native` The browser's file box, `custom` A drop area with previews
- `bfbeShopReviewsDropTitle` (text) **Words**: placeholder Drag your photos here; only when `bfbeShopReviewsUploadLook` is `custom`
- `bfbeShopReviewsDropButtonWords` (text) **Button words**: placeholder Choose photos; only when `bfbeShopReviewsUploadLook` is `custom`
Styling, in the schema file: `bfbeShopReviewsUploadBackground`, `bfbeShopReviewsUploadBorder`, `bfbeShopReviewsUploadButton`, `bfbeShopReviewsUploadButtonHover`, `bfbeShopReviewsUploadButtonText`, `bfbeShopReviewsUploadHelp`, `bfbeShopReviewsDropBackground`, `bfbeShopReviewsDropBorder`, `bfbeShopReviewsDropPadding`, `bfbeShopReviewsDropGap`, `bfbeShopReviewsDropOver`, `bfbeShopReviewsDropOverLine`, `bfbeShopReviewsDropIconSize`, `bfbeShopReviewsDropIconColor`, `bfbeShopReviewsDropTypography`, `bfbeShopReviewsDropButtonBackground`, `bfbeShopReviewsDropButtonColor`, `bfbeShopReviewsDropButtonHover`, `bfbeShopReviewsDropButtonHoverColor`, `bfbeShopReviewsDropButtonBorder`, `bfbeShopReviewsDropButtonPadding`, `bfbeShopReviewsDropButtonTypography`, `bfbeShopReviewsPickedSize`, `bfbeShopReviewsPickedBorder`, `bfbeShopReviewsPickedRemove`.

### Button (`bfbeRvfButton`)
Styling only, every key in the schema file: `bfbeShopReviewsFormButtonPadding`, `bfbeShopReviewsFormButtonTypography`.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<div id="brxe-{id}" class="brxe-bfbe-review-form bfbe-rvf">
  <div id="review_form_wrapper"><div id="review_form">
    <div id="respond" class="comment-respond">
      <span id="reply-title" class="comment-reply-title" role="heading" aria-level="3">Add a review</span>
      <form action="…/wp-comments-post.php" method="post" id="commentform" class="comment-form" enctype="multipart/form-data">
        <p class="comment-notes">…</p><p class="comment-form-author">…</p><p class="comment-form-email">…</p><p class="comment-form-cookies-consent">…</p>
        <div class="comment-form-rating"><label for="rating">Your rating</label><select name="rating" id="rating" required>…</select></div>
        <p class="comment-form-comment"><label for="comment">Your review</label><textarea id="comment" name="comment" rows="8" required></textarea></p>
        <p class="comment-form-bfbe-photos bfbe-rv__upload"><label for="bfbe_review_photos">Photos</label><input type="file" id="bfbe_review_photos" name="bfbe_review_photos[]" multiple …><span class="bfbe-rv__upload-help">…</span></p>
        <p class="form-submit"><input type="submit" id="submit" class="submit" value="Submit">…</p>
      </form>
    </div>
  </div></div>
</div>
```

- Root `div.bfbe-rvf`, the column's whole width (`inline-size: 100%`) since 30 October. Inside, WordPress' own `comment_form()` with WooCommerce's arguments, in the wrappers WooCommerce's template gives it, so its script and Bricks' review styles find it.
- For a guest the notes, name, email and consent box come first, then the rating, the review box and the photo field. WooCommerce's script turns `select#rating` into a `p.stars` of five links; the select stays for the post.
- The photo field appears with **Photos on the review form** on (Shop page); then the form is `multipart/form-data`. With **Look** `bfbeShopReviewsUploadLook: "custom"` it is a `div.bfbe-rv__upload--drop`: the same input, unseen, over a `.bfbe-rv__drop` area with an icon, `.bfbe-rv__drop-title`, `.bfbe-rv__drop-button`, then a live `.bfbe-rv__picked-say` and a `ul.bfbe-rv__picked` of previews with remove buttons (`.bfbe-rv__pick-x`).
- A non-buyer on a shop that lets only verified owners review gets WooCommerce's line `p.woocommerce-verification-required` inside the root, and no form.
- Where controls write: **Area and card** to `#review_form_wrapper` (area) and `.comment-respond` (card); **Title typography** and **Space under the title** to `.comment-reply-title`; **Columns** makes `.comment-form` a grid, name and email a column each, every other part the whole row; label keys to `.comment-form label`; the review box keys to `.comment-form-comment textarea`; the star keys to `.comment-form-rating .stars a`; the button keys to the `.form-submit` submit.
- No script or stylesheet of its own: the Reviews feature's files (`shop-reviews`) and WooCommerce's single product script.

## Wiring to other elements

- **Bricks' Product reviews steps aside.** Set **BFB Review list, Review form** `bfbeShopReviewsFormShow: "hide"` on Product reviews (or Product tabs) and place one BFB Review Form on the page: two forms share WooCommerce's `#commentform` and `#rating` ids (skill `bfbe-shop-reviews`).
- **Anywhere in Bricks' containers** on a product template: under the list, in a column beside it, in a popup on the product page. It reviews the page's product; a variation reviews its parent.
- **The same look keys** as the form inside Product reviews (the `bfbeShopReviewsForm*`, `bfbeShopReviewsUpload*`, `bfbeShopReviewsDrop*` and `bfbeShopReviewsPicked*` keys), plus **Title typography**, **Label typography** and **Resize**, which Product reviews takes from Bricks' own groups.
- **Photo limits** come from the Shop page (BFB Elements, Shop, Products, card **Reviews**: photos per review, largest photo), not from the element.
- After a post WordPress moderates the review and sends the shopper back to the product; the new review joins Bricks' list, any BFB Shop reviews loop and BFB Rating Summary once approved.
- Give it a class in `_cssClasses` for your own CSS. Nothing targets it, and it targets nothing.

## Verified patterns

**The form under the list, in the list's column.** From the demo shop's product template (Fernhouse product page, section "Reviews", "The reviews and the form"). Product reviews hides its own form; BFB Review Form follows it in the same Block, one field per row, a review box that opens 120 px tall, large stars and the drop area for photos. Trimmed: the brand's colour variables (hex kept), typography and the drop area's colours.

```json
{
  "name": "block",
  "settings": { "_rowGap": "20px", "_cssClasses": "reviews-column" },
  "children": [
    { "name": "product-reviews", "settings": { "bfbeShopReviewsFormShow": "hide", "bfbeShopReviewsListTitle": "hide", "bfbeShopReviewsListGap": "12px" } },
    { "name": "bfbe-review-form", "settings": {
      "bfbeShopReviewsFormAreaBackground": { "hex": "#f7f8fa" },
      "bfbeShopReviewsFormAreaPadding": { "top": "14", "right": "14", "bottom": "14", "left": "14" },
      "bfbeShopReviewsFormBackground": { "hex": "#ffffff" },
      "bfbeShopReviewsFormBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "20", "right": "20", "bottom": "20", "left": "20" } },
      "bfbeShopReviewsFormTitleGap": "18px",
      "bfbeShopReviewsFormColumns": 1,
      "bfbeShopReviewsFormRowGap": "20px",
      "bfbeShopReviewsFormLabelGap": "8px",
      "bfbeShopReviewsFormTextHeight": "120px",
      "bfbeShopReviewsFormStarSize": "32px",
      "bfbeShopReviewsFormStarGap": "4px",
      "bfbeShopReviewsFormStarOn": { "hex": "#f5a524" },
      "bfbeShopReviewsUploadLook": "custom",
      "bfbeShopReviewsDropTitle": "Drag photos of it in your home here",
      "bfbeShopReviewsPickedSize": "72px",
      "_cssClasses": "reviews-form" } }
  ]
}
```

**The form in a column of its own, beside the list.** From the fixture template `bfbe-shop-product-p4-reviews` ("Reviews and the form, side by side"). A Bricks grid of 3fr and 2fr; the form takes WooCommerce's words and the element's defaults.

```json
{
  "name": "block",
  "settings": { "_display": "grid", "_gridTemplateColumns": "3fr 2fr", "_columnGap": "48px", "_alignItems": "start", "_cssClasses": "reviews-beside" },
  "children": [
    { "name": "product-reviews", "settings": { "bfbeShopReviewsFormShow": "hide" } },
    { "name": "bfbe-review-form", "settings": { "_cssClasses": "reviews-form" } }
  ]
}
```

## Gotchas

- **One form per page.** With Bricks' form still shown, the page has two `#commentform` and two `#rating`, and WooCommerce's script draws the stars for the first only. <!-- src: docs/elements/review-form.md "Placing it" ; plugins/bfb-elements-pro/elements/review-form.php:145-146 -->
- **It needs the Reviews feature and a product.** Without the feature, off a product, or on a product with reviews closed, the page gets nothing; the canvas says which. <!-- src: plugins/bfb-elements-pro/elements/review-form.php:101-118 -->
- **Verified owners only, no form for others.** With WooCommerce's **Reviews can only be left by "verified owners"** on, a visitor who has not bought the product sees WooCommerce's line alone. In the builder that visitor is you, so the canvas shows the line and the look controls style nothing there. <!-- src: plugins/bfb-elements-pro/elements/review-form.php:129-132 -->
- **No stars without WooCommerce's ratings.** With **Enable star rating on reviews** off in WooCommerce, the rating field is not printed and the star keys style nothing. <!-- src: plugins/bfb-elements-pro/elements/review-form.php:183-192 -->
- **The title is a span.** WooCommerce's title is `span#reply-title` with `role="heading"` and `aria-level="3"`; its level does not change. Empty **Title** reads "Add a review", or "Be the first to review" the product while it has none. <!-- src: plugins/bfb-elements-pro/elements/review-form.php:134-136 ; plugins/bfb-elements-pro/elements/review-form.php:162 -->
- **Height is where the box opens.** **Height** (`bfbeShopReviewsFormTextHeight`) writes height and min-height, so the box opens at it, full width, and a drag cannot shrink it below. <!-- src: plugins/bfb-elements-pro/includes/shop/class-reviews.php:540-551 -->
- **Resize unset is vertical.** The element's stylesheet sets `resize: vertical` on the box although the **Resize** placeholder reads Both; set `bfbeShopReviewsFormTextResize` to say. <!-- src: src/elements/shop-reviews/shop-reviews.css:72 ; plugins/bfb-elements-pro/includes/shop/class-reviews.php:571-582 -->
- **Row and column gaps need Columns.** `bfbeShopReviewsFormRowGap` and `bfbeShopReviewsFormColumnGap` show only with **Columns** set, which turns the form into the grid they space. <!-- src: plugins/bfb-elements-pro/includes/shop/class-reviews.php:405 ; plugins/bfb-elements-pro/includes/shop/class-reviews.php:464-490 -->
- **Each upload look has its own keys.** The `bfbeShopReviewsUpload*` colours style the browser's file box; `bfbeShopReviewsDropTitle`, `bfbeShopReviewsDropButtonWords` and the `Drop*` and `Picked*` keys need `bfbeShopReviewsUploadLook: "custom"`. <!-- src: plugins/bfb-elements-pro/includes/shop/class-reviews.php:398-403 ; plugins/bfb-elements-pro/includes/shop/class-reviews.php:1300-1304 -->
- **The post is a page load.** The form posts to `wp-comments-post.php`, WordPress holds or approves the review and sends the shopper back to the product; nothing is posted in place. Without a script the rating is WooCommerce's plain select. <!-- src: docs/elements/review-form.md "What works without JavaScript" -->

## Never do

- Do not place a BFB Review Form while Product reviews or Product tabs still shows its form; set `bfbeShopReviewsFormShow: "hide"` there.
- Do not place two BFB Review Forms on one page.
- Do not put it on a page that is not a product; it prints nothing there.
- Do not set `bfbeShopReviewsFormRowGap` or `bfbeShopReviewsFormColumnGap` without `bfbeShopReviewsFormColumns`.
- Do not set the `bfbeShopReviewsDrop*` or `bfbeShopReviewsPicked*` keys without `bfbeShopReviewsUploadLook: "custom"`.
