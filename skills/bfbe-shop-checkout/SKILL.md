---
name: bfbe-shop-checkout
description: "Use for the shop's settings on Bricks' Checkout customer details, Order review and Thank you (and the 2.4 Checkout v2 and its form fields): checkout fields of your own with their Shop settings rows and the {bfbe_order_field:key} tag, date pickers, delivery days and time slots, floating labels, and the table, fields and payment look (BFB Shop checkout, `shop-checkout`). Read before writing these settings."
---

# BFB Shop checkout (`shop-checkout`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 2.0.0 or later, and BFB Elements Pro 2.0.0 or later for the groups marked Pro, WooCommerce active, the feature switches on (WordPress menu BFB Elements, Elements): `shop-checkout-fields`, `shop-delivery`. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/shop-checkout.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/shop/ (the Shop), and a page for each feature this skill spans: https://builtforbricks.com/bfb-elements/docs/shop-checkout-fields/, https://builtforbricks.com/bfb-elements/docs/shop-delivery/

## What it is
The website documents this by feature; each line is the approved summary from that feature's page.
- `shop-checkout-fields` (https://builtforbricks.com/bfb-elements/docs/shop-checkout-fields/): A Pro feature that adds fields of your own to the WooCommerce checkout: text, multi-line text, a choice list, a checkbox or a date, in the billing, shipping or order notes section or after the order review. They join WooCommerce's own field list, so each answer is saved on the order and shows on the admin order screen, in the emails, on the thank-you page and in the account. A field can show for some countries, shipping methods or cart contents, decided in the browser as the shopper changes them and again on your server when the order is placed.
- `shop-delivery` (https://builtforbricks.com/bfb-elements/docs/shop-delivery/): The delivery rules every delivery date in the shop counts from: processing days, working days with their cut-off times, holidays, and transit times per shipping zone and method, in your site's time zone. BFB Delivery Estimate, the delivery tags and the checkout read them. It also adds a Delivery date and time type to the checkout fields, where a shopper chooses a day and a time slot that the server judges again when the order is placed.

## Where it lives
A feature, not an element: its groups are added to Bricks' own elements, on the Content tab after Bricks' own groups. By element:
- Checkout customer details (`woocommerce-checkout-customer-details`): BFB Form fields (`bfbeShopFields`), BFB Date fields (`bfbeShopCfDate`), BFB Floating labels (`bfbeShopFloat`), BFB Delivery day and time (`bfbeShopSlot`), BFB Delivery calendar (`bfbeShopSlotCal`).
- Checkout order review (`woocommerce-checkout-order-review`): BFB Table (`bfbeShopTable`), BFB Form fields (`bfbeShopFields`), BFB Payment (`bfbeShopPayment`), BFB Date fields (`bfbeShopCfDate`), BFB Your checkout fields (`bfbeShopCfReview`), BFB Floating labels (`bfbeShopFloat`), BFB Delivery day and time (`bfbeShopSlot`), BFB Delivery calendar (`bfbeShopSlotCal`).
- Checkout thank you (`woocommerce-checkout-thankyou`): BFB Table (`bfbeShopTable`).
- `woocommerce-checkout-v2`: BFB Date fields (`bfbeShopCfDate`), BFB Floating labels (`bfbeShopFloat`), BFB Delivery day and time (`bfbeShopSlot`), BFB Delivery calendar (`bfbeShopSlotCal`). Not registered on the export site (Bricks 2.3.10): a Bricks 2.4 element. The controls are the ones the pack adds when Bricks registers it.
- `woocommerce-form-field`: BFB Date fields (`bfbeShopCfDate`), BFB Delivery day and time (`bfbeShopSlot`), BFB Delivery calendar (`bfbeShopSlotCal`). Not registered on the export site (Bricks 2.3.10): a Bricks 2.4 element. The controls are the ones the pack adds when Bricks registers it.

## Settings that decide the build

### Checkout customer details (`woocommerce-checkout-customer-details`)

#### BFB Form fields (`bfbeShopFields`)
Free.
Styling only, every key in the schema file: `bfbeShopFieldsTitleTypography`, `bfbeShopFieldsTitleMargin`, `bfbeShopFieldsRowGap`, `bfbeShopFieldsRowSpacing`, `bfbeShopFieldsSelectBorder`, `bfbeShopFieldsSelectHeight`, `bfbeShopFieldsSelectPadding`.

#### BFB Date fields (`bfbeShopCfDate`)
Pro, switch `shop-checkout-fields`.
- `bfbeShopCfDatePicker` (select) **Date picker**: options: `native` As the browser draws it (default), `custom` Styled with the controls. Your checkout fields of the Date type.
Styling, in the schema file: `bfbeShopCfDateCalWidth`, `bfbeShopCfDateCalBackground`, `bfbeShopCfDateCalBorder`, `bfbeShopCfDateCalShadow`, `bfbeShopCfDateCalPadding`, `bfbeShopCfDateCalOffset`, `bfbeShopCfDateCalHeadSpace`, `bfbeShopCfDateCalWeekSpace`, `bfbeShopCfDateCalDayGap`, `bfbeShopCfDateCalHeadLine`, `bfbeShopCfDateCalHeadLineColor`, `bfbeShopCfDateCalWeekLine`, `bfbeShopCfDateCalWeekLineColor`, `bfbeShopCfDateCalMonthTypography`, `bfbeShopCfDateCalMonthPadding`, `bfbeShopCfDateCalYearPadding`, `bfbeShopCfDateCalHeadHoverBg`, `bfbeShopCfDateCalYearArrow`, `bfbeShopCfDateCalYearArrowHover`, `bfbeShopCfDateCalArrowSize`, `bfbeShopCfDateCalArrowPadding`, `bfbeShopCfDateCalArrowColor`, `bfbeShopCfDateCalArrowHover`, `bfbeShopCfDateCalArrowBg`, `bfbeShopCfDateCalArrowHoverBg`, `bfbeShopCfDateCalArrowBorder`, `bfbeShopCfDateCalArrowHoverBorder`, `bfbeShopCfDateCalWeekdayTypography`, `bfbeShopCfDateCalDayTypography`, `bfbeShopCfDateCalDaySize`, `bfbeShopCfDateCalDayPadding`, `bfbeShopCfDateCalDayBg`, `bfbeShopCfDateCalDayColor`, `bfbeShopCfDateCalDayBorder`, `bfbeShopCfDateCalDayHoverBg`, `bfbeShopCfDateCalDayHoverColor`, `bfbeShopCfDateCalDayHoverBorder`, `bfbeShopCfDateCalTodayBg`, `bfbeShopCfDateCalTodayColor`, `bfbeShopCfDateCalTodayBorder`, `bfbeShopCfDateCalTodayHoverBg`, `bfbeShopCfDateCalTodayHoverColor`, `bfbeShopCfDateCalTodayHoverBorder`, `bfbeShopCfDateCalSelected`, `bfbeShopCfDateCalSelectedColor`, `bfbeShopCfDateCalSelectedBorder`, `bfbeShopCfDateCalSelectedHoverBg`, `bfbeShopCfDateCalSelectedHoverColor`, `bfbeShopCfDateCalSelectedHoverBorder`, `bfbeShopCfDateCalShutBg`, `bfbeShopCfDateCalShut`, `bfbeShopCfDateCalShutBorder`, `bfbeShopCfDateCalShutHoverBg`, `bfbeShopCfDateCalShutHoverColor`, `bfbeShopCfDateCalShutHoverBorder`, `bfbeShopCfDateCalOtherBg`, `bfbeShopCfDateCalOther`, `bfbeShopCfDateCalOtherBorder`, `bfbeShopCfDateCalOtherHoverBg`, `bfbeShopCfDateCalOtherHoverColor`, `bfbeShopCfDateCalOtherHoverBorder`.

#### BFB Floating labels (`bfbeShopFloat`)
Pro, switch `shop-checkout-fields`.
- `bfbeShopLabelsAt` (select) **Labels**: options: `above` Above the field (default), `border` Floating, on the border
- `bfbeShopFloatPreview` (select) **In the builder**: options: `page` As the page shows them (default), `up` Risen, so you can style them; only when `bfbeShopLabelsAt` is `border`
Styling, in the schema file: `bfbeShopFloatHeight`, `bfbeShopFloatInset`, `bfbeShopFloatGap`, `bfbeShopFloatRestColor`, `bfbeShopFloatFocusColor`.

#### BFB Delivery day and time (`bfbeShopSlot`)
Pro, switch `shop-delivery`.
- `bfbeShopSlotPicker` (select) **Day and time pickers**: options: `native` As the browser draws them (default), `custom` Styled with the controls. Phones keep their own time list.
Styling, in the schema file: `bfbeShopSlotTimeTypography`, `bfbeShopSlotTimeBackground`, `bfbeShopSlotTimeBorder`, `bfbeShopSlotTimePadding`, `bfbeShopSlotTimeChevron`, `bfbeShopSlotTimePanelBg`, `bfbeShopSlotTimePanelBorder`, `bfbeShopSlotTimePanelShadow`, `bfbeShopSlotTimePanelPadding`, `bfbeShopSlotTimeOptTypography`, `bfbeShopSlotTimeOptPadding`, `bfbeShopSlotTimeOptHover`, `bfbeShopSlotTimeHoverText`, `bfbeShopSlotTimeOptOnBg`, `bfbeShopSlotTimeOptOnColor`, `bfbeShopSlotTimeTick`.

#### BFB Delivery calendar (`bfbeShopSlotCal`)
Pro, switch `shop-delivery`.
Styling only, every key in the schema file: `bfbeShopSlotCalWidth`, `bfbeShopSlotCalBackground`, `bfbeShopSlotCalBorder`, `bfbeShopSlotCalShadow`, `bfbeShopSlotCalPadding`, `bfbeShopSlotCalOffset`, `bfbeShopSlotCalHeadSpace`, `bfbeShopSlotCalWeekSpace`, `bfbeShopSlotCalDayGap`, `bfbeShopSlotCalHeadLine`, `bfbeShopSlotCalHeadLineColor`, `bfbeShopSlotCalWeekLine`, `bfbeShopSlotCalWeekLineColor`, `bfbeShopSlotCalMonthTypography`, `bfbeShopSlotCalMonthPadding`, `bfbeShopSlotCalYearPadding`, `bfbeShopSlotCalHeadHoverBg`, `bfbeShopSlotCalYearArrow`, `bfbeShopSlotCalYearArrowHover`, `bfbeShopSlotCalArrowSize`, `bfbeShopSlotCalArrowPadding`, `bfbeShopSlotCalArrowColor`, `bfbeShopSlotCalArrowHover`, `bfbeShopSlotCalArrowBg`, `bfbeShopSlotCalArrowHoverBg`, `bfbeShopSlotCalArrowBorder`, `bfbeShopSlotCalArrowHoverBorder`, `bfbeShopSlotCalWeekdayTypography`, `bfbeShopSlotCalDayTypography`, `bfbeShopSlotCalDaySize`, `bfbeShopSlotCalDayPadding`, `bfbeShopSlotCalDayBg`, `bfbeShopSlotCalDayColor`, `bfbeShopSlotCalDayBorder`, `bfbeShopSlotCalDayHoverBg`, `bfbeShopSlotCalDayHoverColor`, `bfbeShopSlotCalDayHoverBorder`, `bfbeShopSlotCalTodayBg`, `bfbeShopSlotCalTodayColor`, `bfbeShopSlotCalTodayBorder`, `bfbeShopSlotCalTodayHoverBg`, `bfbeShopSlotCalTodayHoverColor`, `bfbeShopSlotCalTodayHoverBorder`, `bfbeShopSlotCalSelected`, `bfbeShopSlotCalSelectedColor`, `bfbeShopSlotCalSelectedBorder`, `bfbeShopSlotCalSelectedHoverBg`, `bfbeShopSlotCalSelectedHoverColor`, `bfbeShopSlotCalSelectedHoverBorder`, `bfbeShopSlotCalShutBg`, `bfbeShopSlotCalShut`, `bfbeShopSlotCalShutBorder`, `bfbeShopSlotCalShutHoverBg`, `bfbeShopSlotCalShutHoverColor`, `bfbeShopSlotCalShutHoverBorder`, `bfbeShopSlotCalOtherBg`, `bfbeShopSlotCalOther`, `bfbeShopSlotCalOtherBorder`, `bfbeShopSlotCalOtherHoverBg`, `bfbeShopSlotCalOtherHoverColor`, `bfbeShopSlotCalOtherHoverBorder`.

### Checkout order review (`woocommerce-checkout-order-review`)

#### BFB Table (`bfbeShopTable`)
Free.
Styling only, every key in the schema file: `bfbeShopTableBorder`, `bfbeShopTableTitleMargin`, `bfbeShopTableAlign`, `bfbeShopTableLine`, `bfbeShopTableHeadBackground`, `bfbeShopTableHeadTypography`, `bfbeShopTableTotalTypography`, `bfbeShopTableLines`.

#### BFB Form fields (`bfbeShopFields`)
Free.
Styling only, every key in the schema file: `bfbeShopFieldsRowGap`, `bfbeShopFieldsRowSpacing`.

#### BFB Payment (`bfbeShopPayment`)
Free.
Styling only, every key in the schema file: `bfbeShopPaymentBorder`, `bfbeShopPaymentGap`, `bfbeShopPaymentListMargin`, `bfbeShopPaymentMethodBackground`, `bfbeShopPaymentMethodBorder`, `bfbeShopPaymentMethodPadding`, `bfbeShopPaymentMethodMargin`, `bfbeShopPaymentNameMargin`, `bfbeShopPaymentRadioColor`, `bfbeShopPaymentBoxMargin`, `bfbeShopPaymentBoxPadding`, `bfbeShopPaymentBoxBackground`, `bfbeShopPaymentBoxBorder`.

#### BFB Date fields (`bfbeShopCfDate`)
The same 73 controls as on `woocommerce-checkout-customer-details`.

#### BFB Your checkout fields (`bfbeShopCfReview`)
Pro, switch `shop-checkout-fields`.
Styling only, every key in the schema file: `bfbeShopCfReviewSpace`, `bfbeShopCfReviewGap`, `bfbeShopCfReviewPadding`, `bfbeShopCfReviewBackground`, `bfbeShopCfReviewBorder`.

#### BFB Floating labels (`bfbeShopFloat`)
The same 7 controls as on `woocommerce-checkout-customer-details`.

#### BFB Delivery day and time (`bfbeShopSlot`)
The same 20 controls as on `woocommerce-checkout-customer-details`.

#### BFB Delivery calendar (`bfbeShopSlotCal`)
The same 72 controls as on `woocommerce-checkout-customer-details`.

### Checkout thank you (`woocommerce-checkout-thankyou`)

#### BFB Table (`bfbeShopTable`)
Free.
Styling only, every key in the schema file: `bfbeShopTableAlign`, `bfbeShopTableLine`, `bfbeShopTableHeadBackground`, `bfbeShopTableHeadTypography`, `bfbeShopTableLinkTypography`.

### `woocommerce-checkout-v2`
Not registered on the export site (Bricks 2.3.10): a Bricks 2.4 element. The controls are the ones the pack adds when Bricks registers it.

#### BFB Date fields (`bfbeShopCfDate`)
The same 73 controls as on `woocommerce-checkout-customer-details`.

#### BFB Floating labels (`bfbeShopFloat`)
The same 7 controls as on `woocommerce-checkout-customer-details`.

#### BFB Delivery day and time (`bfbeShopSlot`)
The same 20 controls as on `woocommerce-checkout-customer-details`.

#### BFB Delivery calendar (`bfbeShopSlotCal`)
The same 72 controls as on `woocommerce-checkout-customer-details`.

### `woocommerce-form-field`
Not registered on the export site (Bricks 2.3.10): a Bricks 2.4 element. The controls are the ones the pack adds when Bricks registers it.

#### BFB Date fields (`bfbeShopCfDate`)
The same 73 controls as on `woocommerce-checkout-customer-details`.

#### BFB Delivery day and time (`bfbeShopSlot`)
The same 20 controls as on `woocommerce-checkout-customer-details`.

#### BFB Delivery calendar (`bfbeShopSlotCal`)
The same 72 controls as on `woocommerce-checkout-customer-details`.
<!-- bfbe:generated:end -->

## Rendered DOM

The feature adds no element. Bricks' checkout elements print WooCommerce's own markup; the feature adds fields to WooCommerce's field list, classes and attributes on its rows, a block or two of its own, and CSS at the host's id.

```html
<!-- A checkout field of yours, in its section (billing, shipping, the order notes area) -->
<p class="form-row form-row-wide bfbe-cf bfbe-cf--text bfbe-cf--hidden" id="bfbe_vat_number_field" data-priority="210">
  <label for="bfbe_vat_number">Company VAT number&nbsp;<span class="optional">(optional)</span></label>
  <span class="woocommerce-input-wrapper"><input type="text" class="input-text" name="bfbe_vat_number" id="bfbe_vat_number"
    data-bfbe-when='{"k":"country","v":"DE, AT","s":"billing"}'></span>
</p>
<!-- Fields set to After the order review, inside Bricks' Order review -->
<div class="bfbe-cf-review"><p class="form-row form-row-wide bfbe-cf bfbe-cf--select" id="bfbe_heard_field">…</p></div>
<!-- Delivery date and time (a field of the type the Delivery feature adds) -->
<p class="form-row form-row-wide bfbe-cf bfbe-cf--delivery bfbe-slot bfbe-slot--custom validate-required" id="bfbe_delivery_slot_field">
  <label for="bfbe_delivery_slot_date">Delivery day and time&nbsp;<span class="required" aria-hidden="true">*</span></label>
  <span class="woocommerce-input-wrapper bfbe-slot__fields bfbe-cal" data-bfbe-slot="{window, slots, words}">
    <input type="text" class="input-text bfbe-slot__date" name="bfbe_delivery_slot_date" min="…" max="…" placeholder="YYYY-MM-DD">
    <span class="bfbe-dd bfbe-slot__dd" data-bfbe-dd><span class="bfbe-dd__field">
      <select class="select bfbe-slot__time" name="bfbe_delivery_slot_slot" aria-label="Delivery time">…</select></span></span>
    <span class="bfbe-slot__hint" aria-live="polite"></span>
  </span>
</p>
<!-- Under WooCommerce's order table (thank-you page, the account's order page) -->
<section class="bfbe-cf-order woocommerce-customer-details"><h2 class="woocommerce-column__title">Your details</h2>
  <dl class="bfbe-cf-order__list"><div class="bfbe-cf-order__row bfbe-cf-order__row--gift_message"><dt>Gift message</dt><dd>…</dd></div></dl>
</section>
```

- **A field of yours** is WooCommerce's own row: input `name` and `id` are `bfbe_<key>`, the row `bfbe-cf bfbe-cf--<type>`. A field with a country or shipping rule carries `data-bfbe-when` on its input. When hidden it takes `bfbe-cf--hidden` (always `display: none`) and the `hidden` attribute, and its input is `disabled`.
- **A Date field** with **Date picker** `bfbeShopCfDatePicker: "custom"` becomes a text box holding `Y-m-d` with `data-bfbe-cal`: the row takes `bfbe-cf--cal`, the wrapper `bfbe-cal`. With the browser's picker it stays `type="date"`.
- **The delivery field** is two plain inputs, `<key>_date` and `<key>_slot`, joined on the server as `date|slot`. With **Day and time pickers** `bfbeShopSlotPicker: "custom"` the row takes `bfbe-slot--custom`, the date box becomes a calendar (flatpickr, Bricks' copy) and the time select gets the shop's list (`ul.bfbe-dd__panel`). Without it, a `type="date"` box and the plain select. Times full or not offered on the chosen day become `disabled` options, "(full)" added: the script marks them as a day is chosen, the server after a refused post.
- **Floating labels** (`bfbeShopLabelsAt: "border"`) mark the element's root `bfbe-pc--float`, each floating row `data-bfbe-float`, its label `.bfbe-fl__label` and its box `.bfbe-fl__input`; **In the builder** `up` adds `data-bfbe-fl-preview` in the canvas only.
- **Where the look groups write.** BFB Table: `table.shop_table` (border, align, line, header row, `.order-total`, `#order_review_heading` margin; **Rows as lines** `bfbeShopTableLines` turns rows into flex lines). BFB Form fields: `.form-row` and the select2 dropdowns; on Customer details also the shipping and notes `h3` titles. BFB Payment: `#payment`, each method `#payment ul.payment_methods > li`, its `.payment_box`. BFB Your checkout fields: `.bfbe-cf-review`. The calendars' controls are scoped to `.bfbe-cf--cal` and `.bfbe-slot`, so both calendars on one element keep their own look.

## Wiring to other elements

### Where each group sits

| Group | Customer details | Order review | Thank you | Checkout (v2), 2.4 | WooCommerce form field, 2.4 |
|---|---|---|---|---|---|
| BFB Form fields `bfbeShopFields` | yes | yes | | | |
| BFB Table `bfbeShopTable` | | yes | yes | | |
| BFB Payment `bfbeShopPayment` | | yes | | | |
| BFB Your checkout fields `bfbeShopCfReview` | | yes | | | |
| BFB Floating labels `bfbeShopFloat` | yes | yes | | yes | |
| BFB Date fields `bfbeShopCfDate` | yes | yes | | yes | yes |
| BFB Delivery day and time `bfbeShopSlot`, BFB Delivery calendar `bfbeShopSlotCal` | yes | yes | | yes | yes |

The 2.4 elements exist only with Bricks' experimental WooCommerce elements on; on 2.3 nothing is attached to them.

### Your checkout fields (Shop settings)

BFB Elements, Shop, **Cart & checkout** (`tab=checkout`), card **Checkout fields**, 30 rows at most, saved in the option `bfbe_shop_checkout_fields` (`fields` rows, `block` for the switch). Each row:

| Column | Key | What it takes |
|---|---|---|
| Label | `label` | The field's label, also its name in emails and on the order |
| Key | `key` | Letters, digits, underscores; made from the label when empty. Names the input `bfbe_<key>`, the order meta `_bfbe_field_<key>` and the tag `{bfbe_order_field:key}` |
| Type | `type` | `text` Text, `textarea` Multi-line text, `select` Choice list, `checkbox` Checkbox, `date` Date; `delivery` Delivery date and time with the Delivery switch on |
| Choices | `choices` | For a Choice list: `Small \| Medium \| Large` |
| Required | `required` | WooCommerce refuses the order without it ("Gift message is a required field.") |
| Where | `section` | `billing` Billing, `shipping` Shipping, `order` Order notes area, `review` After the order review |
| Show when | `when` | `""` Always, `country` Country is one of, `shipping` Shipping method contains, `cart` Cart has a product or category |
| Matching | `value` | `DE, AT`; a method id or part of one, `flat_rate` or `flat_rate:3`; a product or category id or slug |
| In emails | `emails` | In every customer email's order meta block; the admin's emails carry every saved field |
| In the account | `account` | In the "Your details" block under the order table |

The switch **Show the answers with the order details** (on unless turned off) prints that block on the thank-you page and the account's order page. Off, place `{bfbe_order_field:key}` yourself.

### How the fields reach the page

- **Classic checkout (Bricks 2.3 and 2.4).** Billing, Shipping and Order notes area fields print inside **Checkout customer details**, after WooCommerce's own fields of that section. After the order review fields print inside **Checkout order review**, after WooCommerce's review box, in `div.bfbe-cf-review`.
- **Checkout (v2).** Its address elements print one **WooCommerce form field** per field, so yours do not appear by themselves: add one more form field per field and pick it ("Billing: VAT number", "Order: Gift message"). The demo writes `fieldKey: "bfbe_vat_number"`. After the order review fields print where `woocommerce_checkout_after_order_review` fires; the demo places that hook with a Basic Text `{do_action:woocommerce_checkout_after_order_review}` on its Payment step.
- **The order's answers** come back as `{bfbe_order_field:key}` (with `@fallback:'words'`) wherever an order is in hand: the thank-you page, an account order page, an orders loop row (`bfbe-shop-tags-and-conditions`). The delivery choice also writes the promised date read by `{bfbe_order_delivery_date:format}`, `{bfbe_order_delivery_range}` and BFB Add to Calendar (`bfbe-add-to-calendar`).

### Delivery dates and time slots (Shop settings)

BFB Elements, Shop, **Delivery** (`tab=delivery`), card **Delivery dates and time slots**: **Bookable days ahead** (1 to 365, from today), then up to 20 slots, each **Slot name**, **From** and **To** (`09:00`), **Days** (`Mon-Fri`, `Sat`; empty is every day), **Orders per day** (0 is no limit) and **Shipping methods** (`flat_rate, local_pickup`; empty is every method). No slots: the shopper picks a day only. The first day offered is the earliest delivery estimate for the chosen method; holidays and days no slot covers are shut. The estimate's own settings are in `bfbe-delivery-estimate`.

### The pickers follow the element that prints the field

Customer details prints the billing, shipping and order notes fields; Order review prints those after the review. Each takes **its own** Date picker and Day and time pickers choice, so set the choice and the calendar look on both when both print such fields. On v2, a WooCommerce form field with no choice of its own takes the Checkout (v2)'s.

Nothing here needs a class or id; give `_cssClasses` for your own CSS. The hub for the rest of the shop is `bfbe-shop`.

## Verified patterns

The dev site (Bricks 2.3.10) has no checkout carrying these groups, and the 2.4 demo's checkout is Checkout (v2), which 2.3 does not register. These trees are built from the schema on the classic elements, with the look transposed from the 2.4 demo shop's "Fernhouse: checkout, in three steps" (`bfb-demo-checkout`); the demo's colour variables are kept as hex.

**Customer details with the shop's own pickers.** The date fields and the delivery day open the calendar of ours, the time list is the shop's list; the rows are spaced and the dropdowns sized. The calendars carry the brand's purple for the chosen day.

```json
{
  "name": "woocommerce-checkout-customer-details",
  "settings": {
    "_cssClasses": "checkout-details",
    "bfbeShopFieldsRowGap": "6px",
    "bfbeShopFieldsRowSpacing": "14px",
    "bfbeShopFieldsSelectBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "12", "right": "12", "bottom": "12", "left": "12" } },
    "bfbeShopFieldsSelectHeight": "46px",
    "bfbeShopCfDatePicker": "custom",
    "bfbeShopCfDateCalBackground": { "hex": "#ffffff" },
    "bfbeShopCfDateCalBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "18", "right": "18", "bottom": "18", "left": "18" } },
    "bfbeShopCfDateCalSelected": { "hex": "#6e44ff" },
    "bfbeShopCfDateCalSelectedColor": { "hex": "#ffffff" },
    "bfbeShopSlotPicker": "custom",
    "bfbeShopSlotTimePanelBg": { "hex": "#ffffff" },
    "bfbeShopSlotTimePanelBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "16", "right": "16", "bottom": "16", "left": "16" } },
    "bfbeShopSlotTimeOptOnBg": { "hex": "#f0ecff" },
    "bfbeShopSlotTimeTick": { "hex": "#6e44ff" },
    "bfbeShopSlotCalWidth": "100%",
    "bfbeShopSlotCalSelected": { "hex": "#6e44ff" },
    "bfbeShopSlotCalSelectedColor": { "hex": "#ffffff" }
  }
}
```

**The order review as cards.** Rows as lines so the shipping choices sit under their name, the payment methods as separate cards with their description inside, and the fields after the review in a tinted card of their own. Its own `bfbeShopCfDatePicker` because it prints the review fields itself.

```json
{
  "name": "woocommerce-checkout-order-review",
  "settings": {
    "_cssClasses": "checkout-review",
    "bfbeShopTableBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "16", "right": "16", "bottom": "16", "left": "16" } },
    "bfbeShopTableTitleMargin": { "top": "0", "right": "0", "bottom": "16", "left": "0" },
    "bfbeShopTableAlign": "left",
    "bfbeShopTableLine": { "hex": "#e9ecf1" },
    "bfbeShopTableTotalTypography": { "font-size": "18px", "font-weight": "800" },
    "bfbeShopTableLines": true,
    "bfbeShopPaymentGap": "10px",
    "bfbeShopPaymentMethodBackground": { "hex": "#ffffff" },
    "bfbeShopPaymentMethodBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "14", "right": "14", "bottom": "14", "left": "14" } },
    "bfbeShopPaymentMethodPadding": { "top": "14", "right": "16", "bottom": "14", "left": "16" },
    "bfbeShopPaymentMethodMargin": { "top": "0", "right": "0", "bottom": "0", "left": "0" },
    "bfbeShopPaymentBoxBackground": { "hex": "#f7f8fa" },
    "bfbeShopCfReviewSpace": "16px",
    "bfbeShopCfReviewGap": "14px",
    "bfbeShopCfReviewPadding": { "top": "20", "right": "20", "bottom": "20", "left": "20" },
    "bfbeShopCfReviewBackground": { "hex": "#f7f8fa" },
    "bfbeShopCfReviewBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "18", "right": "18", "bottom": "18", "left": "18" } },
    "bfbeShopCfDatePicker": "custom"
  }
}
```

**Floating labels on the classic checkout.** The switch as the checkout float probe sets it on the fixtures' classic Customer details (`dev/shop/checkout-float-probe.mjs`; the demo leaves it off), plus an inset, a colour while typing and the canvas preview from the schema. Labels rest in the box and rise onto its top border; **In the builder** `up` shows them risen in the canvas only, so they can be styled.

```json
{
  "name": "woocommerce-checkout-customer-details",
  "settings": { "bfbeShopLabelsAt": "border", "bfbeShopFloatInset": "14px", "bfbeShopFloatFocusColor": { "hex": "#6e44ff" }, "bfbeShopFloatPreview": "up", "_cssClasses": "checkout-float" }
}
```

## Gotchas

- **Two switches, and the export names one.** Date fields, Your checkout fields and Floating labels need **Checkout fields** (`shop-checkout-fields`); Delivery day and time and Delivery calendar need **Delivery** (`shop-delivery`). Table, Form fields and Payment are look only, with no switch. <!-- src: plugins/bfb-elements-pro/includes/shop/class-checkout-fields.php:101-103 ; plugins/bfb-elements-pro/includes/shop/class-checkout-float.php:45 ; plugins/bfb-elements-pro/includes/shop/class-delivery-slots.php:75 ; plugins/bfb-elements/includes/shop/class-woo-look.php:2-3 -->
- **Each element picks its own picker.** The choice is read from the element printing the field, so a date after the order review keeps the browser's picker unless Order review also sets `bfbeShopCfDatePicker: "custom"`. On v2 a form field with no choice takes the checkout's. <!-- src: plugins/bfb-elements-pro/includes/shop/class-checkout-fields.php:202-205 ; plugins/bfb-elements-pro/includes/shop/class-delivery-slots.php:117-120 -->
- **The calendar and list looks need the custom picker.** Every `bfbeShopCfDateCal*` key needs `bfbeShopCfDatePicker: "custom"`; every `bfbeShopSlotCal*` key and the time list's panel and option keys need `bfbeShopSlotPicker: "custom"`. The time box's own Typography, Background, Border and Padding style the plain select either way, and phones keep their own time list. <!-- src: plugins/bfb-elements-pro/includes/shop/class-checkout-fields.php:149 ; plugins/bfb-elements-pro/includes/shop/class-delivery-slots.php:93-108 -->
- **A required field needs a place to print.** WooCommerce checks every section of its list, so a required After the order review field on a checkout without Bricks' Order review (or, on v2, without the review hook) refuses every order with a field nobody can fill. <!-- src: plugins/bfb-elements-pro/includes/shop/class-checkout-fields.php:530-544 ; bricks/includes/woocommerce/elements/woocommerce-checkout-order-review.php:470 ; woocommerce/includes/class-wc-checkout.php:900-906 -->
- **Shown when is decided twice.** The browser hides and disables the field as the country or method changes; the server decides again from the posted values, so a hidden field is never required or saved. Cart rules decide on the server only. A billing field reads the billing country, a shipping field the shipping country only while "Ship to a different address" is ticked. <!-- src: src/elements/shop-checkout-fields/shop-checkout-fields.js:36-45 ; plugins/bfb-elements-pro/includes/shop/class-checkout-fields.php:366-390 ; plugins/bfb-elements-pro/includes/shop/class-checkout-fields.php:429-452 ; docs/elements/shop-checkout-fields.md "Shown when" -->
- **A required choice list has no empty option.** Its first choice is selected from the start, so a shopper can place the order without having chosen; add a first choice that asks, or leave it optional. <!-- src: plugins/bfb-elements-pro/includes/shop/class-checkout-fields.php:503-511 -->
- **The key is the meta name.** Renaming a key leaves earlier orders' answers under the old `_bfbe_field_<key>`: the new tag prints nothing for them. <!-- src: plugins/bfb-elements-pro/includes/shop/class-checkout-fields.php:49 ; plugins/bfb-elements-pro/includes/shop/class-checkout-fields.php:587 ; plugins/bfb-elements-pro/includes/shop/class-checkout-fields.php:592-593 -->
- **In the account steers the block, not the tag.** `{bfbe_order_field:key}` prints any saved field wherever an order is in hand; the "Your details" block lists only fields marked In the account, and only where WooCommerce's order details print (Bricks' Thank you element, the account's order page). <!-- src: plugins/bfb-elements-pro/includes/shop/class-checkout-fields.php:118-127 ; plugins/bfb-elements-pro/includes/shop/class-checkout-fields.php:667-679 -->
- **Floating labels skip some rows.** Tick boxes, radios, a label only screen readers read (the second address line), a country sold to alone, and the date and delivery fields keep their label above. Bricks' own Floating label style on v2 is another look: use one of the two. <!-- src: plugins/bfb-elements-pro/includes/shop/class-checkout-float.php:9-15 ; plugins/bfb-elements-pro/includes/shop/class-checkout-float.php:137-143 -->
- **Float styling needs the floating labels.** Height on the border, Inset, Gap, both colours and In the builder show only with `bfbeShopLabelsAt: "border"`. <!-- src: ../bfbe-schemas/references/features/shop-checkout.json "bfbeShopFloatHeight" --> <!-- src: plugins/bfb-elements-pro/includes/shop/class-checkout-float.php:65-84 -->
- **The delivery day obeys the estimate.** The window opens at the earliest delivery estimate for the chosen method and closes at Bookable days ahead; a full slot (orders that are processing, on hold or completed) and a day outside the window are refused by the server with WooCommerce's notice. Only the first delivery field becomes the order's promised date. <!-- src: plugins/bfb-elements-pro/includes/shop/class-delivery-slots.php:244-279 ; plugins/bfb-elements-pro/includes/shop/class-delivery-slots.php:486-546 ; plugins/bfb-elements-pro/includes/shop/class-delivery-slots.php:556-580 -->
- **Rows as lines is for the order review only.** `bfbeShopTableLines` exists there, not on Thank you, which has no border or total controls either; the thank-you page's look is Text align, the line, the header row and the product name. <!-- src: plugins/bfb-elements/includes/shop/class-woo-look.php:38-44 -->
- **The 2.3 builder can lag one save.** On Bricks 2.3.10 a change to Floating labels, which rewrites the element's finished output, can show in the canvas only after the next save; the page is right. <!-- src: plugins/bfb-elements/includes/shop/class-woo-elements.php:13-17 -->

## Never do

- Do not set a `bfbeShopCfDateCal*` key without `bfbeShopCfDatePicker: "custom"`, or a `bfbeShopSlotCal*` or time-list panel key without `bfbeShopSlotPicker: "custom"`.
- Do not set the picker on Customer details alone when Order review prints date or delivery fields too.
- Do not make an After the order review field required on a checkout without Bricks' Order review, or without the review hook on v2.
- Do not rename a field's key once orders carry it.
- Do not use Bricks' own Floating label style on v2 together with `bfbeShopLabelsAt: "border"`.
- Do not set float styling keys without `bfbeShopLabelsAt: "border"`.
- Do not expect a field of yours on Checkout (v2) without a WooCommerce form field picking it.
- Do not rely on In the account to keep a field off a page; the tag prints every saved field.
