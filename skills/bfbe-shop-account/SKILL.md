---
name: bfbe-shop-account
description: "Use for the shop's settings on Bricks' Account page and Register form: the table and fields look, the account page's navigation and signed-out view, confirm fields on registration (BFB Shop account, `shop-account`). Read before writing these settings."
---

# BFB Shop account (`shop-account`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 2.0.0 or later, WooCommerce active, the feature switch on (WordPress menu BFB Elements, Elements): `shop-account`. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/shop-account.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/shop-account/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

## Where it lives
A feature, not an element: its groups are added to Bricks' own elements, on the Content tab after Bricks' own groups. By element:
- Account - Register form (`woocommerce-account-form-register`): BFB Registration (`bfbeShopRegister`).
- Account - Page (`woocommerce-account-page`): BFB Table (`bfbeShopTable`), BFB Form fields (`bfbeShopFields`), BFB Account page (`bfbeShopAccountPage`).
- `woocommerce-account-register-form`: BFB Registration (`bfbeShopRegister`). Not registered on the export site (Bricks 2.3.10): a Bricks 2.4 element. The controls are the ones the pack adds when Bricks registers it.

## Settings that decide the build

### Account - Register form (`woocommerce-account-form-register`)

#### BFB Registration (`bfbeShopRegister`)
Free, switch `shop-account`.
- `bfbeShopConfirmEmail` (checkbox) **Confirm email**
- `bfbeShopConfirmEmailLabel` (text) **Confirm email label**: placeholder Confirm email address; only when `bfbeShopConfirmEmail` is set
- `bfbeShopConfirmPassword` (checkbox) **Confirm password**
- `bfbeShopConfirmPasswordLabel` (text) **Confirm password label**: placeholder Confirm password; only when `bfbeShopConfirmPassword` is set
Styling, in the schema file: `bfbeShopConfirmHintTypography`, `bfbeShopConfirmMismatchBorder`.

### Account - Page (`woocommerce-account-page`)

#### BFB Table (`bfbeShopTable`)
Free.
Styling only, every key in the schema file: `bfbeShopTableBorder`, `bfbeShopTableCellPadding`, `bfbeShopTableAlign`, `bfbeShopTableLine`, `bfbeShopTableHeadBackground`, `bfbeShopTableHeadTypography`, `bfbeShopTableLinkTypography`, `bfbeShopTableStack`, `bfbeShopTableStackPadding`, `bfbeShopTableLabelTypography`.

#### BFB Form fields (`bfbeShopFields`)
Free.
Styling only, every key in the schema file: `bfbeShopFieldsRowGap`, `bfbeShopFieldsRowSpacing`, `bfbeShopFieldsSelectBorder`, `bfbeShopFieldsSelectHeight`, `bfbeShopFieldsSelectPadding`.

#### BFB Account page (`bfbeShopAccountPage`)
Free.
Styling only, every key in the schema file: `bfbeShopAccountNavPadding`, `bfbeShopAccountNavFit`, `bfbeShopAccountOrderTitleTypography`, `bfbeShopAccountOrderTitleMargin`, `bfbeShopAccountOrderMargin`, `bfbeShopAccountMarkTypography`, `bfbeShopAccountMarkBackground`, `bfbeShopAccountMarkBorder`, `bfbeShopAccountMarkPadding`.

### `woocommerce-account-register-form`
Not registered on the export site (Bricks 2.3.10): a Bricks 2.4 element. The controls are the ones the pack adds when Bricks registers it.

#### BFB Registration (`bfbeShopRegister`)
The same 6 controls as on `woocommerce-account-form-register`.
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
