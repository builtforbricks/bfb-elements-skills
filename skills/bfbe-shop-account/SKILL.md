---
name: bfbe-shop-account
description: "Use for the shop's settings on Bricks' Account page and Register form: account pages of your own from Bricks templates, WooCommerce's pages renamed or hidden, where customers land after login or logout, confirm email and password on registration, and the orders table, fields and menu look (BFB Shop account, `shop-account`). Read before writing these settings."
---

# BFB Shop account (`shop-account`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 2.0.0 or later, WooCommerce active, the feature switch on (WordPress menu BFB Elements, Elements): `shop-account`. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/shop-account.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/shop-account/

## What it is
A free feature with three parts on WooCommerce's account: pages of your own drawn from Bricks templates, with WooCommerce's own pages renamed, reordered or hidden; a chosen page after logging in, registering or logging out, by role; and confirm email and password fields on Bricks' register forms. Everything goes through WooCommerce's own hooks, so its account menu, its endpoints and its redirects stay WooCommerce's.

**Not for:** Not a membership or a sign-in page builder: an account page needs a signed-in visitor, as WooCommerce's own do, and takes one template. To design the whole account, use Bricks' Account page element and its templates.

**Nestable:** no · **In a query loop:** no · **Dynamic data:** no · **Keyboard:** no · **Reduced motion:** no

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

## What it guarantees for accessibility (do not undo)
- Each confirm field has its own label, is marked required and carries autocomplete email or new-password.
- A mismatch is said in a polite live region tied to the field with aria-describedby, and the field is marked aria-invalid, once the visitor leaves it.
- The server refuses a mismatch with a WooCommerce notice, so the check holds with the script off.
<!-- bfbe:generated:end -->

## Rendered DOM

The feature adds no element. Bricks' Account page and register form keep their markup; the feature adds menu items and pages through WooCommerce's hooks, two confirm fields inside the register form, and CSS at the host's id.

```html
<!-- Account page: a page of your own, a WooCommerce endpoint -->
<nav class="woocommerce-MyAccount-navigation"><ul>
  <li class="woocommerce-MyAccount-navigation-link woocommerce-MyAccount-navigation-link--loyalty bfbe-account-item {icon classes} is-active"><a href="/my-account/loyalty/">Loyalty</a></li>
</ul></nav>
<div class="woocommerce-MyAccount-content">
  <div class="bfbe-account-page bfbe-account-page--loyalty">… the Bricks template …</div>
</div>

<!-- Register form: right after the email field (div.form-group in Bricks' v1 form, p.form-row in WooCommerce's) -->
<div class="form-group bfbe-confirm">
  <label for="bfbe_email_confirm">Confirm email address&nbsp;<span class="required" aria-hidden="true">*</span></label>
  <input type="email" class="woocommerce-Input woocommerce-Input--text input-text" name="bfbe_email_confirm" id="bfbe_email_confirm"
         autocomplete="email" required data-bfbe-confirm="reg_email" aria-describedby="bfbe_email_confirm_hint">
  <span class="bfbe-confirm__hint" id="bfbe_email_confirm_hint" aria-live="polite"></span>
  <input type="hidden" name="bfbe_confirm" value="email,password"><input type="hidden" name="bfbe_confirm_sig" value="…">
</div>
```

- The menu item takes `bfbe-account-item` and the row's **Icon class** words only when that column is filled. A visitor the page is not for gets `p.bfbe-account__refused` in place of the template.
- The password confirm (`bfbe_password_confirm`, `autocomplete="new-password"`) follows the password field the same way. While the visitor types, the script sets `aria-invalid` and `bfbe-confirm--mismatch` on the confirm input and writes the hint.
- **BFB Registration** look: `bfbeShopConfirmHintTypography` writes `.bfbe-confirm__hint`, `bfbeShopConfirmMismatchBorder` the border colour of `.bfbe-confirm--mismatch`.
- **BFB Table** writes `table.shop_table` (the orders and downloads tables): border, cell padding, text align, the line between rows, the header row, `.product-name a`. **Stack the rows** (`bfbeShopTableStack`) turns `table.shop_table_responsive` rows into blocks, each cell its `data-title` label and its value on one line.
- **BFB Form fields** writes `.form-row` (gap between label and field, space under a row) and WooCommerce's select2 dropdowns. **BFB Account page** writes `.woocommerce-MyAccount-navigation` (padding; **As tall as its items** sets `align-self: flex-start`), an order page's headings and sections, and the `mark` elements around the order number, date and status.
- To a signed-out visitor with no Bricks login template, the Account page element wraps WooCommerce's login and register forms in its own root, so its style controls reach them.

## Wiring to other elements

- **Your account pages** come from BFB Elements, Shop, Customers, card **Your account pages**: **Menu name**, **Slug**, **Template** (a published Bricks section or content template), **Place in the menu**, **Icon class**, **Who sees it**. Each is a WooCommerce endpoint, so it renders inside Bricks' Account page element under its menu, marked current. Saved in the option `bfbe_shop_account` (`pages`: `title`, `slug`, `template`, `position`, `icon`, `who`).
- **The template knows the customer.** Its dynamic data and query loops read the signed-in visitor: the demo shop's "Your lists" page is a section template with a Wishlist loop (`bfbeShopWishlist`); orders are `bfbeShopOrders` (`bfbe-shop-loops`).
- **WooCommerce's account pages** (card of that name, `woo`: `item`, `label`, `shown`): every WooCommerce item once, renamed (**Rename to**), left out (**In the menu**) and reordered by row order. Items other plugins add stay before Log out.
- **Where customers land** (`redirects`: `event` login, registration or logout; `role`; `page` as an id, slug, path or address on the site): obeyed by WooCommerce's forms, Bricks' login and register elements and wp-login.php.
- **Confirm fields need Bricks' register form element** (`woocommerce-account-form-register`, or the 2.4 v2 wrapper). The Account page's own signed-out forms are WooCommerce's and get none.
- **Refusals are WooCommerce notices.** On the My Account page WooCommerce prints them; on any other page place Bricks' Notice element, which Bricks registers only with its setting "Use Bricks' WooCommerce notice" on.
- Other account parts: BFB Withdrawal Button on an order's page (`bfbe-withdrawal-button`), order tags on view-order (`bfbe-shop-tags-and-conditions`). Nothing here needs a class or id; `_cssClasses` is for your own CSS.

## Verified patterns

**An account page styled through its BFB groups.** From the 2.4 site's demo shop, template "Fernhouse: my account" (`bfb-demo-account`). The menu box only as tall as its items, an order page's headings sized as the account's cards, the status marks as quiet pills, the orders table rounded and stacked at the phone breakpoint, the address form's rows spaced. Trimmed: Bricks' own menu controls and some typography; the demo's colour variables kept as hex.

```json
{
  "name": "woocommerce-account-page",
  "settings": {
    "_cssClasses": "account",
    "bfbeShopAccountNavPadding": { "top": "8", "right": "8", "bottom": "8", "left": "8" },
    "bfbeShopAccountNavFit": true,
    "bfbeShopAccountOrderTitleTypography": { "font-size": "22px", "font-weight": "800", "line-height": "1.2" },
    "bfbeShopAccountOrderTitleMargin": { "top": "32", "right": "0", "bottom": "14", "left": "0" },
    "bfbeShopAccountMarkBackground": { "hex": "#f6f6f8" },
    "bfbeShopAccountMarkBorder": { "radius": { "top": "999", "right": "999", "bottom": "999", "left": "999" } },
    "bfbeShopAccountMarkPadding": { "top": "2", "right": "8", "bottom": "2", "left": "8" },
    "bfbeShopTableBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "16", "right": "16", "bottom": "16", "left": "16" } },
    "bfbeShopTableCellPadding": { "top": "16", "right": "16", "bottom": "16", "left": "16" },
    "bfbeShopTableLine": { "hex": "#e9ecf1" },
    "bfbeShopTableHeadBackground": { "hex": "#f7f8fa" },
    "bfbeShopTableStack:mobile_landscape": true,
    "bfbeShopTableStackPadding:mobile_landscape": { "top": "10", "right": "16", "bottom": "10", "left": "16" },
    "bfbeShopTableLabelTypography": { "font-weight": "700" },
    "bfbeShopFieldsRowGap": "6px",
    "bfbeShopFieldsRowSpacing": "14px"
  }
}
```

**A register form that asks twice.** From the register fixture (`fixture-shop-p8-register`). Both confirm fields on, the password's label set; the email's keeps "Confirm email address". Put Bricks' Notice element on the same page so a refused post says why.

```json
{
  "name": "woocommerce-account-form-register",
  "settings": { "bfbeShopConfirmEmail": true, "bfbeShopConfirmPassword": true, "bfbeShopConfirmPasswordLabel": "Repeat your password", "_cssClasses": "register" }
}
```

## Gotchas

- **The look groups need no switch; the rest does.** BFB Table, BFB Form fields and BFB Account page are look only and always there; BFB Registration, your pages and the landing rules need the **Account** switch (`shop-account`). <!-- src: plugins/bfb-elements/includes/shop/class-woo-look.php:2-3 ; plugins/bfb-elements/includes/shop/class-account.php:47-49 -->
- **Bricks 2.4's Account v2 gets none of the look groups.** They are added to the classic Account page only; on v2 your page renders inside the dashboard state's wrapper (`brx-wc-account-page-v2--dashboard`), so styling on that state reaches it too. <!-- src: plugins/bfb-elements/includes/shop/class-woo-elements.php:54-55 ; plugins/bfb-elements/includes/shop/class-woo-look.php:38-44 --> <!-- src: docs/elements/shop-account.md "With Bricks' Account page element" -->
- **WooCommerce's slugs are refused.** `orders`, `downloads`, `view-order`, `order-withdrawal` and the other WooCommerce endpoints are not saved as your page; a new page that answers "not found" needs WordPress' Permalinks saved once. <!-- src: plugins/bfb-elements/includes/shop/class-account.php:251-255 ; plugins/bfb-elements/includes/shop/class-account.php:275-278 --> <!-- src: docs/elements/shop-account.md "Account pages (Shop page)" -->
- **No published template, no page.** A page whose template is missing or unpublished shows an administrator a notice and every other customer nothing. <!-- src: plugins/bfb-elements/includes/shop/class-account.php:385-392 -->
- **Hidden is not closed.** A WooCommerce item left out of the menu still answers at its address; only a page of yours set to a role refuses everyone else ("This page is not available for your account."). <!-- src: docs/elements/shop-account.md "Account pages (Shop page)" ; plugins/bfb-elements/includes/shop/class-account.php:298-305 ; plugins/bfb-elements/includes/shop/class-account.php:380-384 -->
- **A login at the checkout stays there.** WooCommerce's own `redirect` field beats every rule; a rule for the visitor's role beats one for any role. <!-- src: plugins/bfb-elements/includes/shop/class-account.php:412-431 ; plugins/bfb-elements/includes/shop/class-account.php:460-463 -->
- **The password confirm needs a password field.** With WooCommerce set to send a link to set a password, the form has none and only the email confirm prints. <!-- src: plugins/bfb-elements/includes/shop/class-account.php:605-611 --> <!-- src: docs/elements/shop-account.md "BFB Registration (the register form element)" -->
- **A refusal needs somewhere to print.** Off the My Account page, without Bricks' Notice element (and its setting on) a refused post shows nothing; the typed confirm comes back so the visitor sees it. <!-- src: docs/elements/shop-account.md "BFB Registration (the register form element)" --> <!-- src: dev/shop/p8-probe.mjs:318-338 -->
- **The marker is signed with the site's salts.** A page cached before a salt change or a site move posts a stale signature and is refused with "The form was out of date. Please reload the page and try again." <!-- src: plugins/bfb-elements/includes/shop/class-account.php:577-580 ; plugins/bfb-elements/includes/shop/class-account.php:657-661 -->
- **Stacked cell padding is not scoped to the stack.** `bfbeShopTableStackPadding` writes every cell of `table.shop_table_responsive`, so set it at the same breakpoint as `bfbeShopTableStack`, as the demo does. <!-- src: plugins/bfb-elements/includes/shop/class-woo-look.php:286-290 ; dev/demo/shop/15-templates-buy.php:203 -->
- **The 2.3 builder shows confirm fields late.** On Bricks 2.3.10 a change to BFB Registration shows after the canvas reloads. <!-- src: docs/elements/shop-account.md "BFB Registration (the register form element)" ; plugins/bfb-elements/includes/shop/class-woo-elements.php:13-17 -->

## Never do

- Do not give your own account page a WooCommerce slug.
- Do not hide a WooCommerce item to keep customers out of it; it still answers at its address.
- Do not set the BFB look groups on Account v2 and expect them; they live on the classic Account page.
- Do not set `bfbeShopConfirmEmailLabel` or `bfbeShopConfirmPasswordLabel` without their switch.
- Do not expect confirm fields on the Account page's own signed-out forms; use Bricks' register form element.
- Do not place a register form off the My Account page without Bricks' Notice element.
- Do not set `bfbeShopTableStackPadding` outside the breakpoint that stacks the rows.
