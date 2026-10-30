---
name: bfbe-product-questions
description: "Use when placing, wiring or styling BFB Product Questions (`bfbe-product-questions`). Read before writing its settings."
---

# BFB Product Questions (`bfbe-product-questions`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-product-questions.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/product-questions/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 0.79 KB, JS 0.60 KB (gzipped), no dependencies, loaded only on pages that use it.

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Questions (`bfbeQuestions`)
- `shows` (select) **Shows**: options: `both` Questions and the form (default), `list` Questions only, `form` Form only
- `title` (text) **Title**: placeholder Questions and answers; dynamic data accepted; only when `shows` is not `form`. Still names the section when the tag is None.
- `titleTag` (select) **Title tag**: options: `h2` H2, `h3` H3 (default), `h4` H4, `p` p, `none` None; only when `shows` is not `form`
- `most` (number) **Questions shown**: placeholder 10; only when `shows` is not `form`
- `none` (text) **None yet**: placeholder No questions answered yet. Be the first to ask.; dynamic data accepted; only when `shows` is not `form`
- `meta` (select) **Under each question**: options: `both` Who asked and when (default), `who` Who asked, `none` Nothing; only when `shows` is not `form`
- `helpful` (select) **Was this helpful**: options: `show` Under each answer (default), `hide` Hidden; only when `shows` is not `form`
Styling, in the schema file: `titleTypography`, `titleMargin`, `noneTypography`, `listGap`, `cardBackground`, `cardBorder`, `cardPadding`, `cardShadow`, `openBackground`, `openBorder`, `questionTypography`, `questionHoverColor`, `questionPadding`, `markSize`, `markBackground`, `markColor`, `markBorder`, `answerTypography`, `metaTypography`, `voteTypography`, `voteBackground`, `voteBorder`, `votePadding`, `votePressedBackground`, `votePressedColor`.

### Ask a question (`bfbeAsk`)
The whole group shows only when `shows` is not `list`.
- `askTitle` (text) **Form title**: placeholder Ask a question; only when `shows` is not `list`
- `nameLabel` (text) **Name label**: placeholder Your name; only when `shows` is not `list`
- `emailLabel` (text) **Email label**: placeholder Your email; only when `shows` is not `list`
- `questionLabel` (text) **Question label**: placeholder Your question; only when `shows` is not `list`
- `button` (text) **Button**: placeholder Ask; only when `shows` is not `list`
- `thanks` (text) **Thank you text**: placeholder Thank you. Your question is with the shop and will show here once it is answered.; only when `shows` is not `list`
Styling, in the schema file: `askBackground`, `askBorder`, `askPadding`, `askTitleTypography`, `fieldLabelTypography`, `fieldsGap`, `inputTypography`, `inputBackground`, `inputBorder`, `inputPadding`, `inputFocusBorder`, `buttonTypography`, `buttonBackground`, `buttonBorder`, `buttonPadding`, `buttonHoverBackground`, `buttonHoverColor`, `statusTypography`, `errorColor`.
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
