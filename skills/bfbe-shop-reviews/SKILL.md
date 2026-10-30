---
name: bfbe-shop-reviews
description: "Use for the shop's settings on Bricks' Product reviews and Product tabs: review photos, helpful votes, sorting, the review list and form look, extra tabs from templates (BFB Shop reviews, `shop-reviews`). Read before writing these settings."
---

# BFB Shop reviews (`shop-reviews`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 2.0.0 or later, and BFB Elements Pro 2.0.0 or later for the groups marked Pro, WooCommerce active, the feature switches on (WordPress menu BFB Elements, Elements): `shop-reviews-loop`, `shop-reviews`, `shop-tabs`. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/shop-reviews.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/shop-reviews/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

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
- `bfbeShopReviewsListTitle` (select) **List title**: options: `show` Shown (default), `hide` Hidden; writes CSS
Styling, in the schema file: `bfbeShopReviewsListGap`, `bfbeShopReviewsItemBackground`, `bfbeShopReviewsItemBorder`, `bfbeShopReviewsItemPadding`, `bfbeShopReviewsTextBorder`.

#### BFB Review form (`bfbeShopReviewForm`)
Pro, switch `shop-reviews`.
- `bfbeShopReviewsUploadLook` (select) **Look**: options: `native` The browser's file box, `custom` A drop area with previews
- `bfbeShopReviewsDropTitle` (text) **Words**: placeholder Drag your photos here; only when `bfbeShopReviewsUploadLook` is `custom`
- `bfbeShopReviewsDropButtonWords` (text) **Button words**: placeholder Choose photos; only when `bfbeShopReviewsUploadLook` is `custom`
Styling, in the schema file: `bfbeShopReviewsFormSpace`, `bfbeShopReviewsFormAreaBackground`, `bfbeShopReviewsFormAreaBorder`, `bfbeShopReviewsFormAreaPadding`, `bfbeShopReviewsFormBackground`, `bfbeShopReviewsFormBorder`, `bfbeShopReviewsFormPadding`, `bfbeShopReviewsFormTitleGap`, `bfbeShopReviewsFormColumns`, `bfbeShopReviewsFormRowGap`, `bfbeShopReviewsFormColumnGap`, `bfbeShopReviewsFormNotes`, `bfbeShopReviewsFormLabelGap`, `bfbeShopReviewsFormRequired`, `bfbeShopReviewsFormConsentGap`, `bfbeShopReviewsFormConsent`, `bfbeShopReviewsFormTextHeight`, `bfbeShopReviewsFormTextPadding`, `bfbeShopReviewsFormTextBorder`, `bfbeShopReviewsFormTextTypography`, `bfbeShopReviewsFormStarSize`, `bfbeShopReviewsFormStarGap`, `bfbeShopReviewsFormStarColor`, `bfbeShopReviewsFormStarOn`, `bfbeShopReviewsUploadBackground`, `bfbeShopReviewsUploadBorder`, `bfbeShopReviewsUploadButton`, `bfbeShopReviewsUploadButtonHover`, `bfbeShopReviewsUploadButtonText`, `bfbeShopReviewsUploadHelp`, `bfbeShopReviewsDropBackground`, `bfbeShopReviewsDropBorder`, `bfbeShopReviewsDropPadding`, `bfbeShopReviewsDropGap`, `bfbeShopReviewsDropOver`, `bfbeShopReviewsDropOverLine`, `bfbeShopReviewsDropIconSize`, `bfbeShopReviewsDropIconColor`, `bfbeShopReviewsDropTypography`, `bfbeShopReviewsDropButtonBackground`, `bfbeShopReviewsDropButtonColor`, `bfbeShopReviewsDropButtonHover`, `bfbeShopReviewsDropButtonHoverColor`, `bfbeShopReviewsDropButtonBorder`, `bfbeShopReviewsDropButtonPadding`, `bfbeShopReviewsDropButtonTypography`, `bfbeShopReviewsPickedSize`, `bfbeShopReviewsPickedBorder`, `bfbeShopReviewsPickedRemove`, `bfbeShopReviewsFormButtonPadding`, `bfbeShopReviewsFormButtonTypography`.

### Product tabs (`product-tabs`)

#### BFB Review list (`bfbeShopReviewList`)
The same 7 controls as on `product-reviews`.

#### BFB Review form (`bfbeShopReviewForm`)
Pro, switch `shop-reviews`.
- `bfbeShopReviewsFormTextResize` (select) **Resize**: options: `none` None, `vertical` Vertical, `horizontal` Horizontal, `both` Both (default); writes CSS
- `bfbeShopReviewsUploadLook` (select) **Look**: options: `native` The browser's file box, `custom` A drop area with previews
- `bfbeShopReviewsDropTitle` (text) **Words**: placeholder Drag your photos here; only when `bfbeShopReviewsUploadLook` is `custom`
- `bfbeShopReviewsDropButtonWords` (text) **Button words**: placeholder Choose photos; only when `bfbeShopReviewsUploadLook` is `custom`
Styling, in the schema file: `bfbeShopReviewsFormSpace`, `bfbeShopReviewsFormAreaBackground`, `bfbeShopReviewsFormAreaBorder`, `bfbeShopReviewsFormAreaPadding`, `bfbeShopReviewsFormBackground`, `bfbeShopReviewsFormBorder`, `bfbeShopReviewsFormPadding`, `bfbeShopReviewsFormTitleTypography`, `bfbeShopReviewsFormTitleGap`, `bfbeShopReviewsFormColumns`, `bfbeShopReviewsFormRowGap`, `bfbeShopReviewsFormColumnGap`, `bfbeShopReviewsFormNotes`, `bfbeShopReviewsFormLabel`, `bfbeShopReviewsFormLabelGap`, `bfbeShopReviewsFormRequired`, `bfbeShopReviewsFormConsentGap`, `bfbeShopReviewsFormConsent`, `bfbeShopReviewsFormTextHeight`, `bfbeShopReviewsFormTextPadding`, `bfbeShopReviewsFormTextBorder`, `bfbeShopReviewsFormTextTypography`, `bfbeShopReviewsFormStarSize`, `bfbeShopReviewsFormStarGap`, `bfbeShopReviewsFormStarColor`, `bfbeShopReviewsFormStarOn`, `bfbeShopReviewsUploadBackground`, `bfbeShopReviewsUploadBorder`, `bfbeShopReviewsUploadButton`, `bfbeShopReviewsUploadButtonHover`, `bfbeShopReviewsUploadButtonText`, `bfbeShopReviewsUploadHelp`, `bfbeShopReviewsDropBackground`, `bfbeShopReviewsDropBorder`, `bfbeShopReviewsDropPadding`, `bfbeShopReviewsDropGap`, `bfbeShopReviewsDropOver`, `bfbeShopReviewsDropOverLine`, `bfbeShopReviewsDropIconSize`, `bfbeShopReviewsDropIconColor`, `bfbeShopReviewsDropTypography`, `bfbeShopReviewsDropButtonBackground`, `bfbeShopReviewsDropButtonColor`, `bfbeShopReviewsDropButtonHover`, `bfbeShopReviewsDropButtonHoverColor`, `bfbeShopReviewsDropButtonBorder`, `bfbeShopReviewsDropButtonPadding`, `bfbeShopReviewsDropButtonTypography`, `bfbeShopReviewsPickedSize`, `bfbeShopReviewsPickedBorder`, `bfbeShopReviewsPickedRemove`, `bfbeShopReviewsFormButtonPadding`, `bfbeShopReviewsFormButtonTypography`.

#### BFB Tabs (`bfbeShopTabs`)
Pro, switch `shop-tabs`.
- `bfbeShopTabsLeaveOut` (select) **Leave out WooCommerce's tabs**: options: `description` Description, `additional_information` Additional information, `reviews` Reviews. Reviews: when the page shows its own reviews.
Styling, in the schema file: `bfbeShopTabsGap`, `bfbeShopTabsTabBackground`, `bfbeShopTabsTabBorder`, `bfbeShopTabsLinkPadding`, `bfbeShopTabsActiveBorder`, `bfbeShopTabsHoverBackground`, `bfbeShopTabsHoverColor`, `bfbeShopTabsCellPadding`, `bfbeShopTabsCellBorder`.
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
