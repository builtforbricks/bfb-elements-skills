---
name: bfbe-product-questions
description: "Use when adding shopper questions and the shop's answers to a product page with `bfbe-product-questions`: the answered list, the ask form, or the two placed apart as separate instances."
---

# BFB Product Questions (`bfbe-product-questions`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-product-questions.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/product-questions/

## What it is
Questions shoppers asked about the product, with the shop's answers, as a list where each question opens, and a form to ask a new one. A question is a WordPress comment of its own type on the product, held until the shop answers it, so it never mixes with the reviews or their rating. Show the list, the form or both, so the form can sit in a popup, a tab or a sidebar of your own.

**Not for:** It does not answer questions by itself, suggest answers or email the asker when the answer is published, and other shoppers cannot answer: only the shop does. For reviews with a star rating, use Bricks' Product reviews.

**Costs a page:** CSS 0.82 KB, JS 0.64 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** no · **In a query loop:** no · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Questions (`bfbeQuestions`)
- `shows` (select) **Shows**: options: `both` Questions and the form (default), `list` Questions only, `form` Form only. Questions and the form by default, Questions only or Form only. The form is whole on its own, so a second Product Questions set to the form can sit in a popup, a tab or a sidebar.
- `title` (text) **Title**: placeholder Questions and answers; dynamic data accepted; only when `shows` is not `form`. Questions and answers when empty, with dynamic data. **Title tag**: H3 by default, or H2, H4, p, or None for a list under a Bricks heading of your own, when the section takes the title's words as its name.
- `titleTag` (select) **Title tag**: options: `h2` H2, `h3` H3 (default), `h4` H4, `p` p, `none` None; only when `shows` is not `form`
- `most` (number) **Questions shown**: placeholder 10; only when `shows` is not `form`. The newest answered questions, 10 when empty, up to 100. **None yet**: what shows while no question has an answer.
- `none` (text) **None yet**: placeholder No questions answered yet. Be the first to ask.; dynamic data accepted; only when `shows` is not `form`
- `meta` (select) **Under each question**: options: `both` Who asked and when (default), `who` Who asked, `none` Nothing; only when `shows` is not `form`. Who asked and when by default, Who asked, or Nothing; the same goes under each answer.
- `helpful` (select) **Was this helpful**: options: `show` Under each answer (default), `hide` Hidden; only when `shows` is not `form`. Under each answer by default, or Hidden. It is the Reviews feature's Helpful vote, so it shows only where that feature and its Helpful votes switch are on.
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

## What it guarantees for accessibility (do not undo)
- The list is a list of details elements, newest first, the top one open; each question is the summary, so it opens and closes from the keyboard as any disclosure does.
- The Q and A marks are hidden from screen readers. With Title tag None, the section takes the title's words as its name.
- The form is a real form with labelled fields and a legend naming it. After sending, a line under it says the question is with the shop, and the shop's announcer says it once.
- With reduced motion requested, the open and close arrow turns at once.
- Without JavaScript the form posts to the product's own page, which comes back with WooCommerce's notice in Bricks' WooCommerce Notice element.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<section id="brxe-{id}" class="brxe-bfbe-product-questions bfbe-qa" data-bfbe-qa="{product id}" aria-labelledby="bfbe-{uid}-qa-title">
  <h3 class="bfbe-qa__title" id="bfbe-{uid}-qa-title">Questions and answers</h3>  <!-- titleTag none: no heading, aria-label on the section -->
  <ol class="bfbe-qa__list">                                                       <!-- or p.bfbe-qa__none while nothing is answered -->
    <li class="bfbe-qa__item"><details class="bfbe-qa__details" id="bfbe-{uid}-qa-q{comment id}" open>
      <summary class="bfbe-qa__question"><span class="bfbe-qa__q" aria-hidden="true">Q</span><span class="bfbe-qa__question-text">…</span></summary>
      <p class="bfbe-qa__meta">Asked by Mara on 17 October 2026</p>
      <div class="bfbe-qa__answer"><span class="bfbe-qa__a" aria-hidden="true">A</span>
        <div class="bfbe-qa__answer-body"><p>…</p><p class="bfbe-qa__meta">Answered by …</p><div class="bfbe-rv__vote">…</div></div></div>
    </details></li>
  </ol>
  <form class="bfbe-qa__ask" method="post" data-bfbe-qa-ask data-bfbe-qa-thanks="…">
    <!-- the shop's action and nonce fields, then --><input type="hidden" name="product" value="{product id}">
    <fieldset class="bfbe-qa__set"><legend class="bfbe-qa__ask-title">Ask a question</legend>
      <div class="bfbe-qa__fields"><label class="bfbe-qa__field">… bfbe_name</label><label class="bfbe-qa__field">… bfbe_email</label>
        <label class="bfbe-qa__field bfbe-qa__field--wide">… <textarea name="bfbe_question"></textarea></label><label class="bfbe-qa__hp" aria-hidden="true">…</label></div>
      <button type="submit" class="bfbe-qa__send bfbe-chip">Ask</button><p class="bfbe-qa__status" data-bfbe-qa-status hidden></p>
    </fieldset>
  </form>
</section>
```

- **Shows** `shows` decides the root: `both` and `list` print the `section` (the list alone has no form); `form` prints a plain `div.bfbe-qa` holding the form only, named by its legend.
- The list is `details` and `summary`, newest first, the first one `open`. States: `[open]` on a card; `disabled` on `.bfbe-qa__send` while sending; `.bfbe-qa__status` unhidden after, with `is-error` on a refusal.
- Where controls write: `card*` to `.bfbe-qa__details`, `openBackground` and `openBorder` to `.bfbe-qa__details[open]`, `question*` to `.bfbe-qa__question`, `mark*` to `.bfbe-qa__q, .bfbe-qa__a`, `answerTypography` to `.bfbe-qa__answer-body`, `metaTypography` to `.bfbe-qa__meta`, `listGap` to the list's `row-gap`, `vote*` to the Reviews feature's `.bfbe-rv__btn`. On the form: `ask*` to `.bfbe-qa__ask`, `input*` to the fields, `button*` to `.bfbe-qa__send`, `statusTypography` and `errorColor` to `.bfbe-qa__status`.

## Wiring to other elements

- **Two instances, placed apart.** The form is whole on its own (the product's id, the nonce fields, its own script binding), so one instance with `shows: "list"` and a second with `shows: "form"` can sit in any two Bricks containers: side by side, the form in a popup, a Tabs pane or a sidebar. Both read the same product.
- **Under your own heading.** With `titleTag: "none"` the list prints no title; put a Bricks `heading` before it and keep **Title** `title` set to the same words, which become the section's name.
- **Was this helpful** is the Reviews feature's vote (`shop-reviews`, skill `bfbe-shop-reviews`): it shows under answers only where that feature and its **Helpful votes** switch are on.
- **Bricks' Notice element** (`woocommerce-notice`) on the product template shows the answer to a form sent without a script, as WooCommerce's notice.
- **The shop answers** in WooCommerce's Products, Reviews screen with **Reply** on the question; approving the pair publishes it. Nothing on the page targets the element by attribute; `_cssClasses` is for your own CSS.

## Verified patterns

**The list and the form side by side** (fixture template `bfbe-shop-product-p4-reviews`, `.p4-apart-qa`). Two instances, each set to one part: the list under a Bricks heading with `titleTag: "none"` and `title` matching it, the form in a padded box of its own with its own **Form title** `askTitle`. Use on a product template; the element needs a product.

```json
{
  "name": "block",
  "settings": { "_display": "grid", "_gridTemplateColumns": "3fr 2fr", "_columnGap": "32px", "_alignItems": "start", "_cssClasses": "p4-apart-qa" },
  "children": [
    { "name": "block", "settings": { "_rowGap": "12px" }, "children": [
      { "name": "heading", "settings": { "text": "Asked by other shoppers", "tag": "h2" } },
      { "name": "bfbe-product-questions", "settings": { "shows": "list", "titleTag": "none", "title": "Asked by other shoppers", "_cssClasses": "p4-qa-list" } }
    ] },
    { "name": "block", "settings": { "_padding": { "top": "20px", "right": "20px", "bottom": "20px", "left": "20px" } }, "children": [
      { "name": "bfbe-product-questions", "settings": { "shows": "form", "askTitle": "Ask the shop", "button": "Send", "_cssClasses": "p4-qa-form" } }
    ] }
  ]
}
```

**List and form in one, as a section of the page** (fixture template `bfbe-shop-product-p4`, `.p4-qa`, with the demo shop's words). The default `shows` prints both; `titleTag: "h2"` because the section stands on its own, `most: 6` keeps the six newest answered questions.

```json
{
  "name": "block",
  "settings": { "_rowGap": "32px" },
  "children": [
    { "name": "product-tabs", "settings": {} },
    { "name": "bfbe-product-questions", "settings": { "title": "Questions and answers", "titleTag": "h2", "most": 6, "none": "No answered questions yet. Ask the first one.", "askTitle": "Ask us about it", "button": "Send my question", "_cssClasses": "p4-qa" } }
  ]
}
```

## Gotchas

- **Only answered questions show.** A question appears once it is approved and has an approved answer; a new one is held, so a new shop shows **None yet** `none` until the shop replies. <!-- src: plugins/bfb-elements-pro/includes/shop/class-questions.php:192 ; docs/elements/product-questions.md "How the shop answers" -->
- **`shows` hides the other part's controls.** With `form`, the Questions group's keys (`title`, `titleTag`, `most`, `none`, `meta`, `helpful` and their look) are hidden; with `list`, the whole Ask a question group is. <!-- src: plugins/bfb-elements-pro/elements/product-questions.php:657 ; ../bfbe-schemas/references/elements/bfbe-product-questions.json -->
- **`ask` is gone.** **Shows** replaced the earlier `ask` control in 2.0.0; the render reads `shows` alone, so an `ask` setting changes nothing. <!-- src: docs/SHOP-LABELS-2.0.0.md "BFB Product Questions" (ask removed) ; plugins/bfb-elements-pro/elements/product-questions.php:647 -->
- **Title tag None still needs the title.** `titleTag: "none"` prints no heading, but `title` (else "Questions and answers") becomes the section's `aria-label`. <!-- src: plugins/bfb-elements-pro/elements/product-questions.php:667 -->
- **The vote needs the Reviews feature.** `helpful: "show"` draws nothing unless `shop-reviews` and its Helpful votes switch are on; the canvas then draws a sample with Yes pressed. <!-- src: plugins/bfb-elements-pro/elements/product-questions.php:625 ; plugins/bfb-elements-pro/elements/product-questions.php:651 -->
- **Without a script the answer is a WooCommerce notice.** The form posts to the product's page and the result shows only where Bricks' Notice element sits on the template. <!-- src: docs/elements/product-questions.md "What works without JavaScript" ; src/elements/product-questions/product-questions.js:2 -->
- **A signed-in visitor's page is not cached.** The form fills the customer's name and email, so it sets `DONOTCACHEPAGE` and page caches skip that page. <!-- src: plugins/bfb-elements-pro/elements/product-questions.php:735 -->
- **Questions shown reads a window.** `most` is 1 to 100 (10 empty), but only the newest `most` times three approved questions are looked at, so many unanswered approved ones can leave fewer cards. <!-- src: plugins/bfb-elements-pro/elements/product-questions.php:648 ; plugins/bfb-elements-pro/includes/shop/class-questions.php:200 -->
- **The form refuses more than it shows.** A question takes 10 to 500 characters; five an hour per address, WordPress' flood and duplicate checks and a honeypot field apply. <!-- src: plugins/bfb-elements-pro/includes/shop/class-questions.php:107-112 ; plugins/bfb-elements-pro/includes/shop/class-questions.php:162 ; plugins/bfb-elements-pro/elements/product-questions.php:746 -->
- **Switched off, no question is taken.** With the element switched off (the Elements page, or Bricks' Element Manager) a question is refused whoever sends it, also from a page drawn before (since Pro 2.1.1). <!-- src: plugins/bfb-elements-pro/includes/shop/class-questions.php:76 -->
- **The site's comment settings are not followed.** "Comments open" on the product and "Users must be registered and logged in to comment" do not close the form: closing reviews does not close questions. To decide who may ask, a site adds the filter `bfbe/shop/questions/may_ask` (true, the product's id, the visitor); `add_filter( 'bfbe/shop/questions/may_ask', 'is_user_logged_in' );` takes questions from signed-in visitors only (since Pro 2.1.1). No setting of the element does this. <!-- src: plugins/bfb-elements-pro/includes/shop/class-questions.php:92 ; docs/elements/product-questions.md "What is stored, and the limits" -->
- **Variations share the parent's questions.** `data-bfbe-qa` and the form's `product` are the parent's id. <!-- src: plugins/bfb-elements-pro/elements/product-questions.php:646 -->
- **Only the shop answers.** A reply from anyone who cannot moderate comments is refused. <!-- src: plugins/bfb-elements-pro/includes/shop/class-questions.php:178 -->
- **No product, no element.** Outside a product template or a product loop the page gets nothing and the canvas a notice; set the template's preview product. <!-- src: plugins/bfb-elements-pro/elements/product-questions.php:642 -->

## Never do

- Do not set Questions keys with `shows: "form"`, or Ask a question keys with `shows: "list"`.
- Do not set `ask`; use `shows`.
- Do not pair a `shows: "both"` instance with a `shows: "form"` one on the same page; that prints two forms.
- Do not set `titleTag: "none"` without a heading of your own before the list.
- Do not count on `helpful` where the Reviews feature's Helpful votes are off.
- Do not leave a template that takes questions without Bricks' Notice element.
