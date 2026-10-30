---
name: bfbe-payment-icons
description: "Use when showing the payment methods a shop accepts as a row of icons with BFB Payment Icons (`bfbe-payment-icons`): at the checkout, under the cart totals, in a footer, every method switched on in WooCommerce or a chosen few, with or without names. Read before writing its settings."
---

# BFB Payment Icons (`bfbe-payment-icons`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-payment-icons.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/payment-icons/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 0.41 KB, JS none (gzipped), no dependencies, loaded only on pages that use it.

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Icons (`bfbeIcons`)
- `gateways` (select) **Show**: options: `bacs` Direct bank transfer, `cod` Cash on delivery
- `titles` (checkbox) **Names**
Styling, in the schema file: `justify`, `gap`, `size`, `color`, `chipBackground`, `chipBorder`, `chipShadow`, `chipPadding`, `nameTypography`, `nameGap`.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<ul id="brxe-{id}" class="brxe-bfbe-payment-icons bfbe-pay bfbe-pay--named" aria-label="Payment methods">
  <li class="bfbe-pay__chip" data-bfbe-gateway="cod">
    <svg class="bfbe-pay__mark bfbe-pay__mark--cash" viewBox="0 0 48 44" aria-hidden="true">…</svg>
    <span class="bfbe-pay__name">Cash on delivery</span>
  </li>
  <li class="bfbe-pay__chip" data-bfbe-gateway="stripe">
    <img class="bfbe-pay__img" src="…" alt="" aria-hidden="true" loading="lazy" decoding="async">
    <span class="bfbe-pay__name">Credit card</span>
  </li>
</ul>
```

- The root is a real `ul`, a wrapping flex row; `bfbe-pay--named` only with **Names** (`titles`). One `li.bfbe-pay__chip` per gateway switched on in WooCommerce, in WooCommerce's order, `data-bfbe-gateway` holding the gateway id.
- A gateway with its own icon prints that markup with `img.bfbe-pay__img` added; any other gets an inline `svg.bfbe-pay__mark--{kind}`: `card`, `bank`, `cash`, `cheque`, `paypal`, `apple`, `google`, `klarna`, `ideal`, `bancontact`, `sepa`. An unknown id gets `card`.
- Without names, each mark is `role="img"` with the gateway's title as `aria-label`, and an own image keeps its `alt` or takes the title. With names, marks and images are `aria-hidden="true"` with `alt=""`, and `span.bfbe-pay__name` carries the title.
- Where controls write: **Height** `size` sets `--bfbe-pay-size` (24px) on the root, the height of marks and images; **Gap** `gap` sets `--bfbe-pay-gap` (12px); **Alignment** `justify` the root's `justify-content`; **Colour** `color` writes `.bfbe-pay__mark`; `chipBackground`, `chipBorder`, `chipShadow`, `chipPadding` write `.bfbe-pay__chip`; `nameTypography` writes `.bfbe-pay__name`; the second **Gap** `nameGap` the chip's gap under `.bfbe-pay--named`.
- No script. One stylesheet, loaded only on pages with the element.

## Wiring to other elements

Stands alone; nothing targets it and it targets nothing. It reads WooCommerce's gateway list each time the page renders (WooCommerce, Settings, Payments), so switching a method off removes its chip with no edit. Place it beside the checkout's payment step, under the cart totals or in a footer; give it a class in `_cssClasses` for your own CSS. Start at `bfbe-shop` for the rest of the shop.

## Verified patterns

**Named chips beside the checkout's payment step.** From the 2.4 site's demo shop, templates "Fernhouse: checkout, in three steps" (`bfb-demo-checkout`) and "Fernhouse: cart" (`bfb-demo-cart`), which share it. Every method that is on, each with its name in a pill-shaped chip. Trimmed: the demo's colour variables, kept as their hex values.

```json
{
  "name": "bfbe-payment-icons",
  "settings": {
    "titles": true,
    "size": "20px",
    "gap": "8px",
    "color": { "hex": "#101828" },
    "chipBackground": { "color": { "hex": "#f7f8fa" } },
    "chipBorder": { "width": { "top": "0", "right": "0", "bottom": "0", "left": "0" }, "style": "solid", "radius": { "top": "999", "right": "999", "bottom": "999", "left": "999" } },
    "chipPadding": { "top": "7", "right": "12", "bottom": "7", "left": "12" },
    "nameTypography": { "font-size": "13px", "font-weight": "600", "color": { "hex": "#101828" } },
    "_cssClasses": "pay-row"
  }
}
```

**One method picked, named and larger.** From the order fixture (`fixture-shop-p8`, "Payment icons (cash on delivery, named)"). **Show** `gateways` limits the row to Cash on delivery; its mark becomes decoration once the name prints. The ids are the target site's: read the `gateways` options there first.

```json
{
  "name": "bfbe-payment-icons",
  "settings": {
    "gateways": [ "cod" ],
    "titles": true,
    "size": "32px",
    "chipShadow": { "values": { "offsetX": "0", "offsetY": "2", "blur": "6", "spread": "0" }, "color": { "hex": "#102030" } },
    "_cssClasses": "pay-cod"
  }
}
```

## Gotchas

- **The row shows what is switched on, not what this cart can use.** A method WooCommerce offers only above a cart total still shows, as long as it is switched on. <!-- src: docs/elements/payment-icons.md "Limits" --> <!-- src: plugins/bfb-elements-pro/elements/payment-icons.php:182-193 -->
- **Gateway ids belong to the site.** The `gateways` options are the ids switched on where the panel opens; a picked id that is later switched off simply drops out, and when none of the picked ones is on the page prints nothing. <!-- src: plugins/bfb-elements-pro/elements/payment-icons.php:271-277 -->
- **Nothing on the page, a notice in the builder.** With no gateway on (or none of the picked), the canvas says "No payment method is on in WooCommerce." or "None of the chosen payment methods is on."; the page gets no markup at all. <!-- src: plugins/bfb-elements-pro/elements/payment-icons.php:274-277 --> <!-- src: plugins/bfb-elements/includes/abstract-element.php:549-557 -->
- **Colour reaches only the marks of ours.** `color` writes `.bfbe-pay__mark`, drawn in `currentColor`; a gateway's own image keeps its own colours. <!-- src: plugins/bfb-elements-pro/elements/payment-icons.php:107-113 --> <!-- src: src/elements/payment-icons/payment-icons.css:4-5 -->
- **The marks are small glyphs, not official logos.** A shop that must show a brand's own mark relies on the gateway's icon (used first when the gateway sets one) or a Bricks Image. <!-- src: docs/elements/payment-icons.md "Limits" --> <!-- src: plugins/bfb-elements-pro/elements/payment-icons.php:291-293 -->
- **Wide logos are capped.** Marks and images take the height in `size` and stop at 2.4 times that width, so a long wordmark from a gateway shrinks to fit rather than widening its chip. <!-- src: src/elements/payment-icons/payment-icons.css:4 -->
- **Names change what assistive tech hears.** With `titles` on, every mark and image is hidden and the printed name says the method once; without, each mark is named by the gateway's title. <!-- src: plugins/bfb-elements-pro/elements/payment-icons.php:294-296 --> <!-- src: dev/shop/p8-probe.mjs:79 -->
- **The name controls need Names.** **Typography** `nameTypography` and the second **Gap** `nameGap` show only with `titles` set. <!-- src: plugins/bfb-elements-pro/elements/payment-icons.php:147 ; plugins/bfb-elements-pro/elements/payment-icons.php:158 -->
- **A cached page keeps its row.** The list is read on the server at render, so a page served from a cache shows the methods that were on when it was cached, until the cache is cleared. <!-- src: plugins/bfb-elements-pro/elements/payment-icons.php:268-272 -->

## Never do

- Do not copy `gateways` ids from another site; read the target site's options, or leave it empty for every method.
- Do not present the row as the methods this cart accepts; it lists what is switched on.
- Do not set `nameTypography` or `nameGap` without `titles`.
- Do not expect `color` to recolour a gateway's own image; it reaches the marks of ours only.
- Do not add your own text alternative or label around the chips; the element names every method once.
