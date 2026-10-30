---
name: bfbe-tax-switch
description: "Use when placing, wiring or styling BFB Tax Switch (`bfbe-tax-switch`). Read before writing its settings."
---

# BFB Tax Switch (`bfbe-tax-switch`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-tax-switch.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/tax-switch/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 0.26 KB, JS 0.62 KB (gzipped), no dependencies, loaded only on pages that use it.

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Switch (`bfbeSwitch`)
- `label` (text) **Label**: placeholder Prices; dynamic data accepted
- `labelShow` (select) **Label shown**: options: `show` Beside the buttons (default), `sr` Hidden
- `inclText` (text) **With tax**: placeholder With VAT; dynamic data accepted
- `exclText` (text) **Without tax**: placeholder Without VAT; dynamic data accepted
Styling, in the schema file: `labelTypography`, `buttonTypography`, `buttonBackground`, `buttonBorder`, `buttonShadow`, `buttonPadding`, `buttonGap`, `hoverBackground`, `hoverColor`, `pressedTypography`, `pressedBackground`, `pressedColor`, `pressedBorder`.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<form class="brxe-bfbe-tax-switch bfbe-taxsw" method="post" data-bfbe-taxsw data-bfbe-taxsw-default="excl"
      data-bfbe-taxsw-incl="Prices are shown with tax." data-bfbe-taxsw-excl="Prices are shown without tax.">
  <input type="hidden" …>                                               <!-- the shop's action fields, for the no-script post -->
  <span class="bfbe-taxsw__label" id="{id}">Prices</span>               <!-- + bfbe-sr with Label shown: Hidden -->
  <span class="bfbe-taxsw__btns" role="group" aria-labelledby="{id}">
    <button type="submit" class="bfbe-taxsw__btn bfbe-chip" name="bfbe_tax" value="incl" data-bfbe-tax="incl" aria-pressed="false">With VAT</button>
    <button type="submit" class="bfbe-taxsw__btn bfbe-chip" name="bfbe_tax" value="excl" data-bfbe-tax="excl" aria-pressed="true">Without VAT</button>
  </span>
</form>
```

- The root is a real `<form>`; in the canvas the buttons are `type="button"`.
- Every price it switches is printed twice, `<span class="bfbe-tax" data-bfbe-tax-default="excl"><span class="bfbe-tax__incl">…</span><span class="bfbe-tax__excl">…</span></span>`, and one half shows by the class on `<html>`: `bfbe-tax-incl` or `bfbe-tax-excl`. With neither class, `data-bfbe-tax-default` (WooCommerce's shop display setting) decides.
- Once a switch has rendered, every page's `<head>` carries `script#bfbe-tax` (applies the stored choice before paint) and `style#bfbe-tax-css` (hides the other half).
- States: `aria-pressed` on the two buttons, the same on every switch of the page.
- Where controls write: `labelTypography` to the label while it shows; `buttonTypography`, `buttonBackground`, `buttonBorder`, `buttonShadow` and `buttonPadding` to `.bfbe-taxsw__btn`; `buttonGap` to `.bfbe-taxsw__btns`; `hoverBackground` and `hoverColor` to the unpressed button on hover and focus; `pressed*` to `.bfbe-taxsw__btn[aria-pressed="true"]`. Bricks' own Style tab styles the form round them.
- `window.bfbeTaxSwitch()` binds switches added later.

## Wiring to other elements

- **Every price on the site, by filter.** The switch targets no element: the pack wraps every price that passes through WooCommerce's `woocommerce_get_price_html` (Bricks' Product price, Products, product cards and query loops, the variation's price) and the classic cart's item price, line total and subtotal (cart, mini cart, checkout). Cards Bricks loads by AJAX pagination, infinite scroll or query filters carry both halves too.
- **Several switches move together.** A switch in the header and one on the product page share the choice; pressing either updates both and every price.
- **The EU price lines** (skill `bfbe-shop-price-and-stock`): each half of a price carries its own lowest and unit price lines, so they switch with it.
- **The Shop page.** BFB Elements, Shop, **Prices with or without tax**: **Include both prices from the start** prints both halves on every page before any switch has rendered. Hub skill `bfbe-shop`.
- Place it anywhere: a header, a catalogue's toolbar, beside a price. Nothing points at it by class or id.

## Verified patterns

**In the shop's utility bar** (the demo shop's header, `dev/demo/shop/10-templates.php`, "Tax switch"). The buttons are white pills with a hairline, and the pressed one is ink with white text. The demo's typography and colour variables are left out; colours are plain hex.

```json
{
  "name": "bfbe-tax-switch",
  "settings": {
    "label": "Prices", "inclText": "With VAT", "exclText": "Without VAT",
    "buttonBackground": { "hex": "#ffffff" },
    "buttonBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "999", "right": "999", "bottom": "999", "left": "999" } },
    "pressedBackground": { "hex": "#101828" }, "pressedColor": { "hex": "#ffffff" }
  }
}
```

**Over a product grid** (fixture page `fixture-shop-p4`, `.p4-tax`). The switch with its default words above Bricks' Products element; every card's price carries both halves and changes on a press.

```json
{
  "name": "block",
  "settings": { "_rowGap": "24px" },
  "children": [
    { "name": "bfbe-tax-switch", "settings": { "label": "Prices", "_cssClasses": "p4-tax" } },
    { "name": "woocommerce-products", "settings": { "columns": 3, "gap": "24px", "posts_per_page": 3, "orderby": "menu_order", "_cssClasses": "p4-grid" } }
  ]
}
```

## Gotchas

- **Taxes off, nothing on the page.** With **Enable tax rates and calculations** off in WooCommerce the switch renders nothing and no price is doubled; the canvas says why. <!-- src: plugins/bfb-elements-pro/elements/tax-switch.php:235-240 ; plugins/bfb-elements-pro/includes/shop/class-tax.php:99-101 -->
- **Both prices start after the first switch renders.** Prices are doubled site-wide from the first front-end render of a switch (an option), so the page view that renders it first still prints one price. **Include both prices from the start** on the Shop page removes that wait. <!-- src: plugins/bfb-elements-pro/elements/tax-switch.php:243 ; plugins/bfb-elements-pro/includes/shop/class-tax.php:99-108 ; plugins/bfb-elements-pro/includes/shop/class-tax.php:189-192 -->
- **The switch is a form.** Its root is `<form method="post">`, so inside a Bricks Form, BFB Advanced Forms or an Add to cart form it nests one form in another and breaks both. <!-- src: plugins/bfb-elements-pro/elements/tax-switch.php:251 -->
- **The totals table keeps WooCommerce's cart setting.** Item prices, line totals and the subtotal switch; shipping, fees, discounts, tax lines and the total stay as **Display prices during cart and checkout** says, so in the other mode they do not add up to the subtotal shown. <!-- src: plugins/bfb-elements-pro/includes/shop/class-tax.php:196-199 ; docs/elements/tax-switch.md "Which price shows" -->
- **Block cart and block checkout are not reached.** WooCommerce's cart, checkout and mini cart blocks price through the Store API, which carries one figure; they follow the cart setting. <!-- src: docs/elements/tax-switch.md "What it does not do" ; dev/shop/p4-probe.mjs:216 -->
- **One price where nothing differs.** A product that is not taxable, or whose two figures are the same, keeps one price. The figures use the shop's base address until a customer gives one. <!-- src: plugins/bfb-elements-pro/includes/shop/class-tax.php:248-255 ; docs/elements/tax-switch.md "What it does not do" -->
- **Before a choice, WooCommerce's setting shows.** **Display prices in the shop** picks the half and the pressed button for a visitor who has not chosen; the choice is then kept in the visitor's browser (`bfbe_shop_tax`, kind needed) and, after a press, their WooCommerce session. <!-- src: plugins/bfb-elements-pro/includes/shop/class-tax.php:111-114 ; src/elements/tax-switch/tax-switch.js:10-14 ; docs/elements/tax-switch.md "What is stored" -->
- **The no-script choice turns off page caching for that visitor.** While their session holds a choice, their pages are sent with WooCommerce's no-cache headers. <!-- src: plugins/bfb-elements-pro/includes/shop/class-tax.php:163-167 -->
- **Label shown: Hidden drops the label's typography.** `labelShow: "sr"` keeps the words for screen readers and hides **Label** typography `labelTypography` from the panel. The pressed button is weight 600 until `pressedTypography` sets its own. <!-- src: plugins/bfb-elements-pro/elements/tax-switch.php:212 ; src/elements/tax-switch/tax-switch.css:4 -->
- **A site-wide cost once used.** The head snippet is 294 bytes gzipped on every page from the first render on, and every price prints twice, so a product grid's HTML grows. It never changes what a customer pays. <!-- src: docs/elements/tax-switch.md "Cost" ; plugins/bfb-elements-pro/includes/shop/class-tax.php:144-157 -->

## Never do

- Do not place the switch on a shop with taxes off in WooCommerce.
- Do not put it inside a Bricks Form, BFB Advanced Forms or an Add to cart form.
- Do not rely on the cart totals, shipping or tax lines switching; only prices, line totals and the subtotal do.
- Do not use it with WooCommerce's block cart or block checkout and expect their prices to change.
- Do not set `labelTypography` with `labelShow: "sr"`; the panel hides it.
- Do not leave **Include both prices from the start** off when the switch's first page view must already show both prices.
