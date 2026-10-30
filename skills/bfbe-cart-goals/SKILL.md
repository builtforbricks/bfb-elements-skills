---
name: bfbe-cart-goals
description: "Use for BFB Cart Goals (`bfbe-cart-goals`): a progress bar towards free shipping, a free gift or a discount, the sentence of what is left, the free gift chooser, and each part placed apart with Shows. Read before writing its settings."
---

# BFB Cart Goals (`bfbe-cart-goals`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-cart-goals.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/cart-goals/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 0.99 KB, JS 1.77 KB (gzipped), no dependencies, loaded only on pages that use it.

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Goals (`bfbeGoals`)
- `shows` (select) **Shows**: options: `all` Sentence, track and gift choice (default), `sentence` Sentence only, `track` Track only, `gifts` Gift choice only. Place a second one to put a part elsewhere.
- `nextOnly` (checkbox) **Next goal only**
- `steps` (select) **Steps**: options: `show` Show (default), `hide` Hide
- `toGo` (text) **Before a goal**: placeholder {amount} to go for {label}
- `reachedText` (text) **Goal reached**: placeholder Reached: {label}
- `allText` (text) **All reached**: placeholder You have every reward.

### Gift choice (`bfbeGift`)
The whole group shows only when `shows` is not `sentence` or `track`.
- `gifts` (text) **Gift choices**: placeholder Ids or SKUs, comma-separated
- `giftWord` (text) **Chooser heading**: placeholder Choose your free gift; only when `gifts` is set
- `chooseWord` (text) **Button**: placeholder Choose; only when `gifts` is set
- `choicesAs` (select) **Choices as**: options: `radios` Radios (default), `pills` Pills; only when `gifts` is set
- `radioLook` (select) **Radios**: options: `native` As the browser draws it (default), `custom` Styled with the controls below; only when `gifts` is set and `choicesAs` is not `pills`
Styling, in the schema file: `legendTypography`, `choiceTypography`, `legendSpace`, `choiceGap`, `radioGap`, `boxBackground`, `boxBorder`, `boxPadding`, `radioColor`, `radioTickSize`, `radioTickBg`, `radioTickBorder`, `radioTickHover`, `radioTickOnLine`, `radioTickMarkColor`, `pillBackground`, `pillColor`, `pillBorder`, `pillPadding`, `pillHoverBackground`, `pillHoverBorder`, `pillOnBackground`, `pillOnColor`, `pillOnBorder`.

### Track (`bfbeTrack`)
The whole group shows only when `shows` is not `gifts`.
- `labelDisplay` (select) **Goal names**: options: `block` Show (default), `none` Hide; writes CSS; only when `steps` is not `hide`
Styling, in the schema file: `gap`, `textTypography`, `trackHeight`, `trackColor`, `fillColor`, `trackBorder`, `stepTypography`, `thresholdTypography`, `reachedTypography`, `markColor`, `markBorder`.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<div class="brxe-bfbe-cart-goals bfbe-goals bfbe-goals--js" data-bfbe-shop-need="cart,goals"
     data-bfbe-goals-shows="track" data-bfbe-choices="pills" data-bfbe-tick="dot"
     data-bfbe-goals='{"post":412,"el":"a1b2c3","next":false,"words":{"toGo":"…","reached":"…","all":"…"}}'>
  <p class="bfbe-goals__text" id="bfbe-{uid}-text">34,00 € to go for Free shipping</p>
  <!-- shows: "track" prints <span class="bfbe-goals__said" id="bfbe-{uid}-text" hidden> instead of the p -->
  <div class="bfbe-goals__track" role="progressbar" aria-label="Cart goals" aria-describedby="bfbe-{uid}-text"
       aria-valuemin="0" aria-valuemax="300" aria-valuenow="16" aria-valuetext="34,00 € to go for Free shipping">
    <span class="bfbe-goals__fill" style="--bfbe-goals-now:5.33%"></span></div>
  <ol class="bfbe-goals__steps">
    <li class="bfbe-goals__step is-reached" style="--bfbe-goals-at:16.67%" data-goal="0"><span class="bfbe-goals__mark" aria-hidden="true"></span>
      <span class="bfbe-goals__label">Free shipping</span><span class="bfbe-goals__threshold">50,00 €</span></li>…</ol>
  <form class="bfbe-goals__gifts" method="post" data-goal="2" hidden><!-- bfbe_shop_act=goal_gift, g, post, el -->
    <fieldset class="bfbe-goals__set"><legend class="bfbe-goals__legend">Choose your free gift</legend>
      <label class="bfbe-goals__gift-choice" for="…"><input type="radio" class="bfbe-tick" name="p" value="{id}" checked>
        <span class="bfbe-goals__gift-name">Beeswax Candles</span></label>…</fieldset>
    <button type="submit" class="bfbe-goals__choose">Choose</button></form>
</div>
```

- Root `div.bfbe-goals`, a flex column that stretches to its column. `data-bfbe-goals-shows` appears only when **Shows** `shows` is not `all`; `data-bfbe-choices="pills"` with **Choices as** `choicesAs: "pills"`; `data-bfbe-tick` only with **Radios** `radioLook: "custom"`. The script adds `bfbe-goals--js`, which hides the Choose button.
- The track is a real `progressbar`; the sentence is its value text and its description. The fill's width is `--bfbe-goals-now`, each step's place `--bfbe-goals-at`; reached steps carry `is-reached`. The script rewrites the words, the bar's values and the whole `ol` from every live answer.
- One `form.bfbe-goals__gifts` per free gift goal with a set to choose from, `hidden` until that goal is reached. A gift choice placed alone (`shows: "gifts"`) puts `hidden` on the root as well.
- Where controls write: `gap` to the root's `row-gap` and `--bfbe-goals-gap`; `trackHeight` to `--bfbe-goals-h`; `trackColor` and `trackBorder` to `.bfbe-goals__track`; `fillColor` to `.bfbe-goals__fill` and reached marks; `markColor` to marks not reached; `textTypography` to `.bfbe-goals__text`; `stepTypography`, `thresholdTypography`, `reachedTypography` and `labelDisplay` to the step parts; `box*` to `.bfbe-goals__gifts`; `pill*` to `.bfbe-goals__gift-choice` under `[data-bfbe-choices="pills"]`.

## Wiring to other elements

- **The goals live on the Shop page**, not the element: BFB Elements, Shop, Cart & checkout, card **Cart goals**. Each row has **Goal** (Cart total or Number of items), **Target**, **Reward** (Free shipping, A free gift, A percentage off, A fixed amount off, A message only), **Amount off**, **Gift product** and **Name shoppers see**. The server applies the rewards on every cart count; the element only draws them.
- **Every instance draws the same goals.** One in the cart, one in the mini cart's template and one in the header never disagree: each paints from the shared live answer (`goals`), so a cached page is right after load.
- **Parts placed apart are separate instances** with **Shows**: the sentence in a header (`sentence`), the bar and steps under the cart (`track`), the gift choice beside the totals (`gifts`). Give each the same words (`toGo`, `reachedText`, `allText`).
- **In a popup or a cart of your own**, put it inside a Container with BFB Live cart (`bfbeLiveCart`, skill `bfbe-shop-cart-page`), as the demo's quick cart does; the element follows the cart either way.
- **Bricks' Interactions**: the trigger **Cart goal reached** (`bfbeGoalReached`, the event `bfbe/woo/goal-reached` with `{ goal, label, reward }`) needs the Shop data feature (skill `bfbe-shop-tags-and-conditions`). `{bfbe_cart_free_shipping_left}` and the cart conditions cover text of your own.
- **The gift line** it adds shows in Bricks' Cart items, the Mini cart and the order as "Free gift", quantity fixed at 1 with no remove link, and never gets a Save for later button.
- Give each instance a class in `_cssClasses` for your own CSS. Nothing targets it by attribute.

## Verified patterns

**The cart page, its parts apart.** From the demo shop's cart template (`bfb-demo-cart`, "Cart goals" and the totals column), colours resolved to hex, the shared words kept. The sentence and the track sit together in a tinted Block at the top; the gift choice, as pills, sits in the totals column and waits hidden until the gift's goal is reached. Each instance carries only the keys its **Shows** offers. `gifts` names the demo's SKUs: use the target shop's.

```json
{
  "name": "block",
  "settings": { "_rowGap": "24px" },
  "children": [
    { "name": "block", "settings": { "_rowGap": "14px", "_padding": { "top": "24", "right": "24", "bottom": "24", "left": "24" }, "_cssClasses": "cart-goals" }, "children": [
      { "name": "bfbe-cart-goals", "settings": { "shows": "sentence", "toGo": "{amount} more for {label}", "reachedText": "Yours: {label}", "allText": "You have every reward.", "textTypography": { "font-size": "16px", "font-weight": "700", "color": { "hex": "#101828" } } } },
      { "name": "bfbe-cart-goals", "settings": { "shows": "track", "toGo": "{amount} more for {label}", "reachedText": "Yours: {label}", "allText": "You have every reward.", "gap": "14", "trackHeight": "10", "trackColor": { "hex": "#f0ecff" }, "fillColor": { "hex": "#6e44ff" }, "stepTypography": { "font-size": "13px", "font-weight": "600", "color": { "hex": "#667085" } }, "labelDisplay:mobile_landscape": "none" } }
    ] },
    { "name": "bfbe-cart-goals", "settings": { "shows": "gifts", "toGo": "{amount} more for {label}", "reachedText": "Yours: {label}", "allText": "You have every reward.", "gifts": "DEMO-TOWEL-TEA, DEMO-CANDLE-BEES", "giftWord": "Choose your free gift", "choicesAs": "pills", "legendTypography": { "font-size": "16px", "font-weight": "800" }, "boxBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "20", "right": "20", "bottom": "20", "left": "20" } }, "boxPadding": { "top": "24", "right": "24", "bottom": "24", "left": "24" }, "pillPadding": { "top": "9", "right": "18", "bottom": "9", "left": "18" }, "pillOnBackground": { "hex": "#6e44ff" }, "pillOnBorder": { "hex": "#6e44ff" }, "pillOnColor": { "hex": "#ffffff" }, "_cssClasses": "cart-gift" } }
  ]
}
```

**The next goal only, for a small space.** From the demo's quick cart popup (`Fernhouse: the quick cart (a popup)`, inside its BFB Live cart region). **Next goal only** `nextOnly` keeps one goal on the track and `steps: "hide"` drops the steps, so the sentence and a thin bar fit a mini cart.

```json
{ "name": "bfbe-cart-goals", "settings": { "nextOnly": true, "steps": "hide", "toGo": "{amount} more for {label}", "reachedText": "Yours: {label}", "allText": "You have every reward.", "gap": "8", "trackHeight": "8", "trackColor": { "hex": "#f0ecff" }, "fillColor": { "hex": "#6e44ff" }, "textTypography": { "font-size": "14px", "font-weight": "600", "color": { "hex": "#101828" } }, "_padding": { "top": "14", "right": "16", "bottom": "14", "left": "16" }, "_cssClasses": "mini-goals" } }
```

## Gotchas

- **No goals, no output.** With no row on the Shop page's Cart goals card the page gets nothing and the canvas says "Add goals in BFB Elements > Shop > Cart & checkout." <!-- src: plugins/bfb-elements-pro/elements/cart-goals.php:508-515 -->
- **Free shipping counts to the zone's own minimum.** The goal reads the minimum of the visitor's Free shipping method; its **Target** shows only before the zone is known, and a zone without such a method leaves the goal out. <!-- src: plugins/bfb-elements-pro/includes/shop/class-cart-goals.php:200-212 --> <!-- src: docs/elements/cart-goals.md "The Shop page: Cart goals" -->
- **A chooser needs two products.** The goal's **Gift product** counts as one, so `gifts` must add at least one more. Only simple products that can be bought count; variable, grouped, external and sold-out ones are dropped quietly. <!-- src: plugins/bfb-elements-pro/includes/shop/class-cart-goals.php:162-172 ; plugins/bfb-elements-pro/includes/shop/class-cart-goals.php:481-505 ; plugins/bfb-elements-pro/elements/cart-goals.php:553-556 -->
- **A gift choice alone may print nothing.** With `shows: "gifts"` and no chooser, the page gets nothing and the canvas a notice; with one, the root stays `hidden` (with `!important`, so a Bricks display setting cannot show it) until a gift goal is reached. <!-- src: plugins/bfb-elements-pro/elements/cart-goals.php:559-572 ; src/elements/cart-goals/cart-goals.css:2 -->
- **The canvas shows every chooser.** In the builder the gift forms are drawn open whatever the cart; on the page each waits for its goal. <!-- src: plugins/bfb-elements-pro/elements/cart-goals.php:613 -->
- **The pick belongs to the element it was made on.** The server checks a choice against that element's saved `gifts`; take a product out of it and the Shop page's gift comes back. <!-- src: plugins/bfb-elements-pro/includes/shop/class-cart-goals.php:216-220 ; plugins/bfb-elements-pro/includes/shop/class-cart-goals.php:508-524 -->
- **The first instance on the page speaks.** The announcement "Reached: {label}" uses the first Cart Goals' **Goal reached** words, whichever part it shows. <!-- src: src/elements/cart-goals/cart-goals.js:84-95 -->
- **A goal reached before the tab's first answer is never announced.** The first answer sets the baseline in session storage; only goals crossed after it are said and fire `bfbe/woo/goal-reached`. <!-- src: src/elements/cart-goals/cart-goals.js:18-22 ; src/elements/cart-goals/cart-goals.js:89 -->
- **Space the parts with `gap`.** The marks climb `--bfbe-goals-gap` to sit on the track's middle; Bricks' universal `_rowGap` moves the parts but not the marks. <!-- src: plugins/bfb-elements-pro/elements/cart-goals.php:425-426 ; src/elements/cart-goals/cart-goals.css:42-48 -->
- **Close goals crowd their words.** Each step sits at its share of the track, up to 9em wide; hide the names per breakpoint (`labelDisplay:mobile_landscape: "none"`) or use `steps: "hide"`. <!-- src: src/elements/cart-goals/cart-goals.css:25-41 ; plugins/bfb-elements-pro/elements/cart-goals.php:401-415 -->
- **The scale changes with an item goal.** Amount goals share one money scale, ending at the last goal; with an item-count goal among them each goal is one equal step. <!-- src: plugins/bfb-elements-pro/elements/cart-goals.php:531-541 -->
- **Look keys need their switch.** `pill*` act only with `choicesAs: "pills"`; `radioTick*` only with `radioLook: "custom"`. <!-- src: plugins/bfb-elements-pro/elements/cart-goals.php:184-199 ; plugins/bfb-elements-pro/elements/cart-goals.php:352-354 -->

## Never do

- Do not place Cart Goals on a site whose Shop page has no goals.
- Do not write Gift choice keys with `shows: "sentence"` or `"track"`, or Track keys with `shows: "gifts"`.
- Do not list variable, grouped or external products in `gifts`.
- Do not space the parts with Bricks' `_rowGap`; use `gap`.
- Do not give the instances on one page different **Goal reached** words.
- Do not set `pill*` without `choicesAs: "pills"`, or `radioTick*` without `radioLook: "custom"`.
