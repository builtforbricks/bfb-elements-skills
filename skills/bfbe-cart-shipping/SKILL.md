---
name: bfbe-cart-shipping
description: "Use when placing, wiring or styling BFB Cart Shipping (`bfbe-cart-shipping`): the cart's shipping rates as cards with radios you style, on a cart page or in a cart region laid out yourself, the totals following the choice. Read before writing its settings."
---

# BFB Cart Shipping (`bfbe-cart-shipping`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-cart-shipping.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/cart-shipping/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 0.55 KB, JS 1.15 KB (gzipped), plus shop-live, loaded only on pages that use it.

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Cards (`bfbeCartShip`)
- `radioLook` (select) **Radios**: options: `native` As the browser draws it (default), `custom` Styled with the controls below
Styling, in the schema file: `listDirection`, `cardGap`, `cardBackground`, `cardBorder`, `cardPadding`, `cardShadow`, `hoverBorderColor`, `chosenBackground`, `chosenBorderColor`, `accentColor`, `radioTickSize`, `radioTickBg`, `radioTickBorder`, `radioTickHover`, `radioTickOnLine`, `radioTickMarkColor`, `labelTypography`, `nameTypography`, `contentsTypography`, `noteTypography`.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<form id="brxe-{id}" class="brxe-bfbe-cart-shipping bfbe-cartship" method="post" data-bfbe-tick="dot"
      data-bfbe-shop-need="cart,cartship" data-bfbe-cartship="{signature}" data-bfbe-cartship-words='…'>
  <input type="hidden" name="bfbe_shop_act" value="cart_shipping"> …
  <div class="bfbe-cartship__notices" role="status">… after a no-script post …</div>
  <div class="bfbe-cartship__packages">
    <fieldset class="bfbe-cartship__package" data-bfbe-cartship-package="0">
      <legend class="bfbe-cartship__name bfbe-cartship__sr">Shipment 1</legend>
      <div class="bfbe-cartship__rates">
        <div class="bfbe-cartship__rate">
          <label class="bfbe-cartship__choice">
            <input type="radio" class="bfbe-cartship__radio bfbe-tick" name="rate_0" value="flat_rate:1" data-bfbe-said="…" checked>
            <span class="bfbe-cartship__label">Flat rate: <span class="woocommerce-Price-amount">5,00 €</span></span>
          </label>
          <div class="bfbe-cartship__after">… what a shipping plugin prints under its rate …</div>
        </div>
      </div>
      <p class="bfbe-cartship__contents"><small>… with more than one package …</small></p>
      <p class="bfbe-cartship__note">Shipping to Cluj-Napoca.</p>
    </fieldset>
  </div>
  <button type="submit" class="bfbe-cartship__update">Update</button>
</form>
```

- **The root is the form**, one `fieldset` per package, one `.bfbe-cartship__rate` card per rate with a real radio inside its `label`. With one package the `legend` is visually hidden (`bfbe-cartship__sr`); with more it shows, with the package's contents under its rates.
- **WooCommerce's own words** take the place of the packages when there is no rate to choose ("Enter your address to view shipping options."): a single `p.bfbe-cartship__note`.
- **States.** `bfbe-cartship--js` on the root once the script runs, which hides Update; `aria-busy="true"` on `.bfbe-cartship__packages` while a choice is answered; `hidden` on the root while the cart needs no shipping. The chosen card is `.bfbe-cartship__rate:has(.bfbe-cartship__radio:checked)`.
- **Where controls write.** `listDirection` and `cardGap` write `.bfbe-cartship__rates`; `cardBackground`, `cardBorder`, `cardShadow` the card; `cardPadding` sets `--bfbe-cartship-pad-*`, read by `.bfbe-cartship__choice` and by the sides and bottom of `.bfbe-cartship__after`; `hoverBorderColor` a card not chosen, on hover or with focus inside; `chosen*` the chosen card. `radioLook: "custom"` adds `data-bfbe-tick="dot"` and the `radioTick*` custom properties; `accentColor` sets the radio's `accent-color` and `--bfbe-tick-on`. The four typographies write `__label`, `__name`, `__contents` and `__note`.

## Wiring to other elements

- **Stands alone on the cart**: it reads WooCommerce's packages for the visitor's cart, so nothing targets it and it targets nothing. Place it anywhere on a cart page or in a cart region laid out yourself (`bfbe-shop-cart-page`); it works with Bricks' experimental shop setting off, on Bricks 2.3 and 2.4.
- **What follows a choice.** The live tags `{bfbe_cart_shipping}`, `{bfbe_cart_tax}` and `{bfbe_cart_total}`, Bricks' Mini cart (WooCommerce's fragments), a BFB Live cart region, and on a page with WooCommerce's own cart form, its form and totals (`wc_update_cart`).
- **What it follows.** Every live answer carries the packages, so a quantity changed by BFB Cart Quantity or a coupon reaching free shipping redraws the cards, and a cached page shows the visitor's own rates after load.
- Give it a class in `_cssClasses` for your own CSS; component instances share ids.

## Verified patterns

**Delivery cards in a cart summary.** From the demo shop's "Your own cart" page (`dev/demo/shop/20-pages.php`, "Delivery"). White cards with a 14px corner, the chosen one ringed in the brand's purple, the browser's radio in the same colour, WooCommerce's words small and muted. Trimmed: the demo's colour variables.

```json
{
  "name": "bfbe-cart-shipping",
  "settings": {
    "cardGap": "8px",
    "cardBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "14", "right": "14", "bottom": "14", "left": "14" } },
    "cardBackground": { "hex": "#ffffff" },
    "chosenBorderColor": { "hex": "#6e44ff" },
    "accentColor": { "hex": "#6e44ff" },
    "labelTypography": { "font-size": "15px", "font-weight": "600" },
    "nameTypography": { "font-size": "13px", "font-weight": "700", "text-transform": "uppercase", "letter-spacing": "0.06em" },
    "noteTypography": { "font-size": "13px" },
    "_width": "100%"
  }
}
```

**Rates side by side with the pack's radios.** From the fixture "SHOP Q2: the cart parts with their inner looks set" (`fixture-shop-custom-cart-styled`, `.ship`). `listDirection: "row"` lays the cards in a wrapping row; `radioLook: "custom"` turns on the `radioTick*` controls; the padding is the click area's. The fixture's test colours are replaced with sober ones.

```json
{
  "name": "bfbe-cart-shipping",
  "settings": {
    "listDirection": "row", "cardGap": "12px",
    "cardPadding": { "top": "20", "right": "24", "bottom": "20", "left": "24" },
    "cardShadow": { "values": { "offsetX": "0", "offsetY": "4", "blur": "10", "spread": "0" }, "color": { "hex": "#1018281a" } },
    "hoverBorderColor": { "hex": "#98a2b3" },
    "chosenBackground": { "hex": "#f0ecff" },
    "radioLook": "custom", "radioTickBg": { "hex": "#ffffff" },
    "contentsTypography": { "font-size": "13px", "font-weight": "700" },
    "_cssClasses": "ship"
  }
}
```

## Gotchas

- **Padding is the click area's, not the card's.** `cardPadding` sits on the label and under it on a plugin's extra lines, so a press anywhere in the card, its edges included, chooses the rate; a padding of your own on `.bfbe-cartship__rate` leaves an edge that chooses nothing. <!-- src: src/elements/cart-shipping/cart-shipping.css:8-16 ; plugins/bfb-elements-pro/elements/cart-shipping.php:78-88 -->
- **The styled radio needs its switch.** `radioTickSize`, `radioTickBg`, `radioTickBorder`, `radioTickHover`, `radioTickOnLine` and `radioTickMarkColor` show only with `radioLook: "custom"`; `accentColor` colours the browser's radio and the styled one alike. <!-- src: plugins/bfb-elements-pro/elements/cart-shipping.php:141-149 ; plugins/bfb-elements-pro/elements/cart-shipping.php:188-189 -->
- **Package names show only with more than one package.** With one, the legend is visually hidden, so `nameTypography` and `contentsTypography` change nothing on most carts. <!-- src: plugins/bfb-elements-pro/includes/shop/class-cart-parts.php:531-552 -->
- **No rates, only WooCommerce's words.** Until an address is known (where the shop asks for one), or with no rate for it, the element shows WooCommerce's sentence and no Update; there is no shipping calculator in it. <!-- src: plugins/bfb-elements-pro/includes/shop/class-cart-parts.php:425-433 ; plugins/bfb-elements-pro/elements/cart-shipping.php:253 ; docs/elements/cart-shipping.md "Does a shop need a shipping calculator?" -->
- **A cart that ships nothing hides it.** A downloads-only cart prints the form `hidden`, and the live answer shows it again when a product that ships arrives; the builder says "The cart needs no shipping now". <!-- src: plugins/bfb-elements-pro/elements/cart-shipping.php:218-221 ; plugins/bfb-elements-pro/elements/cart-shipping.php:242-245 -->
- **A choice posts at once.** A click on a card, or an arrow key among the radios, sends the package and the rate id and redraws the cards; the amount is never sent. <!-- src: src/elements/cart-shipping/cart-shipping.js:1-9 ; docs/elements/cart-shipping.md "What the visitor gets" -->
- **Two elements show the same choice.** Every package is in one element; a second on the page repeats the same radios. <!-- src: docs/elements/cart-shipping.md "Limits" -->
- **Without the script it is a form.** Choose, press Update, and the page comes back with the totals counted again and "Shipping: …" above the cards. <!-- src: plugins/bfb-elements-pro/elements/cart-shipping.php:248-253 ; docs/elements/cart-shipping.md "Without the script" -->
- **The canvas is inert.** The radios are disabled in the builder and Update does nothing there. <!-- src: plugins/bfb-elements-pro/includes/shop/class-cart-parts.php:541 ; plugins/bfb-elements-pro/elements/cart-shipping.php:254 -->

## Never do

- Do not pad `.bfbe-cartship__rate` yourself; use `cardPadding`.
- Do not set a `radioTick*` key without `radioLook: "custom"`.
- Do not style package names for a one-package cart and expect to see them.
- Do not place two BFB Cart Shipping elements on one page.
- Do not expect a shipping calculator in it; leave the address to WooCommerce's cart calculator or the checkout.
