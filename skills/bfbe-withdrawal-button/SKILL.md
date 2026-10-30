---
name: bfbe-withdrawal-button
description: "Use when linking to WooCommerce's online withdrawal page with BFB Withdrawal Button (`bfbe-withdrawal-button`): on the thank-you page or an account order with the order number filled in, or as a plain link in a footer. Read before writing its settings."
---

# BFB Withdrawal Button (`bfbe-withdrawal-button`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-withdrawal-button.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/withdrawal-button/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 0.24 KB, JS none (gzipped), no dependencies, loaded only on pages that use it.

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Button (`bfbeButton`)
- `text` (text) **Text**: placeholder Withdraw from this order; dynamic data accepted
- `look` (select) **Look**: options: `button` Button (default), `link` Link
- `style` (select) **Style**: options: `primary` Primary, `secondary` Secondary, `light` Light, `dark` Dark, `muted` Muted, `info` Info, `success` Success, `warning` Warning, `danger` Danger; only when `look` is not `link`
- `size` (select) **Size**: options: `sm` Small, `md` Medium (default), `lg` Large, `xl` Extra large; only when `look` is not `link`
- `outline` (checkbox) **Outline**: only when `look` is not `link`
- `newTab` (checkbox) **Open in a new tab**
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<a id="brxe-{id}" class="brxe-bfbe-withdrawal-button bfbe-withdraw bfbe-withdraw--button bricks-button md outline bricks-color-dark"
   href="https://shop.example/my-account/withdraw-order/?bfbe_order=1042" data-bfbe-order="1042">Withdraw from this order</a>
```

- One `a`, the root, and nothing else. `bfbe-withdraw--button` or `bfbe-withdraw--link` follows **Look** (`look`).
- The button look adds Bricks' own `bricks-button`, the **Size** class (`sm`, `md`, `lg`, `xl`) only when `size` is set, `outline` with **Outline**, and the **Style** colour class: `bricks-color-{style}` with Outline, `bricks-background-{style}` without. `style` unset adds no colour class, so the theme's plain button look applies.
- The link look carries none of these: it is underlined (2px on hover) in the surrounding text's colour.
- `href` is WooCommerce's withdrawal page; with an order in hand it carries `?bfbe_order=<number>` and the root takes `data-bfbe-order`. **Open in a new tab** (`newTab`) adds `target="_blank"` and `rel="noopener"`.
- `:focus-visible` draws the shop's focus outline. Bricks' Style tab (typography, background, border) writes the root itself. No script.

## Wiring to other elements

- **The order comes from the page, not from a setting.** On WooCommerce's thank-you page (the order key in the address) and on the account's order page (for its own customer) the link carries that order's number; WooCommerce's withdrawal form then opens with its order-number field filled.
- **With BFB Elements Pro** the order is resolved as the shop's order tags resolve it (`bfbe-shop-tags-and-conditions`): also inside any query loop whose row is an order (BFB Shop customer orders, `bfbeShopOrders`, or Bricks' own orders loop), on the order-pay page with its key, and on a page where BFB Order Status has just looked an order up.
- **Elsewhere** (a footer, a help page) it links to the page with no number, and the visitor types it. The Pro tag `{bfbe_order_withdrawal_url}` prints that same plain address for any link that takes dynamic data.
- Nothing points at the element; give it a class in `_cssClasses` for your own CSS.

## Verified patterns

**The button beside an order's facts on the thank-you page.** From the 2.4 site's demo shop, template "Fernhouse: thank you" (`bfb-demo-thankyou`), in a row with BFB Add to Calendar. Bricks' dark outline button at medium size; the order number rides the link by itself. Trimmed: the demo's border and typography.

```json
{
  "name": "bfbe-withdrawal-button",
  "settings": { "look": "button", "text": "Withdraw from this order", "style": "dark", "outline": true, "size": "md", "_cssClasses": "thanks-withdraw" }
}
```

**A plain link in a footer.** From the demo shop's footer template ("Fernhouse: footer", `bfb-demo-footer`) and the order fixture (`fixture-shop-p8`, "Withdrawal button (link)"). No order here, so the link opens the empty form; the words say what the visitor will do there.

```json
{
  "name": "bfbe-withdrawal-button",
  "settings": { "look": "link", "text": "Changed your mind? Withdraw from an order", "_cssClasses": "footer-withdraw" }
}
```

## Gotchas

- **Nothing without WooCommerce's withdrawal feature.** Unless **Order withdrawal** is on (WooCommerce, Settings, Advanced, Features; WooCommerce 11.1 and later), the page gets nothing and the canvas says the feature is off. Nothing of ours stands in for the missing page. <!-- src: plugins/bfb-elements/elements/withdrawal-button.php:130-139 --> <!-- src: plugins/bfb-elements/includes/shop/class-withdrawal.php:36-41 -->
- **The free plugin knows two pages.** Without Pro the number is filled in only on the thank-you page and the account's order page; in a loop of orders it needs Pro's resolver. <!-- src: plugins/bfb-elements/includes/shop/class-withdrawal.php:54-81 --> <!-- src: docs/elements/withdrawal-button.md "Where it sends the visitor" -->
- **Guests on Bricks 2.3.10 meet a login form.** Bricks' classic Account page element shows a guest the login form at the withdrawal address; on Bricks 2.4.2 a guest reaches WooCommerce's form. A 2.3 shop that wants guests to reach it can use WooCommerce's `[woocommerce_my_account]` shortcode on the account page instead of the Bricks element. <!-- src: docs/elements/withdrawal-button.md "Measured on Bricks 2.3.10" --> <!-- src: dev/shop/p8-probe.mjs:209-210 -->
- **The address follows WooCommerce's endpoint.** It is `/my-account/withdraw-order/` unless the endpoint was renamed in WooCommerce, Settings, Advanced, Account endpoints; never write it by hand into a Bricks link. <!-- src: plugins/bfb-elements/includes/shop/class-withdrawal.php:44-52 -->
- **Only an order number is filled in.** The form takes the address's value only when it is letters, digits and `- _ / .`, 40 characters at most, and only into an empty field; the visitor still types name and email. <!-- src: plugins/bfb-elements/includes/shop/class-withdrawal.php:92-106 -->
- **Style, Size and Outline are for the button look.** All three show only with `look` not `link`; the link look ignores them and takes the text's colour. <!-- src: plugins/bfb-elements/elements/withdrawal-button.php:89 ; plugins/bfb-elements/elements/withdrawal-button.php:105 ; plugins/bfb-elements/elements/withdrawal-button.php:113 --> <!-- src: src/elements/withdrawal-button/withdrawal-button.css:3 -->
- **No Style, no colour.** `style` unset adds only `bricks-button` and the size class, so the theme style's plain button look applies; set `style` (with or without `outline`) for one of Bricks' colours. <!-- src: plugins/bfb-elements/elements/withdrawal-button.php:145 ; plugins/bfb-elements/elements/withdrawal-button.php:150-161 -->
- **A footer and a thank-you page differ by themselves.** The same element, or a template or component holding it, links with the number where an order is in hand and without it elsewhere; no setting changes that. <!-- src: plugins/bfb-elements/elements/withdrawal-button.php:141-143 ; plugins/bfb-elements/includes/shop/class-withdrawal.php:58-81 -->
- **The element is a link, never the process.** WooCommerce's form handles the withdrawal, its review step, notices and acknowledgment email; WooCommerce's own emails are not Bricks templates, so paste the page's address into the email text there. <!-- src: docs/elements/withdrawal-button.md "Limits" ; docs/elements/withdrawal-button.md "Footers and emails" -->

## Never do

- Do not build the withdrawal link with a Bricks Button and a typed address; the element follows the endpoint and the order.
- Do not set `style`, `size` or `outline` with `look: "link"`.
- Do not expect the order number on a page without an order in hand (a footer, a help page); it links to the empty form there.
- Do not rely on the number inside an orders loop without BFB Elements Pro.
- Do not place it where the shop has not switched on WooCommerce's Order withdrawal feature and expect a button.
