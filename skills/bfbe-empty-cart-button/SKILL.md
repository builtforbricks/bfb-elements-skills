---
name: bfbe-empty-cart-button
description: "Use when placing, wiring or styling BFB Empty Cart Button (`bfbe-empty-cart-button`): a button that empties the cart after asking, on a cart page, in a mini cart popup or a header; hide it while the cart is empty, style its question box. Read before writing its settings."
---

# BFB Empty Cart Button (`bfbe-empty-cart-button`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-empty-cart-button.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/empty-cart-button/

## What it is
A button that empties the visitor's cart after asking. It is a real form with a submit button, so it works before any script runs; the script adds the question in the browser's own modal dialog. The cart is emptied on the server, and the button can hide itself while there is nothing to empty.

**Not for:** It empties the whole cart; to take out one line, use BFB Cart Quantity's Remove or WooCommerce's own remove link. Without scripts no question can be asked, so the post empties the cart straight away.

**Costs a page:** CSS 0.71 KB, JS 0.84 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** no · **In a query loop:** no · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** no

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Button (`bfbeButton`)
- `text` (text) **Text**: placeholder Empty the cart; dynamic data accepted. "Empty the cart" unless you set it; dynamic data works.
- `style` (select) **Style**: options: `primary` Primary, `secondary` Secondary, `light` Light, `dark` Dark, `muted` Muted, `info` Info, `success` Success, `warning` Warning, `danger` Danger
- `size` (select) **Size**: options: `sm` Small, `md` Medium (default), `lg` Large, `xl` Extra large
- `outline` (checkbox) **Outline**
- `icon` (icon) **Icon**. Before the text. None unless set.
- `hideEmpty` (checkbox) **Hide when empty**. Off unless you tick it. On, the button is not shown while the cart is empty, follows the live answer on cached pages, and goes once the cart has been emptied.
Styling, in the schema file: `iconSize`, `iconGap`.

### Confirm (`bfbeConfirm`)
- `question` (text) **Question**: placeholder Empty your cart?; dynamic data accepted. The dialog's name, "Empty your cart?" unless you set it; dynamic data works.
- `confirmText` (text) **Yes button**: placeholder Yes, empty it
- `cancelText` (text) **Cancel button**: placeholder Keep my cart

### Question box (`bfbeDialog`)
- `builderPreview` (checkbox) **Preview in the builder**. Draws the dialog open below the button while you style it.
Styling, in the schema file: `boxTypography`, `boxBackground`, `boxBorder`, `boxPadding`, `boxWidth`, `boxShadow`, `backdrop`, `questionTypography`, `btnTypography`, `btnPadding`, `btnBorder`, `btnGap`, `btnJustify`, `okBackground`, `okColor`, `okHoverBackground`, `okHoverColor`, `okHoverBorder`, `cancelBackground`, `cancelColor`, `cancelHoverBackground`, `cancelHoverColor`, `cancelHoverBorder`.

## What it guarantees for accessibility (do not undo)
- The question is a modal dialog of the browser's own, named by the question. The focus lands on Cancel; Escape and a click outside keep the cart, and the focus goes back to the button when it closes.
- "Your cart is now empty." is said once, politely.
- When Hide when empty takes the button away, the focus goes to the place around it (a mini cart's panel, or the page's main area) rather than the top of the page.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<form id="brxe-{id}" class="brxe-bfbe-empty-cart-button bfbe-emptycart bricks-button sm outline bricks-color-dark" method="post"
      data-bfbe-shop-need="cart" data-bfbe-emptycart-hide="1" data-bfbe-emptycart-done="Your cart is now empty.">
  <input type="hidden" name="bfbe_shop_act" value="cart_empty"> …
  <button type="submit" class="bfbe-emptycart__button"><i class="bfbe-emptycart__icon …"></i><span class="bfbe-emptycart__text">Empty the cart</span></button>
  <dialog class="bfbe-emptycart__confirm" aria-labelledby="{uid}">
    <p class="bfbe-emptycart__question" id="{uid}">Empty your cart?</p>
    <div class="bfbe-emptycart__actions">
      <button type="button" class="bfbe-emptycart__cancel bricks-button outline">Keep my cart</button>
      <button type="button" class="bfbe-emptycart__ok bricks-button bricks-background-primary">Yes, empty it</button>
    </div>
  </dialog>
</form>
```

- **The root is the form, and it is the button.** It wears Bricks' `bricks-button` classes: **Size** adds `sm` to `xl`, **Style** adds `bricks-background-{style}`, or `bricks-color-{style}` with **Outline**; no Style, no colour class. The submit button inside is transparent, inherits the look, and its `::after` covers the root, padding included.
- **The icon** (`icon`) prints before the text, inside the button; `iconSize` sets `--bfbe-emptycart-icon` on the root, `iconGap` the button's `gap`.
- **The question** is a real `<dialog>` inside the form, opened with `showModal()`; `[open]` is its state. Box controls write `.bfbe-emptycart__confirm`, `backdrop` its `::backdrop`, `boxWidth` sets `--bfbe-emptycart-w`, `question*` the `p`, `btn*` both buttons, `ok*` and `cancel*` each one (hover keys also on `:focus-visible`).
- **States.** **Hide when empty** (`hideEmpty`) adds `data-bfbe-emptycart-hide`; with an empty cart the root takes `hidden` and `bfbe-emptycart--empty`, set again from every live answer. `.bfbe-emptycart__ok[disabled]` while the request runs. In the builder the submit is `type="button"`, and **Preview in the builder** (`builderPreview`) draws the dialog `open` with `data-bfbe-preview`, below the button.

## Wiring to other elements

- **Stands alone.** It needs no target: it empties the visitor's own cart through the shop's `cart_empty` action and nothing points at it. Start at `bfbe-shop` for the shared script.
- **What follows it.** The answer carries WooCommerce's fragments, so Bricks' Mini cart refreshes; a BFB Live cart region (`bfbeLiveCart`, skill `bfbe-shop-cart-page`) is drawn again from the next live answer; the sentence goes to the shop's live region `#bfbe-shop-status`.
- **On a cart or checkout page** (a page holding `.woocommerce-cart-form`, Bricks' Cart items, Cart totals, a v2 cart or `.woocommerce-checkout`) the page reloads after emptying, so WooCommerce's own empty-cart content shows.
- **Where to place it.** Beside Bricks' Cart items in a title row, at the foot of a cart region in a Bricks popup, or in a header. Give it a class in `_cssClasses` for your own CSS; nothing targets it by class or id.

## Verified patterns

**A title row on a cart page.** From the demo shop's cart template (`dev/demo/shop/15-templates-buy.php`, "Title row"). A small dark outline pill beside the page heading, hidden while the cart is empty, the Style tab's own border and typography drawing the pill. Trimmed: the demo's colour variables.

```json
{
  "name": "block",
  "settings": { "_direction": "row", "_justifyContent": "space-between", "_alignItems": "flex-end", "_flexWrap": "wrap", "_rowGap": "12px" },
  "children": [
    { "name": "heading", "settings": { "text": "Your cart", "tag": "h1" } },
    { "name": "bfbe-empty-cart-button", "settings": {
      "text": "Empty the cart", "outline": true, "style": "dark", "size": "sm", "hideEmpty": true,
      "question": "Empty your cart?", "confirmText": "Yes, empty it", "cancelText": "Keep my cart",
      "_border": { "radius": { "top": "999", "right": "999", "bottom": "999", "left": "999" } },
      "_typography": { "font-size": "14px", "font-weight": "700" }
    } }
  ]
}
```

**An icon button with its question box styled.** From the fixture "SHOP P7a" (`fixture-shop-p7a`, `.ec-styled`). A trash icon before the word, the box's own type lighter and larger, more room between its buttons, and both buttons' hover look (also their keyboard focus look). The fixture's test colours are replaced with sober ones.

```json
{
  "name": "bfbe-empty-cart-button",
  "settings": {
    "text": "Empty", "style": "primary",
    "icon": { "library": "themify", "icon": "ti-trash" }, "iconSize": "18px", "iconGap": "10px",
    "boxTypography": { "font-size": "19px", "font-weight": "300" },
    "btnGap": "20px",
    "okHoverColor": { "hex": "#ffffff" },
    "okHoverBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#101828" } },
    "cancelHoverColor": { "hex": "#101828" },
    "cancelHoverBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#101828" } },
    "_cssClasses": "ec-styled"
  }
}
```

## Gotchas

- **Style the root, not a part.** The form is the button: Bricks' universal `_padding`, `_background`, `_border` and `_typography` on the Style tab draw it, and the theme style's button look reaches it through `bricks-button`. <!-- src: plugins/bfb-elements-pro/elements/empty-cart-button.php:381-391 ; src/elements/empty-cart-button/empty-cart-button.css:3-24 -->
- **The icon is always before the text.** There is no position control; `iconSize` and `iconGap` show only with `icon` set. <!-- src: plugins/bfb-elements-pro/elements/empty-cart-button.php:104-134 ; plugins/bfb-elements-pro/elements/empty-cart-button.php:410-412 -->
- **The question box keeps its own type.** It sits inside the button's form but resets to 16px, regular, no capitals, in the page's face, whatever the button's typography; change it with `boxTypography` and `questionTypography`. <!-- src: src/elements/empty-cart-button/empty-cart-button.css:27-50 ; docs/elements/empty-cart-button.md "Question box" -->
- **The box is a light card on any page.** White with dark ink by default, so on a dark site set `boxBackground` and a colour in `boxTypography`. It is never wider than the screen less 32px, whatever `boxWidth` says. <!-- src: src/elements/empty-cart-button/empty-cart-button.css:30-38 -->
- **Its two buttons wear Bricks' button classes.** Yes is `bricks-background-primary` and Cancel `outline`, so the theme style's Primary and outline looks reach them until `ok*` and `cancel*` are set. <!-- src: plugins/bfb-elements-pro/elements/empty-cart-button.php:420-422 -->
- **Hide when empty is decided twice.** The server prints `hidden` for an empty cart, and every live answer sets it again, so a cached page is right after load. The builder always shows the button. <!-- src: plugins/bfb-elements-pro/elements/empty-cart-button.php:395-401 ; src/elements/empty-cart-button/empty-cart-button.js:17-21 -->
- **The canvas never opens the dialog.** The button is inert in the builder; tick `builderPreview` to style the box, drawn open below the button. `backdrop` does not show in that preview. <!-- src: plugins/bfb-elements-pro/elements/empty-cart-button.php:413-415 ; plugins/bfb-elements-pro/elements/empty-cart-button.php:240 -->
- **A cart page reloads after emptying.** On a page with WooCommerce's cart form, Bricks' Cart items, Cart totals, a v2 cart or the checkout, the page reloads 400ms after the answer; elsewhere nothing reloads. <!-- src: src/elements/empty-cart-button/empty-cart-button.js:22-24 ; src/elements/empty-cart-button/empty-cart-button.js:50 -->
- **Without the script there is no question.** The form posts straight through and the cart is emptied; WooCommerce's notice "Your cart is now empty." shows only where the page prints WooCommerce's notices. <!-- src: src/elements/empty-cart-button/empty-cart-button.js:34-39 ; plugins/bfb-elements/includes/shop/class-live.php:249-255 -->
- **No WooCommerce, no button.** Without WooCommerce the page prints nothing; the builder still draws the button. <!-- src: plugins/bfb-elements-pro/elements/empty-cart-button.php:377-379 -->

## Never do

- Do not add an outer element to draw the button; style the element's root with the Style tab.
- Do not look for an icon position; the icon is always before the text.
- Do not expect the button's typography to reach the question; set `boxTypography`.
- Do not leave the default white box on a dark site; set `boxBackground` and its text colour.
- Do not set `iconSize` or `iconGap` without `icon`.
- Do not judge the question box from the canvas without `builderPreview`.
- Do not rely on the question without the script: the no-script post empties the cart at once.
