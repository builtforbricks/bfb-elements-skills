---
name: bfbe-delivery-estimate
description: "Use when showing a delivery date, a cut-off countdown, a postcode check or pickup hours with `bfbe-delivery-estimate`, on a product, cart or any page, or with those parts placed apart as separate instances."
---

# BFB Delivery Estimate (`bfbe-delivery-estimate`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-delivery-estimate.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/delivery-estimate/

## What it is
A delivery estimate for the visitor, such as Order within 2 h 14 min for delivery Tuesday 27 to Wednesday 28 October, and a postcode check that answers with WooCommerce's own rates for another address. The dates are worked out on your server from the Delivery settings on the Shop page and WooCommerce's shipping zones, for the visitor's zone, on the site's clock, and a cached page is put right after load. The countdown is a real clock to the cut-off. It needs the Delivery switch on.

**Not for:** Not a carrier's tracking: the dates come from your own rules, so a carrier's own delay is not known here. For the day and time slot a shopper books at checkout, use the Delivery feature's Delivery date and time checkout field.

**Costs a page:** CSS 0.83 KB, JS 1.71 KB (gzipped), plus shop-live, loaded only on pages that use it.

**Nestable:** no · **In a query loop:** no · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** no

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Estimate (`bfbeEstimate`)
- `show` (select) **Show**: options: `both` Estimate and postcode check (default), `estimate` Estimate only, `check` Postcode check only, `pickup` Pickup hours only. Estimate and postcode check (the default), Estimate only, Postcode check only, or Pickup hours only. Add a second element set to another part to place each part where you want it.
- `withinText` (text) **Before the cut-off**: placeholder Order within {time} for delivery {date}; only when `show` is not `check` or `pickup`. The sentence while today's cut-off is ahead, Order within {time} for delivery {date} unless set; {time}, {date}, {from} and {to} are filled in. Change it when your shop says dispatched rather than delivered.
- `afterText` (text) **After the cut-off**: placeholder Delivery {date}; only when `show` is not `check` or `pickup`. The sentence once today's orders are closed or on a day off, Delivery {date} unless set.
- `noneText` (text) **Without an estimate**: placeholder Nothing is shown; dynamic data accepted; only when `show` is not `check` or `pickup`. What shows when no transit rule covers the visitor; empty, nothing shows. It takes dynamic data.

### Postcode check (`bfbeCheck`)
The whole group shows only when `show` is not `estimate` or `pickup`.
- `checkTitle` (text) **Title**: placeholder Delivery to your address; dynamic data accepted; only when `show` is not `estimate` or `pickup`. Delivery to your address unless set; it names the form for screen readers too, and takes dynamic data.
- `checkFor` (select) **Check for**: options: `auto` This product, else the cart (default), `cart` The cart; only when `show` is not `estimate` or `pickup`. This product, else the cart (the default), or The cart, for a product page that should answer for the whole basket.
- `countryLabel` (text) **Country label**: placeholder Country; only when `show` is not `estimate` or `pickup`
- `postcodeLabel` (text) **Postcode label**: placeholder Postcode; only when `show` is not `estimate` or `pickup`
- `buttonText` (text) **Button text**: placeholder Check; only when `show` is not `estimate` or `pickup`
- `fieldsDirection` (select) **Direction**: options: `row` Across (default), `column` Down; only when `show` is not `estimate` or `pickup`
Styling, in the schema file: `checkTitleTypography`, `fieldLabelTypography`, `fieldsGap`, `fieldTypography`, `fieldBackground`, `fieldBorder`, `fieldPadding`, `fieldFocusBorder`, `buttonTypography`, `buttonBackground`, `buttonColor`, `buttonBorder`, `buttonPadding`, `buttonHoverBackground`, `buttonHoverColor`, `rateGap`, `ratePadding`, `rateNameTypography`, `rateCostTypography`, `rateWhenTypography`, `rateLineColor`, `noneTypography`, `errorTypography`.

### Pickup (`bfbePickup`)
- `pickup` (select) **Pickup hours**: options: `hours` From a BFB Business Hours element, `words` In words. None (the default), From a BFB Business Hours element, or In words; shown while WooCommerce offers the visitor Local pickup.
- `pickupFrom` (select) **Business Hours in**: placeholder This page; only when `pickup` is `hours`. A template holding a BFB Business Hours element; empty, the page it is on. Days with the same hours are joined, such as Monday to Friday 09:00 to 18:00.
- `pickupWords` (textarea) **Pickup hours in words**: placeholder Monday to Friday, 9:00 to 17:00; dynamic data accepted; only when `pickup` is `words`
- `pickupTitle` (text) **Pickup title**: placeholder Pickup hours; dynamic data accepted; only when `pickup` is set

### Look (`bfbeLook`)
- `lines` (checkbox) **Lines between parts**
Styling, in the schema file: `gap`, `lineColor`, `lineWidth`, `estimateTypography`, `timeTypography`, `dateTypography`, `pickupTitleTypography`, `pickupDaysTypography`, `pickupHoursTypography`, `pickupWordsTypography`.

### Country list (`bfbeCountryList`)
The whole group shows only when `show` is not `estimate` or `pickup`.
- `countryListLook` (select) **Open list**: options: `native` As the browser draws it (default), `custom` Styled with the controls below. The country select's open list As the browser draws it (the default) or Styled with the controls below; phones keep their own list either way.
Styling, in the schema file: `countryListChevron`, `countryListPanelBg`, `countryListPanelBorder`, `countryListPanelShadow`, `countryListPanelPadding`, `countryListOptTypography`, `countryListOptPadding`, `countryListOptHover`, `countryListHoverText`, `countryListOptOnBg`, `countryListOptOnColor`, `countryListTick`.

## What it guarantees for accessibility (do not undo)
- The estimate is a paragraph whose ticking words are aria-live off; one polite sentence says the new date when the cut-off passes.
- The check is a form named by its title, with a label for each field, autocomplete country and postal-code, and a real submit button.
- Its answer is a list named for the destination, said in one sentence, such as 2 delivery options for Romania 030031.
- The pickup hours are a group named by its title, written as a definition list.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<div id="brxe-{id}" class="brxe-bfbe-delivery-estimate bfbe-delivery bfbe-delivery--lines" data-bfbe-shop-need="delivery"
     data-bfbe-delivery='{"s":{"none":false,"now":…,"until":…,"range":"…","fromText":"…","toText":"…","pickup":true},"w":{…}}'>
  <p class="bfbe-delivery__estimate"><span class="bfbe-delivery__words" aria-live="off">Order within
    <span class="bfbe-delivery__left">2 h 14 min</span> for delivery <span class="bfbe-delivery__date">Tuesday 27 to Wednesday 28 October</span></span></p>
  <div class="bfbe-delivery__pickup" data-bfbe-dl-pickup role="group" aria-labelledby="bfbe-{uid}-dl-pickup" hidden>
    <p class="bfbe-delivery__pickup-title" id="bfbe-{uid}-dl-pickup">Pickup hours</p>
    <dl class="bfbe-delivery__hours"><div class="bfbe-delivery__hours-row"><dt>Monday to Friday</dt><dd>09:00 to 18:00</dd></div>…</dl>
    <!-- or, with pickup: "words": <p class="bfbe-delivery__pickup-words"> -->
  </div>
  <form class="bfbe-delivery__check" id="bfbe-{uid}-dl" method="post" action="#bfbe-{uid}-dl" aria-labelledby="bfbe-{uid}-dl-title">
    <p class="bfbe-delivery__check-title" id="bfbe-{uid}-dl-title">Delivery to your address</p>
    <div class="bfbe-delivery__fields bfbe-delivery__fields--row">
      <span class="bfbe-delivery__field"><label>Country</label><select name="bfbe_dl_country" autocomplete="country">…</select></span>
      <span class="bfbe-delivery__field"><label>Postcode</label><input name="bfbe_dl_postcode" autocomplete="postal-code"></span>
      <button type="submit" class="bfbe-delivery__button">Check</button></div>
    <input type="hidden" name="bfbe_dl_check" value="{element id}"><input type="hidden" name="bfbe_dl_product" value="{id or 0}">
  </form>
  <div class="bfbe-delivery__answer" id="bfbe-{uid}-dl-answer"><!-- ul.bfbe-delivery__rates > li.bfbe-delivery__rate, or p.bfbe-delivery__none --></div>
</div>
```

- **Show** `show` picks the parts: `both` the sentence and the check, `estimate` the sentence, `check` the form and its answer, `pickup` the pickup hours alone. The pickup block prints with any of them while **Pickup hours** `pickup` is set.
- The root is a grid; `bfbe-delivery--lines` (**Lines between parts** `lines`) draws a line over each shown part after the first. `data-bfbe-delivery` carries the server's state and words; the script repaints the sentence from it every second and from each live answer.
- States: `hidden` on the estimate when nothing is promised and **Without an estimate** is empty, and on the pickup block while Local pickup is not offered; `aria-busy="true"` on the answer and `disabled` on the button while checking. An answer holds `li.bfbe-delivery__rate` with `__rate-name`, `__rate-cost`, `__rate-when` (`--pickup` for Local pickup), else `p.bfbe-delivery__none` or `p.bfbe-delivery__error`.
- Where controls write: `gap`, `lineColor` and `lineWidth` set `--bfbe-delivery-gap`, `--bfbe-delivery-line` and `--bfbe-delivery-line-width` on the root. `estimateTypography` writes to the sentence, `timeTypography` to `.bfbe-delivery__left`, `dateTypography` to `.bfbe-delivery__date`, `pickup*Typography` to the pickup title, `dt`, `dd` and words. `button*` write to `.bfbe-delivery__button`, `field*` to the select and input, `fieldsGap` to `.bfbe-delivery__fields`, `rateGap` to `.bfbe-delivery__rates`, `rate*` to the rates.

## Wiring to other elements

- **Every instance follows one live answer.** Each root carries `data-bfbe-shop-need="delivery"`; the shop's shared script asks the server once after load and every Delivery Estimate on the page paints that answer. Several instances cost no extra request.
- **Two instances, placed apart.** Set one to `show: "estimate"` beside the add to cart button and a second to `show: "pickup"` (or `check`) in a sidebar or a Bricks container of its own. Leave `pickup` unset on every instance but the one meant to show the hours.
- **BFB Business Hours** feeds `pickup: "hours"`: the first `bfbe-business-hours` with days in this page (its header and footer included), or in the template chosen in **Business Hours in** `pickupFrom`. Consecutive days with the same hours are joined.
- **The settings live on the Shop page**: BFB Elements, Shop, Delivery (processing days, cut-offs, holidays, transit days per zone and method), with the `shop-delivery` feature on (skill `bfbe-shop`).
- **The same dates as tags**: `{bfbe_delivery_date}`, `{bfbe_delivery_range}`, `{bfbe_delivery_cutoff}`, each live on cached pages, in any Bricks text (skill `bfbe-shop-tags-and-conditions`).

## Verified patterns

**The estimate and the pickup hours as two elements** (fixture page `fixture-shop-p6`, `.dl-apart`, with the page's Business Hours). The estimate-only instance has no `pickup`; the pickup-only one reads the Business Hours below it and shows only while Local pickup is offered. The hours are the fixture's own: set the shop's.

```json
{
  "name": "block",
  "settings": { "_rowGap": "24px" },
  "children": [
    { "name": "block", "settings": { "_direction": "row", "_columnGap": "24px", "_alignItems": "flex-start", "_cssClasses": "dl-apart" }, "children": [
      { "name": "bfbe-delivery-estimate", "settings": { "show": "estimate", "_cssClasses": "dl-est-only", "_width": "50%" } },
      { "name": "bfbe-delivery-estimate", "settings": { "show": "pickup", "pickup": "hours", "pickupTitle": "Pick it up here", "_cssClasses": "dl-pickup", "_width": "50%" } }
    ] },
    { "name": "bfbe-business-hours", "settings": { "days": [
      { "day": "mon", "open": "09:00", "close": "18:00" }, { "day": "tue", "open": "09:00", "close": "18:00" },
      { "day": "wed", "open": "09:00", "close": "18:00" }, { "day": "thu", "open": "09:00", "close": "18:00" },
      { "day": "fri", "open": "09:00", "close": "18:00" }, { "day": "sat", "open": "10:00", "close": "14:00" },
      { "day": "sun", "closed": true }
    ], "_cssClasses": "dl-hours" } }
  ]
}
```

**The check for the whole cart, fields down** (fixture page `fixture-shop-p6-cart`, `.dl-cart`). **Check for** `checkFor: "cart"` prices the basket; **Direction** `fieldsDirection: "column"` stacks the fields over the button for a narrow cart column.

```json
{ "name": "bfbe-delivery-estimate", "settings": { "checkFor": "cart", "checkTitle": "Delivery for this cart", "fieldsDirection": "column", "fieldsGap": "20px", "_cssClasses": "dl-cart" } }
```

**Own sentences and pickup hours in words** (fixture page `fixture-shop-p6`, `.dl-words`). `withinText` and `afterText` use `{time}`, `{from}` and `{to}`; `pickup: "words"` prints `pickupWords` for a shop whose pickup hours are not its opening hours.

```json
{ "name": "bfbe-delivery-estimate", "settings": { "show": "estimate", "withinText": "Order in the next {time} and it arrives {from} at the earliest", "afterText": "It arrives between {from} and {to}", "pickup": "words", "pickupWords": "Weekdays 9:00 to 18:00 at Strada Lipscani 12", "pickupTitle": "Collect it yourself", "_cssClasses": "dl-words" } }
```

## Gotchas

- **Pickup prints with every Show.** `pickup` set on an estimate or check instance adds the hours there too, so a split page shows them twice. <!-- src: plugins/bfb-elements-pro/elements/delivery-estimate.php:766 -->
- **Pickup only, with no source, is an empty box.** `show: "pickup"` without `pickup` prints an empty root on the site; the canvas says to choose a source. <!-- src: plugins/bfb-elements-pro/elements/delivery-estimate.php:763 -->
- **Pickup hides unless Local pickup is offered.** The block is `hidden` while WooCommerce offers this visitor no Local pickup, and the live answer toggles it; the canvas always shows it. <!-- src: plugins/bfb-elements-pro/elements/delivery-estimate.php:777 ; src/elements/delivery-estimate/delivery-estimate.js:52 -->
- **No transit rule, no date.** With no rule for the visitor's zone and method, the sentence is **Without an estimate** `noneText`, or hidden when that is empty; the canvas draws a sample marked as one. <!-- src: plugins/bfb-elements-pro/elements/delivery-estimate.php:724 ; plugins/bfb-elements-pro/elements/delivery-estimate.php:758 -->
- **The estimate is the cart's, not the page's product.** The sentence counts from the rates for the visitor's cart and address, also on a product page; only the check prices the product, with `checkFor` unset. <!-- src: docs/elements/delivery-estimate.md "Limits" ; plugins/bfb-elements-pro/elements/delivery-estimate.php:796 -->
- **A product that ships nothing gets nothing.** On a download or a service the element prints nothing on the site. <!-- src: plugins/bfb-elements-pro/elements/delivery-estimate.php:716 -->
- **The sentences take four words, no dynamic data.** `withinText` and `afterText` fill `{time}`, `{date}`, `{from}` and `{to}` only; `{time}` has a value before the cut-off alone. `noneText` and `pickupWords` take dynamic data. <!-- src: plugins/bfb-elements-pro/elements/delivery-estimate.php:608 ; plugins/bfb-elements-pro/elements/delivery-estimate.php:732 ; src/elements/delivery-estimate/delivery-estimate.js:60 -->
- **The clock is the server's.** The countdown counts to the cut-off with the live answer's own time, asks again when it reaches zero (five tries at most) and says the new date once; the ticking words are `aria-live="off"`. <!-- src: src/elements/delivery-estimate/delivery-estimate.js:107 ; src/elements/delivery-estimate/delivery-estimate.js:119 ; plugins/bfb-elements-pro/elements/delivery-estimate.php:758 -->
- **A guest's check starts from the shop's country.** A cached page carries no visitor's postcode; the script fills the visitor's own after load, never over what they typed. The country list is WooCommerce's shipping countries. <!-- src: plugins/bfb-elements-pro/elements/delivery-estimate.php:801 ; src/elements/delivery-estimate/delivery-estimate.js:96 -->
- **Business Hours is read as saved.** `pickup: "hours"` reads the first Business Hours with days stored in the page, its header or footer, or the `pickupFrom` template; none found prints no pickup block. <!-- src: plugins/bfb-elements-pro/elements/delivery-estimate.php:617 -->
- **Line controls need the switch.** `lineColor` and `lineWidth` are offered only with `lines` on. <!-- src: plugins/bfb-elements-pro/elements/delivery-estimate.php:231 -->

## Never do

- Do not set `pickup` on more than one instance of a page split by `show`.
- Do not set `show: "pickup"` without `pickup`.
- Do not put dynamic tags in `withinText` or `afterText`; use `{time}`, `{date}`, `{from}` and `{to}`.
- Do not present the sentence as the product's delivery; it is the cart's.
- Do not set `pickup: "hours"` on a page or template with no BFB Business Hours, unless `pickupFrom` names one.
- Do not set `lineColor` or `lineWidth` without `lines`.
