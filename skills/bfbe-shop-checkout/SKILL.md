---
name: bfbe-shop-checkout
description: "Use for the shop's settings on Bricks' Checkout customer details, Order review and Thank you (and the 2.4 v2 checkout): the table and fields look, floating labels, your own checkout fields and their date pickers, delivery days and time slots, the payment list (BFB Shop checkout, `shop-checkout`). Read before writing these settings."
---

# BFB Shop checkout (`shop-checkout`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 2.0.0 or later, and BFB Elements Pro 2.0.0 or later for the groups marked Pro, WooCommerce active, the feature switch on (WordPress menu BFB Elements, Elements): `shop-checkout-fields`. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/shop-checkout.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/shop-checkout/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

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
- `bfbeShopCfDatePicker` (select) **Date picker**: options: `native` The browser's, `custom` Styled with the controls. Your checkout fields of the Date type.
Styling, in the schema file: `bfbeShopCfDateCalWidth`, `bfbeShopCfDateCalBackground`, `bfbeShopCfDateCalBorder`, `bfbeShopCfDateCalShadow`, `bfbeShopCfDateCalPadding`, `bfbeShopCfDateCalOffset`, `bfbeShopCfDateCalHeadSpace`, `bfbeShopCfDateCalWeekSpace`, `bfbeShopCfDateCalDayGap`, `bfbeShopCfDateCalHeadLine`, `bfbeShopCfDateCalHeadLineColor`, `bfbeShopCfDateCalWeekLine`, `bfbeShopCfDateCalWeekLineColor`, `bfbeShopCfDateCalMonthTypography`, `bfbeShopCfDateCalMonthPadding`, `bfbeShopCfDateCalYearPadding`, `bfbeShopCfDateCalHeadHoverBg`, `bfbeShopCfDateCalYearArrow`, `bfbeShopCfDateCalYearArrowHover`, `bfbeShopCfDateCalArrowSize`, `bfbeShopCfDateCalArrowPadding`, `bfbeShopCfDateCalArrowColor`, `bfbeShopCfDateCalArrowHover`, `bfbeShopCfDateCalArrowBg`, `bfbeShopCfDateCalArrowHoverBg`, `bfbeShopCfDateCalArrowBorder`, `bfbeShopCfDateCalArrowHoverBorder`, `bfbeShopCfDateCalWeekdayTypography`, `bfbeShopCfDateCalDayTypography`, `bfbeShopCfDateCalDaySize`, `bfbeShopCfDateCalDayPadding`, `bfbeShopCfDateCalDayBg`, `bfbeShopCfDateCalDayColor`, `bfbeShopCfDateCalDayBorder`, `bfbeShopCfDateCalDayHoverBg`, `bfbeShopCfDateCalDayHoverColor`, `bfbeShopCfDateCalDayHoverBorder`, `bfbeShopCfDateCalTodayBg`, `bfbeShopCfDateCalTodayColor`, `bfbeShopCfDateCalTodayBorder`, `bfbeShopCfDateCalTodayHoverBg`, `bfbeShopCfDateCalTodayHoverColor`, `bfbeShopCfDateCalTodayHoverBorder`, `bfbeShopCfDateCalSelected`, `bfbeShopCfDateCalSelectedColor`, `bfbeShopCfDateCalSelectedBorder`, `bfbeShopCfDateCalSelectedHoverBg`, `bfbeShopCfDateCalSelectedHoverColor`, `bfbeShopCfDateCalSelectedHoverBorder`, `bfbeShopCfDateCalShutBg`, `bfbeShopCfDateCalShut`, `bfbeShopCfDateCalShutBorder`, `bfbeShopCfDateCalShutHoverBg`, `bfbeShopCfDateCalShutHoverColor`, `bfbeShopCfDateCalShutHoverBorder`, `bfbeShopCfDateCalOtherBg`, `bfbeShopCfDateCalOther`, `bfbeShopCfDateCalOtherBorder`, `bfbeShopCfDateCalOtherHoverBg`, `bfbeShopCfDateCalOtherHoverColor`, `bfbeShopCfDateCalOtherHoverBorder`.

#### BFB Floating labels (`bfbeShopFloat`)
Pro.
- `bfbeShopLabelsAt` (select) **Labels**: options: `above` Above the field (default), `border` Floating, on the border
- `bfbeShopFloatPreview` (select) **In the builder**: options: `page` As the page shows them (default), `up` Risen, so you can style them; only when `bfbeShopLabelsAt` is `border`
Styling, in the schema file: `bfbeShopFloatHeight`, `bfbeShopFloatInset`, `bfbeShopFloatGap`, `bfbeShopFloatRestColor`, `bfbeShopFloatFocusColor`.

#### BFB Delivery day and time (`bfbeShopSlot`)
Pro.
- `bfbeShopSlotPicker` (select) **Day and time pickers**: options: `native` The browser's, `custom` Styled with the controls. Phones keep their own time list.
Styling, in the schema file: `bfbeShopSlotTimeTypography`, `bfbeShopSlotTimeBackground`, `bfbeShopSlotTimeBorder`, `bfbeShopSlotTimePadding`, `bfbeShopSlotTimeChevron`, `bfbeShopSlotTimePanelBg`, `bfbeShopSlotTimePanelBorder`, `bfbeShopSlotTimePanelShadow`, `bfbeShopSlotTimePanelPadding`, `bfbeShopSlotTimeOptTypography`, `bfbeShopSlotTimeOptPadding`, `bfbeShopSlotTimeOptHover`, `bfbeShopSlotTimeHoverText`, `bfbeShopSlotTimeOptOnBg`, `bfbeShopSlotTimeOptOnColor`, `bfbeShopSlotTimeTick`.

#### BFB Delivery calendar (`bfbeShopSlotCal`)
Pro.
Styling only, every key in the schema file: `bfbeShopSlotCalWidth`, `bfbeShopSlotCalBackground`, `bfbeShopSlotCalBorder`, `bfbeShopSlotCalShadow`, `bfbeShopSlotCalPadding`, `bfbeShopSlotCalOffset`, `bfbeShopSlotCalHeadSpace`, `bfbeShopSlotCalWeekSpace`, `bfbeShopSlotCalDayGap`, `bfbeShopSlotCalHeadLine`, `bfbeShopSlotCalHeadLineColor`, `bfbeShopSlotCalWeekLine`, `bfbeShopSlotCalWeekLineColor`, `bfbeShopSlotCalMonthTypography`, `bfbeShopSlotCalMonthPadding`, `bfbeShopSlotCalYearPadding`, `bfbeShopSlotCalHeadHoverBg`, `bfbeShopSlotCalYearArrow`, `bfbeShopSlotCalYearArrowHover`, `bfbeShopSlotCalArrowSize`, `bfbeShopSlotCalArrowPadding`, `bfbeShopSlotCalArrowColor`, `bfbeShopSlotCalArrowHover`, `bfbeShopSlotCalArrowBg`, `bfbeShopSlotCalArrowHoverBg`, `bfbeShopSlotCalArrowBorder`, `bfbeShopSlotCalArrowHoverBorder`, `bfbeShopSlotCalWeekdayTypography`, `bfbeShopSlotCalDayTypography`, `bfbeShopSlotCalDaySize`, `bfbeShopSlotCalDayPadding`, `bfbeShopSlotCalDayBg`, `bfbeShopSlotCalDayColor`, `bfbeShopSlotCalDayBorder`, `bfbeShopSlotCalDayHoverBg`, `bfbeShopSlotCalDayHoverColor`, `bfbeShopSlotCalDayHoverBorder`, `bfbeShopSlotCalTodayBg`, `bfbeShopSlotCalTodayColor`, `bfbeShopSlotCalTodayBorder`, `bfbeShopSlotCalTodayHoverBg`, `bfbeShopSlotCalTodayHoverColor`, `bfbeShopSlotCalTodayHoverBorder`, `bfbeShopSlotCalSelected`, `bfbeShopSlotCalSelectedColor`, `bfbeShopSlotCalSelectedBorder`, `bfbeShopSlotCalSelectedHoverBg`, `bfbeShopSlotCalSelectedHoverColor`, `bfbeShopSlotCalSelectedHoverBorder`, `bfbeShopSlotCalShutBg`, `bfbeShopSlotCalShut`, `bfbeShopSlotCalShutBorder`, `bfbeShopSlotCalShutHoverBg`, `bfbeShopSlotCalShutHoverColor`, `bfbeShopSlotCalShutHoverBorder`, `bfbeShopSlotCalOtherBg`, `bfbeShopSlotCalOther`, `bfbeShopSlotCalOtherBorder`, `bfbeShopSlotCalOtherHoverBg`, `bfbeShopSlotCalOtherHoverColor`, `bfbeShopSlotCalOtherHoverBorder`.

### Checkout order review (`woocommerce-checkout-order-review`)

#### BFB Table (`bfbeShopTable`)
Free.
Styling only, every key in the schema file: `bfbeShopTableBorder`, `bfbeShopTableTitleMargin`, `bfbeShopTableAlign`, `bfbeShopTableLine`, `bfbeShopTableHeadBackground`, `bfbeShopTableHeadTypography`, `bfbeShopTableTotalTypography`, `bfbeShopTableLines`.

#### BFB Form fields (`bfbeShopFields`)
Free.
Styling only, every key in the schema file: `bfbeShopFieldsRowGap`, `bfbeShopFieldsRowSpacing`, `bfbeShopFieldsSelectBorder`, `bfbeShopFieldsSelectHeight`, `bfbeShopFieldsSelectPadding`.

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

_Not written yet._

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
