---
name: bfbe-order-status
description: "Use for an order lookup with BFB Order Status (`bfbe-order-status`): a form for the order number and email, answered with the order's steps, facts, history and items, together or as two instances (Show: form only, answer only) placed apart. Read before writing its settings."
---

# BFB Order Status (`bfbe-order-status`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-order-status.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/order-status/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 1.07 KB, JS none (gzipped), no dependencies, loaded only on pages that use it.

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Lookup form (`bfbeForm`)
- `shows` (select) **Show**: options: `both` Form and answer (default), `form` Form only, `answer` Answer only. Place the answer elsewhere with a second element.
- `intro` (textarea) **Intro**: dynamic data accepted; only when `shows` is not `answer`
- `numberLabel` (text) **Order number label**: placeholder Order number; only when `shows` is not `answer`
- `emailLabel` (text) **Email label**: placeholder Email address used for the order; only when `shows` is not `answer`
- `buttonText` (text) **Button**: placeholder Check my order; only when `shows` is not `answer`
- `buttonStyle` (select) **Style**: options: `primary` Primary (default), `secondary` Secondary, `light` Light, `dark` Dark, `muted` Muted, `info` Info, `success` Success, `warning` Warning, `danger` Danger; only when `shows` is not `answer`
Styling, in the schema file: `formGap`, `introTypography`, `labelTypography`, `fieldTypography`, `fieldBackground`, `fieldBorder`, `fieldPadding`, `focusBorderColor`, `buttonTypography`, `buttonBackground`, `buttonBorder`, `buttonPadding`, `buttonHoverBackground`, `buttonHoverColor`, `buttonHoverBorder`, `refusedBorder`, `errorTypography`.

### Timeline (`bfbeTimeline`)
The whole group shows only when `shows` is not `form`.
- `showHistory` (select) **History**: options: `show` Show (default), `hide` Hide
- `showItems` (select) **Items**: options: `show` Show (default), `hide` Hide
- `showTracking` (select) **Tracking numbers**: options: `show` Show (default), `hide` Hide
- `stepDirection` (select) **Direction**: options: `row` Across (default), `column` Down
Styling, in the schema file: `stepTypography`, `stepColor`, `stepDoneColor`, `stepCurrentColor`, `stepSize`, `stepLineColor`, `stepLineWidth`.

### Answer (`bfbeAnswer`)
The whole group shows only when `shows` is not `form`.
- `titleText` (text) **Title**: placeholder Order #{number}. {number} is filled in.
- `titleTag` (select) **Title tag**: options: `h2` H2, `h3` H3 (default), `h4` H4, `h5` H5, `h6` H6, `p` p
- `placedLabel` (text) **Date label**: placeholder Placed
- `statusLabel` (text) **Status label**: placeholder Status
- `shippingLabel` (text) **Shipping label**: placeholder Shipping
- `trackingLabel` (text) **Tracking label**: placeholder Tracking; only when `showTracking` is not `hide`
- `historyHeading` (text) **History heading**: placeholder History; only when `showHistory` is not `hide`
- `itemsHeading` (text) **Items heading**: placeholder Items; only when `showItems` is not `hide`
- `headingTag` (select) **Heading tag**: options: `h2` H2, `h3` H3, `h4` H4 (default), `h5` H5, `h6` H6, `p` p
Styling, in the schema file: `boxBackground`, `boxBorder`, `boxShadow`, `boxPadding`, `answerTitleTypography`, `headingTypography`, `historyTypography`, `factLabelTypography`, `factValueTypography`, `dateColor`, `trackingColor`, `trackingHoverColor`, `itemNameTypography`, `itemQtyTypography`, `itemDividerColor`, `itemDividerWidth`.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<div id="brxe-{id}" class="brxe-bfbe-order-status bfbe-os bfbe-os--row">
  <p class="bfbe-os__intro">…</p>
  <form class="bfbe-os__form" method="post" action="" novalidate>
    <p class="bfbe-os__row"><label class="bfbe-os__label" for="{uid}-n">Order number</label>
      <input class="bfbe-os__input" type="text" inputmode="numeric" autocomplete="off" required id="{uid}-n" name="bfbe_os_number"></p>
    <p class="bfbe-os__row"><label class="bfbe-os__label" for="{uid}-e">Email address used for the order</label>
      <input class="bfbe-os__input" type="email" autocomplete="email" required id="{uid}-e" name="bfbe_os_email"></p>
    <p class="bfbe-os__row bfbe-os__row--submit"><button type="submit" class="bfbe-os__button bricks-button bricks-background-primary">Check my order</button></p>
  </form>
  <div class="bfbe-os__answer bfbe-os__answer--refused" role="alert"><p class="bfbe-os__error">We could not find an order with that number and email.</p></div>
  <div class="bfbe-os__answer" aria-live="polite">
    <h3 class="bfbe-os__title">Order #1042</h3>
    <ol class="bfbe-os__steps" aria-label="Order progress">
      <li class="bfbe-os__step bfbe-os__step--done"><span class="bfbe-os__mark" aria-hidden="true"></span><span class="bfbe-os__word">Order placed</span></li>
      <li class="bfbe-os__step bfbe-os__step--current" aria-current="step">…Being prepared</li>
      <li class="bfbe-os__step bfbe-os__step--next">…Shipped</li>
    </ol>
    <dl class="bfbe-os__facts"><div class="bfbe-os__fact"><dt>Placed</dt><dd class="bfbe-os__date">…</dd></div>…
      <div class="bfbe-os__fact bfbe-os__fact--tracking"><dt>Tracking</dt><dd><a class="bfbe-os__tracking" href="…">…</a></dd></div></dl>
    <h4 class="bfbe-os__heading">History</h4>
    <ol class="bfbe-os__history"><li class="bfbe-os__event"><time class="bfbe-os__date" datetime="…">…</time> <span class="bfbe-os__text">…</span></li></ol>
    <h4 class="bfbe-os__heading">Items</h4>
    <ul class="bfbe-os__items"><li class="bfbe-os__item"><span class="bfbe-os__item-name">…</span> <span class="bfbe-os__item-qty">× 2</span></li></ul>
  </div>
</div>
```

- **Show** (`shows`) decides the parts: `both` prints the form, any refusal and the answer; `form` the intro, form and refusal; `answer` the answer box alone. `bfbe-os--row` or `bfbe-os--column` follows **Direction** (`stepDirection`).
- The form is a plain POST to the page it is on, with no nonce and no script. A signed-in visitor gets no email row. The refusal box follows the form; the answer box carries `aria-live="polite"`.
- Step states are `bfbe-os__step--done`, `--current` (with `aria-current="step"`) and `--next`. **Title tag** `titleTag` (H3) and **Heading tag** `headingTag` (H4) set the title and the History and Items headings.
- Where controls write: the step colours and sizes are custom properties on the root (`--bfbe-os-mark`, `--bfbe-os-done`, `--bfbe-os-current`, `--bfbe-os-size`, `--bfbe-os-line`, `--bfbe-os-line-w`); `box*` write `.bfbe-os__answer`, which the refusal box also carries; `refusedBorder` writes `.bfbe-os__answer--refused`; `field*` write `.bfbe-os__input`; `button*` write `.bfbe-os__button`.

## Wiring to other elements

- **Two instances, placed apart.** One with `shows: "form"` where the visitor types; one with `shows: "answer"` in any Bricks container: a column beside it, a section above it. The lookup is answered before the page renders, so the answer element may come first in the page.
- **Or build the answer from Bricks' own elements.** After a lookup the order tags (`{bfbe_order_number}`, `{bfbe_order_status}`, `{bfbe_order_total}` and the rest) and the query loop **BFB Shop order items** (`bfbeShopOrderItems`) read the looked-up order, as they read the order on a thank-you page. Give their block the condition **Order found** (`bfbe_shop_order_found`, value `yes`) so it prints only once there is an order. The full tree is in `bfbe-shop-tags-and-conditions`.
- **Other order parts follow too.** A BFB Withdrawal Button on the same page carries the looked-up order's number after a lookup (`bfbe-withdrawal-button`).
- The instances meet through the request, not through ids or classes: any class you give in `_cssClasses` is for your own CSS.

## Verified patterns

**The lookup with the answer under it.** From the 2.4 site's demo help page ("Help, delivery and returns", `help`, the "Where is my order?" card). Form and answer in one element, the steps in the brand's purple, the answer box tinted and borderless. Trimmed: the demo's colour variables, kept as hex.

```json
{
  "name": "bfbe-order-status",
  "settings": {
    "intro": "Your order number is in the email we sent. Signed in, the number alone is enough.",
    "buttonText": "Show my order",
    "buttonStyle": "primary",
    "fieldBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "12", "right": "12", "bottom": "12", "left": "12" } },
    "stepColor": { "hex": "#e9ecf1" },
    "stepDoneColor": { "hex": "#6e44ff" },
    "stepCurrentColor": { "hex": "#6e44ff" },
    "dateColor": { "hex": "#667085" },
    "boxBackground": { "color": { "hex": "#f7f8fa" } },
    "boxPadding": { "top": "20", "right": "20", "bottom": "20", "left": "20" },
    "_cssClasses": "track-order"
  }
}
```

**The answer in one column, the form in the other.** From the order fixture (`fixture-shop-p8`, "Order status split"). The Answer only element comes first and carries the answer's words and look; the Form only element carries the form's. History hidden, an H2 title with `{number}` filled in.

```json
{
  "name": "block",
  "settings": { "_direction": "row", "_columnGap": "24px", "_alignItems": "flex-start", "_cssClasses": "os-split" },
  "children": [
    { "name": "bfbe-order-status", "settings": { "shows": "answer", "titleText": "Your order {number}", "titleTag": "h2", "headingTag": "h3", "placedLabel": "Ordered on", "itemsHeading": "What you bought", "showHistory": "hide", "stepLineWidth": "4px", "_cssClasses": "os-away" } },
    { "name": "bfbe-order-status", "settings": { "shows": "form", "buttonText": "Look it up", "_cssClasses": "os-form" } }
  ]
}
```

## Gotchas

- **An Answer only element prints nothing until a lookup.** On a plain visit, or after a refusal, the page gets no markup from it; the refusal shows under the form, where the visitor typed. <!-- src: plugins/bfb-elements-pro/elements/order-status.php:610-615 --> <!-- src: dev/shop/p8-probe.mjs:139 ; dev/shop/p8-probe.mjs:148 -->
- **The canvas shows the newest order.** In the builder an element that shows the answer draws the store's latest order so it can be styled, and its button does not submit; the page shows only an order that was looked up. <!-- src: plugins/bfb-elements-pro/elements/order-status.php:605-609 ; plugins/bfb-elements-pro/elements/order-status.php:657 -->
- **Show hides whole groups.** With `shows: "form"` the Timeline and Answer groups are gone; with `shows: "answer"` the labels, intro, button and refused controls are. Style each instance for the part it prints. <!-- src: plugins/bfb-elements-pro/elements/order-status.php:50-51 ; plugins/bfb-elements-pro/elements/order-status.php:561-590 -->
- **The box controls reach the refusal too.** The refusal is `.bfbe-os__answer.bfbe-os__answer--refused`, so on a `both` element `boxBackground`, `boxBorder` and `boxPadding` style it as well; `refusedBorder` wins for its border. <!-- src: plugins/bfb-elements-pro/elements/order-status.php:661 ; plugins/bfb-elements-pro/elements/order-status.php:546-551 -->
- **Five tries per ten minutes.** Counted per address and per visitor; the sixth is refused as "Too many tries" even with the right pair. Testing a build repeatedly from one browser hits it. <!-- src: plugins/bfb-elements-pro/includes/shop/class-order-status.php:26-28 ; plugins/bfb-elements-pro/includes/shop/class-order-status.php:56-61 --> <!-- src: dev/shop/p8-probe.mjs:117-119 -->
- **Signed in, the number alone.** A signed-in customer sees no email field and gets answers only for orders they may view; `emailLabel` is never shown to them. <!-- src: plugins/bfb-elements-pro/elements/order-status.php:653-656 ; plugins/bfb-elements-pro/includes/shop/class-order-status.php:89-91 -->
- **The title is plain words.** **Title** `titleText` fills in `{number}` and nothing else, never dynamic data; **Intro** `intro` is the one text that takes dynamic data. <!-- src: plugins/bfb-elements-pro/elements/order-status.php:673-675 ; plugins/bfb-elements-pro/elements/order-status.php:98-104 -->
- **Direction is one value for every width.** `stepDirection` is a class on the root, not a breakpoint control; across, the step words shrink below 600px. Choose `column` for a narrow place. <!-- src: plugins/bfb-elements-pro/elements/order-status.php:272-280 ; plugins/bfb-elements-pro/elements/order-status.php:618 --> <!-- src: src/elements/order-status/order-status.css:44 -->
- **Shipped and tracking need WooCommerce's data.** The Shipped step appears only for orders that ship; tracking numbers come from WooCommerce's fulfillments (when that feature is on) or the `_tracking_number` order meta, never other plugins' keys. <!-- src: docs/elements/order-status.md "Timeline" ; docs/elements/order-status.md "Limits" -->
- **The digits pad goes with renumbering.** Phones get a numeric keyboard only while no plugin filters `woocommerce_order_number`. <!-- src: plugins/bfb-elements-pro/elements/order-status.php:650-652 -->

## Never do

- Do not leave an Answer only element on a page without a form that posts the lookup.
- Do not put dynamic data in `titleText`; use `{number}` or build the title from order tags.
- Do not set Timeline or Answer keys on a `shows: "form"` element, or form keys on a `shows: "answer"` one.
- Do not style the refusal with the box controls when the answer box should look different; use `refusedBorder` and `errorTypography`.
- Do not test the lookup more than five times in ten minutes from one browser and read the refusal as a fault.
- Do not point the two instances at each other by `_cssId`; they meet through the request.
