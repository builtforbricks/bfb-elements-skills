---
name: bfbe-applied-coupons
description: "Use for BFB Applied Coupons (`bfbe-applied-coupons`): the coupons on the cart listed anywhere, each with its amount and a Remove button, beside Bricks' Cart coupon or on its own. Read before writing its settings."
---

# BFB Applied Coupons (`bfbe-applied-coupons`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-applied-coupons.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/applied-coupons/

## What it is
The coupons on the cart, each with WooCommerce's label, its amount and a Remove button, placed anywhere: beside Bricks' Cart coupon element, above the totals, in the cart's sidebar or on any page. Remove goes through WooCommerce's own remove without leaving the page. It needs the Coupons feature on, and it hides while no coupon is applied.

**Not for:** It is not a coupon field: shoppers type codes in Bricks' Cart coupon element. It lists and removes the coupons already on the cart.

**Nestable:** no · **In a query loop:** no · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** no

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Applied coupons (`bfbeCoupons`)
- `removeWord` (text) **Remove word**: placeholder Remove. "Remove" unless you set it.
Styling, in the schema file: `direction`, `gap`, `chipBackground`, `chipBorder`, `chipPadding`, `labelTypography`, `amountTypography`, `removeTypography`, `removeBackground`, `removeBorder`, `removePadding`, `removeHover`.

## What it guarantees for accessibility (do not undo)
- The coupons are a list named "Applied coupons".
- Each Remove is a real button named with its code ("Remove: welcome10").
- "Coupon has been removed." is announced once, and the focus moves to the Remove now at the pressed one's place, or else to the coupon field.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<ul id="brxe-{id}" class="brxe-bfbe-applied-coupons bfbe-coupons__applied" aria-label="Applied coupons"
    data-bfbe-coupons-applied="Remove" data-bfbe-coupons-form="bfbe-coupons-remove-form" data-bfbe-shop-need="cart,coupons">
  <li class="bfbe-coupons__coupon">
    <span class="bfbe-coupons__label">Coupon: welcome10</span>
    <span class="bfbe-coupons__amount">-3,40 €</span>
    <button type="submit" class="bfbe-coupons__remove" form="bfbe-coupons-remove-form" name="coupon" value="welcome10"
            aria-label="Remove: welcome10">Remove</button>
  </li>
</ul>
<!-- once per page, in the footer -->
<form id="bfbe-coupons-remove-form" class="bfbe-coupons__form" method="post" hidden>
  <input type="hidden" name="bfbe_shop_act" value="coupon_remove">…</form>
```

- The root is the list itself, a real `ul` named "Applied coupons", a flex column with a 6px gap; Bricks' Style tab draws it. It carries `hidden` while no coupon is applied, and the script sets or clears it from every live answer.
- Each `li` holds WooCommerce's own label, the amount (or "Free shipping coupon" for a free shipping coupon worth nothing) and a Remove button named with the code for screen readers.
- Each Remove is a real submit owned by the footer's form through the `form` attribute, so it posts from inside a cart form too. While a removal runs, the pressed button is `disabled`.
- In the canvas, with no coupon in the cart, a sample chip (`welcome10`, -5) is drawn so the look can be set; the root then carries `data-bfbe-sample` and its button is inert.
- Where controls write: `direction` and `gap` to the root; `chipBackground`, `chipBorder` and `chipPadding` to `.bfbe-coupons__coupon`; `labelTypography` to `.bfbe-coupons__label`; `amountTypography` to `.bfbe-coupons__amount`; `remove*` to `.bfbe-coupons__remove`, `removeHover` to its `:hover` and `:focus-visible`.
- No file of its own: it loads the Coupons feature's stylesheet and script (`shop-coupons`) beside the shop's shared script.

## Wiring to other elements

- **It reads the cart, not another element.** It lists whatever WooCommerce has applied, however it got there: Bricks' Cart coupon, a `?coupon=` link, a coupon that applies itself (Shop page, Cart & checkout, card **Coupons**), BFB Copy to Clipboard's Apply now.
- **With Bricks' Cart coupon** (`woocommerce-cart-coupon`) and its **Works anywhere** (`bfbeShopCouponsAnywhere: "on"`, skill `bfbe-shop-cart-page`), a coupon applied there appears in every Applied Coupons on the page at once, and WooCommerce's words for a Remove show under that form. Place the two side by side, or the list above the totals and the form in the sidebar.
- **Without a coupon form on the page**, a Remove still works; its words are only announced, through the shop's live region.
- **After a Remove** every Applied Coupons on the page redraws, the mini cart refreshes from the fragments, and on the cart or checkout page WooCommerce's own totals refresh (a classic cart's form and totals, a v2 cart whole, or `update_checkout`).
- **The cart's coupons as text**: `{bfbe_cart_coupons}` (the codes, live) and the condition `bfbe_shop_coupon_applied` (skill `bfbe-shop-tags-and-conditions`).
- Give it a class in `_cssClasses` for your own CSS. Nothing targets it by attribute.

## Verified patterns

**A coupon card in the cart's totals column.** From the demo shop's cart template (`bfb-demo-cart`, "Coupon"), colours resolved to hex. Bricks' Cart coupon with Works anywhere applies the code; Applied Coupons under it draws each code as a tinted pill with a white Remove, the amount in green.

```json
{
  "name": "block",
  "settings": { "_rowGap": "12px", "_cssClasses": "coupon-card" },
  "children": [
    { "name": "heading", "settings": { "text": "A coupon?", "tag": "h4" } },
    { "name": "woocommerce-cart-coupon", "settings": { "bfbeShopCouponsAnywhere": "on", "_cssClasses": "coupon-form" } },
    { "name": "bfbe-applied-coupons", "settings": { "removeWord": "Remove", "gap": "8px", "chipBackground": { "hex": "#f0ecff" }, "chipBorder": { "radius": { "top": "999", "right": "999", "bottom": "999", "left": "999" } }, "chipPadding": { "top": "6", "right": "8", "bottom": "6", "left": "14" }, "labelTypography": { "font-size": "14px", "font-weight": "700", "color": { "hex": "#101828" } }, "amountTypography": { "font-size": "14px", "font-weight": "600", "color": { "hex": "#067647" } }, "removeTypography": { "font-size": "13px", "font-weight": "600", "color": { "hex": "#101828" } }, "removeBackground": { "hex": "#ffffff" }, "removeBorder": { "radius": { "top": "999", "right": "999", "bottom": "999", "left": "999" } }, "removePadding": { "top": "4", "right": "10", "bottom": "4", "left": "10" }, "removeHover": { "hex": "#f7f8fa" }, "_cssClasses": "coupon-list" } }
  ]
}
```

**The applied codes in a row, away from the form.** From the fixture page `fixture-shop-p7b` ("Applied coupons, elsewhere"). `direction: "row"` lines the chips up, and **Remove word** `removeWord` renames every button; on a page without a coupon form a Remove's words are announced only.

```json
{ "name": "bfbe-applied-coupons", "settings": { "direction": "row", "removeWord": "Take off", "_cssClasses": "coupon-row" } }
```

## Gotchas

- **It needs the Coupons feature.** With **Coupons** (`shop-coupons`) off on BFB Elements, Elements, the page gets nothing and the canvas says so. <!-- src: plugins/bfb-elements-pro/elements/applied-coupons.php:181-188 -->
- **Bricks' Cart coupon no longer lists coupons.** Its old **Show applied coupons** (`bfbeShopCouponsApplied`) was removed in favour of this element; place an Applied Coupons where the list belongs. <!-- src: docs/SHOP-LABELS-2.0.0.md "BFB Coupons | Show applied coupons | removed" (line 1840) ; plugins/bfb-elements-pro/elements/applied-coupons.php:6 -->
- **Empty means hidden, not absent.** With no coupon the `ul` is printed `hidden`, so it takes no space; a coupon applied later shows it without a reload. <!-- src: plugins/bfb-elements-pro/elements/applied-coupons.php:205-207 ; src/elements/shop-coupons/shop-coupons.js:52-55 -->
- **The canvas chip is a sample.** "Coupon: welcome10" at -5 shows only in the builder while the cart has none, and its Remove does nothing. <!-- src: plugins/bfb-elements-pro/elements/applied-coupons.php:191-195 ; plugins/bfb-elements-pro/includes/shop/class-coupons.php:255-257 -->
- **A redrawn amount is plain text.** The server prints WooCommerce's price markup inside `.bfbe-coupons__amount`; after a live answer the script writes the plain amount there, so style it with `amountTypography`, never `.woocommerce-Price-amount`. <!-- src: plugins/bfb-elements-pro/includes/shop/class-coupons.php:256 ; src/elements/shop-coupons/shop-coupons.js:47 -->
- **A row of chips never wraps.** `direction: "row"` sets the list's `flex-direction` only, and the list has no wrap; keep the column where several coupons can apply, or add `flex-wrap` on its class. <!-- src: src/elements/shop-coupons/shop-coupons.css:9 ; plugins/bfb-elements-pro/elements/applied-coupons.php:62-69 -->
- **A removal by hand sticks for the visit.** A coupon the shopper removes stays off for the session, even one that applies itself; one WooCommerce drops as invalid is not remembered. <!-- src: plugins/bfb-elements-pro/includes/shop/class-coupons.php:365-382 ; plugins/bfb-elements-pro/includes/shop/class-coupons.php:441-458 ; docs/elements/applied-coupons.md "What the visitor gets" -->
- **Without a script, Remove posts to the page.** The footer's form takes the code to WooCommerce's own remove; the visitor comes back to the same page with WooCommerce's notice where the page prints notices. <!-- src: plugins/bfb-elements-pro/includes/shop/class-coupons.php:270-273 ; docs/elements/applied-coupons.md "Without the script" -->

## Never do

- Do not place it on a site with the Coupons feature off.
- Do not set `bfbeShopCouponsApplied` on Bricks' Cart coupon; place this element instead.
- Do not style `.woocommerce-Price-amount` inside the list; use `amountTypography`.
- Do not set `direction: "row"` where several coupons can apply without wrapping the list on its class.
- Do not judge the look by the canvas chip alone; apply a real coupon to check the page.
