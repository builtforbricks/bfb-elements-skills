---
name: bfbe-review-form
description: "Use when placing, wiring or styling BFB Review Form (`bfbe-review-form`). Read before writing its settings."
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

_Not written yet._

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
