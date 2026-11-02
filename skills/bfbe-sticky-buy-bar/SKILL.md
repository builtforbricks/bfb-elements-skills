---
name: bfbe-sticky-buy-bar
description: "Use when a product page needs a sticky add to cart bar that appears once the form scrolls away, filled with Bricks' own elements (BFB Sticky Buy Bar, `bfbe-sticky-buy-bar`). Read before writing its settings."
---

# BFB Sticky Buy Bar (`bfbe-sticky-buy-bar`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-sticky-buy-bar.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/sticky-buy-bar/

## What it is
A bar you fill with your own elements, fixed to the bottom or the top of the window, that appears once shoppers scroll past the product's add to cart form and goes away when the form is back. Its button presses the product's real add to cart button, so Bricks' AJAX add or WooCommerce's form post happens as it would there. It follows the chosen variation, keeps clear of a cookie banner at the same edge, and on a variable product takes the shopper back to the choice they skipped.

**Not for:** Not for pages that are not a product's, or for a product that cannot be bought: it renders nothing there. For a bar with news or offers on every page, use BFB Notification Bar.

**Costs a page:** CSS 0.64 KB, JS 2.83 KB (gzipped), plus shop-live, loaded only on pages that use it.

**Nestable:** yes · **In a query loop:** no · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Nestable: any Bricks element goes inside (blocks, headings, text, images, a form).
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-sticky-buy-bar",
    "settings": {},
    "children": [
        {
            "name": "image",
            "settings": {
                "image": {
                    "useDynamicData": "{featured_image}",
                    "size": "thumbnail"
                },
                "_width": "56px"
            }
        },
        {
            "name": "product-title",
            "settings": {
                "tag": "p"
            }
        },
        {
            "name": "text-basic",
            "settings": {
                "text": "{bfbe_variation_price}"
            }
        },
        {
            "name": "button",
            "settings": {
                "text": "Add to cart",
                "tag": "button",
                "style": "primary",
                "_cssClasses": "bfbe-buybar-go"
            }
        }
    ]
}
```

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Bar (`bfbeBar`)
- `edge` (select) **Edge**: options: `bottom` Bottom (default), `top` Top. Bottom (the default) or Top. At the bottom the bar leaves room for the phone's safe area, so a home indicator never covers the button.
- `buttonClass` (text) **Buy button class**: placeholder bfbe-buybar-go. The child that presses the real add to cart button, bfbe-buybar-go unless you name another; without a child carrying it, the bar's opening button is taken.
- `missingText` (text) **Missing choice words**: placeholder Choose a %s first; dynamic data accepted. What is said when the button is pressed before every attribute is chosen, Choose a %s first, where %s is the attribute's name. It takes dynamic data.
- `clear` (text) **Keep clear of**: placeholder #bfbcc. A fixed element at the same edge the bar must not cover, BFB Cookie Consent's #bfbcc unless you name another selector; a fixed BFB Notification Bar at that edge is kept clear of without being named.
- `wrap` (select) **Wrap**: options: `nowrap` No wrap (default), `wrap` Wrap, `wrap-reverse` Wrap reverse; writes CSS
Styling, in the schema file: `width`, `direction`, `align`, `alignItems`, `gap`, `padding`, `pictureMax`, `choiceTypography`.

### Motion (`bfbeMotion`)
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS
Styling, in the schema file: `duration`, `easingCustom`.

### In the builder (`bfbeBuilder`)
- `builderView` (select) **Show it**: options: `open` In the flow, so you can style it (default), `live` Working, as on the site. In the flow, so you can style it (the default), where the bar sits in the canvas with its children selectable, or Working, as on the site, where it shows and hides as it does outside.

## What it guarantees for accessibility (do not undo)
- While hidden the bar is aria-hidden and inert, so a screen reader does not meet it and the keyboard does not land in it.
- Pressed with a choice still missing, it scrolls to the form, moves the focus to that attribute's swatches or select, and says which choice is missing once through the shop's live region.
- When every choice is made but that combination is not sold, WooCommerce's own words for an unavailable choice are said instead.
- Under reduced motion the bar appears at once and the scroll back to the form jumps rather than glides.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<div id="brxe-{id}" class="brxe-bfbe-sticky-buy-bar bfbe-buybar bfbe-buybar--bottom bfbe-buybar--hidden"
     data-bfbe-buybar="bottom" data-bfbe-buybar-button="bfbe-buybar-go" data-bfbe-buybar-missing="Choose a %s first"
     data-bfbe-buybar-clear="#bfbcc" data-bfbe-buybar-product="123" aria-hidden="true" inert>
  <div class="bfbe-buybar__inner">
    <!-- the children, Bricks' own elements -->
    <img class="brxe-image" src="…" alt="">
    <p class="brxe-product-title">Workshop Apron<span class="bfbe-buybar__choice">Linen, Ink</span></p>
    <div class="brxe-text-basic"><span class="bfbe-shop-follow" data-bfbe-shop-follow="price_html">44,00 €</span></div>
    <button class="brxe-button bricks-button bfbe-buybar-go">Add to cart</button>
  </div>
</div>
```

- The root is `position: fixed` across the window at the chosen edge, `z-index: 9970`, with the tokens' surface, shadow and a 1px line on the side facing the page.
- Hidden, it slides out past its edge: `bfbe-buybar--hidden`, `aria-hidden="true"` and `inert`, then `visibility: hidden` once the motion ends. The script lifts all three when it shows and writes `--bfbe-buybar-offset` (the room taken by a banner it keeps clear of).
- At the bottom edge a strip of `env(safe-area-inset-bottom)` follows the row as the root's `::after`.
- `span.bfbe-buybar__choice` is written by the script into the first Bricks Product title child once a variation is chosen ("Linen, Ink"), hidden again on a reset.
- Where controls write: `width` to `--bfbe-buybar-w` (the inner row's max width, 1240px), `direction`, `wrap`, `align`, `alignItems`, `gap` and `padding` to `.bfbe-buybar__inner`, `pictureMax` to `--bfbe-buybar-pic` (an image child's max height, 56px), `choiceTypography` to `.bfbe-buybar__choice`, the Motion group to `--bfbe-duration` and `--bfbe-ease`. Bricks' Style tab writes the root: background, border, shadow, padding.
- In the canvas with **Show it** `builderView` unset (`open`), the root takes `bfbe-buybar--canvas` and sits in the flow with a dashed outline; `live` writes `data-bfbe-live="1"` and lets the script run there.

## Wiring to other elements

- **The product's own Add to cart form.** The bar watches the `form.cart` of its product (by `data-product_id` or the `add-to-cart` value), else the first `form.cart` on the page outside the bar, and shows while no part of it is on screen. Place it in a product template that has Bricks' Add to cart.
- **The buy button, by class.** **Buy button class** `buttonClass` names the child that presses the form's real `.single_add_to_cart_button` (`bfbe-buybar-go` unless set): put that class in the child's `_cssClasses`. Without a child carrying it, the first `button`, `.brxe-button` or `[role="button"]` inside is taken.
- **The price** follows the choice where it is the tag `{bfbe_variation_price}` (Variation data feature); see `bfbe-shop-tags-and-conditions`.
- **The picture** is the first `img` in the bar; it takes the variation's own image and gets the product's back on a reset.
- **Keep clear of** `clear` is a selector for a fixed element at the same edge, `#bfbcc` (BFB Cookie Consent) unless set. A fixed BFB Notification Bar at the same edge (`.bfbe-nbar--fixed.bfbe-nbar--bottom` or `--top`) is cleared without being named.
- **Announcements** go through the shop's shared live region (`bfbe-shop-live`), loaded with the bar.
- See `bfbe-shop` for the shop's switches and `bfbe-shop-add-to-cart` for the form's own settings.

## Verified patterns

**The inserted bar on a product page.** From the template "Shop P5a: single product" (`bfbe-shop-product-p5a`): the product's summary with Bricks' Add to cart, and the bar after it holding the four children the builder inserts. The bar shows once the form scrolls away, clears a fixed `#bfbcc` banner and presses the real add button. Trimmed: the template's gallery, long description, related products and the stand-in banner.

```json
{
  "name": "section",
  "settings": {},
  "children": [
    {
      "name": "block",
      "settings": { "_rowGap": "16px" },
      "children": [
        { "name": "product-title", "settings": { "tag": "h1" } },
        { "name": "product-price", "settings": {} },
        { "name": "product-add-to-cart", "settings": {} }
      ]
    },
    {
      "name": "bfbe-sticky-buy-bar",
      "settings": {},
      "children": [
        { "name": "image", "settings": { "image": { "useDynamicData": "{featured_image}", "size": "thumbnail" }, "_width": "56px" } },
        { "name": "product-title", "settings": { "tag": "p" } },
        { "name": "text-basic", "settings": { "text": "{bfbe_variation_price}" } },
        { "name": "button", "settings": { "text": "Add to cart", "tag": "button", "style": "primary", "_cssClasses": "bfbe-buybar-go" } }
      ]
    }
  ]
}
```

**A styled bar that drops the price on a phone.** From the 2.4 site's demo shop, template "Fernhouse: product page" (`bfb-demo-product`), the bar at the end of the template. A white bar with a soft upward shadow and a top line, the name taking the free room, the price hidden from the landscape phone breakpoint down, a purple pill button. Shown with the summary's Add to cart it watches; trimmed: the demo's colour variables and the template's other sections.

```json
{
  "name": "section",
  "settings": {},
  "children": [
    { "name": "product-add-to-cart", "settings": {} },
    {
      "name": "bfbe-sticky-buy-bar",
      "settings": {
        "edge": "bottom",
        "width": "1240",
        "gap": "16",
        "padding": { "top": "12", "right": "20", "bottom": "12", "left": "20" },
        "_background": { "color": { "hex": "#ffffff" } },
        "_boxShadow": { "values": { "offsetX": 0, "offsetY": -10, "blur": 40, "spread": -10 }, "color": { "rgb": "rgba(16, 24, 40, 0.16)" } },
        "_border": { "width": { "top": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" } }
      },
      "children": [
        { "name": "image", "settings": { "image": { "useDynamicData": "{featured_image}", "size": "thumbnail" }, "_width": "56px" } },
        { "name": "product-title", "settings": { "tag": "p", "_typography": { "font-size": "15px", "font-weight": "700" }, "_flexGrow": "1" } },
        { "name": "text-basic", "settings": { "text": "{bfbe_variation_price}", "_typography": { "font-size": "18px", "font-weight": "800" }, "_display:mobile_landscape": "none" } },
        { "name": "button", "settings": { "text": "Add to cart", "tag": "button", "_cssClasses": "bfbe-buybar-go", "_background": { "color": { "hex": "#6e44ff" } }, "_typography": { "font-size": "15px", "font-weight": "700", "color": { "hex": "#ffffff" } }, "_padding": { "top": "13", "right": "26", "bottom": "13", "left": "26" } } }
      ]
    }
  ]
}
```

## Gotchas

- **Nothing prints where nothing can be bought.** On a page that is not a product's, or for a product out of stock, not purchasable or under a catalogue rule, the bar renders nothing and loads no file. <!-- src: plugins/bfb-elements-pro/elements/sticky-buy-bar.php:240-263 -->
- **No form, no bar.** It needs a `form.cart` on the page and a browser with `IntersectionObserver`; without them, or without JavaScript, it stays hidden for good. With no Add to cart of its product it follows the first `form.cart` it finds, which may be a card's. <!-- src: src/elements/sticky-buy-bar/sticky-buy-bar.js:18-23 ; src/elements/sticky-buy-bar/sticky-buy-bar.js:50-51 ; plugins/bfb-elements-pro/elements/sticky-buy-bar.php:283-285 -->
- **It shows whenever the form is off screen, above or below.** A form that starts below the first screen, as on a phone under a tall gallery, brings the bar in at once on load. <!-- src: src/elements/sticky-buy-bar/sticky-buy-bar.js:81-82 ; docs/elements/sticky-buy-bar.md "What the visitor gets" -->
- **The button's click is taken.** The bar cancels the child's click and presses the form's add button, so a link on that child never navigates. Use a Bricks Button with `tag: "button"` and no link, as the inserted child does. <!-- src: src/elements/sticky-buy-bar/sticky-buy-bar.js:132-158 ; plugins/bfb-elements-pro/elements/sticky-buy-bar.php:233 -->
- **A missing choice posts nothing.** On a variable product with a choice open, the page scrolls to the form, the first open choice's swatches or select take the focus, and the bar says **Missing choice words** `missingText` with `%s` as the attribute's label, lower-cased unless it is mixed case (GSM). An unsold combination says WooCommerce's own words instead. <!-- src: src/elements/sticky-buy-bar/sticky-buy-bar.js:25-31 ; src/elements/sticky-buy-bar/sticky-buy-bar.js:137-153 -->
- **Following the choice needs the right children and the Variation data switch.** The price follows only as `{bfbe_variation_price}` (Bricks' `{woo_product_price}` stays the parent's), the choice words appear only under Bricks' Product title, and the event comes from the Variation data follower, loaded only with that switch on. <!-- src: src/elements/sticky-buy-bar/sticky-buy-bar.js:103-128 ; plugins/bfb-elements-pro/includes/shop/class-variation.php:37-40 -->
- **Two paddings.** **Padding** `padding` sits around the children inside; Bricks' Style tab padding writes the root and adds to the safe-area strip at the bottom, never replacing it. <!-- src: plugins/bfb-elements-pro/elements/sticky-buy-bar.php:137-143 ; src/elements/sticky-buy-bar/sticky-buy-bar.css:19-21 -->
- **Keep clear of measures fixed elements only.** It reads elements with `position: fixed` touching the same edge, shown and with a height; a banner in the flow is not measured, and a selector the browser cannot read falls back to the notification bar alone. <!-- src: src/elements/sticky-buy-bar/sticky-buy-bar.js:65-79 -->
- **A transformed ancestor traps it.** As any `position: fixed` element, it fixes to an ancestor that carries a `transform`, `filter` or `backdrop-filter` instead of the window; place it outside such a container. <!-- src: src/elements/sticky-buy-bar/sticky-buy-bar.css:10 -->
- **The canvas shows a layout.** Unset `builderView` lays the bar in the flow with the script idle; `live` shows and hides it in the canvas as the form scrolls. The setting changes nothing on the site. <!-- src: plugins/bfb-elements-pro/elements/sticky-buy-bar.php:278-289 ; src/elements/sticky-buy-bar/sticky-buy-bar.js:48-49 -->
- **Reduced motion drops the slide.** The tokens zero the duration, so the bar appears and goes at once. <!-- src: src/elements/sticky-buy-bar/sticky-buy-bar.css:1-6 -->

## Never do

- Do not place it on a page or template without Bricks' Add to cart for its product.
- Do not give the buy button child a link; use a Bricks Button with `tag: "button"` and the `buttonClass` class.
- Do not set `buttonClass` without putting that class on a child in `_cssClasses`.
- Do not use `{woo_product_price}` for a price that should follow the choice; use `{bfbe_variation_price}`.
- Do not put it inside a container with a `transform`, `filter` or `backdrop-filter`.
- Do not point `clear` at an element that is not `position: fixed` at the bar's edge.
