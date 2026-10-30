---
name: bfbe-shop-mini-cart
description: "Use for the shop's settings on Bricks' Mini cart (BFB Shop mini cart, `shop-mini-cart`): the panel as a named dialog with a title, keyboard and screen-reader behaviour, its own empty state or hidden while empty, the toggle and the lines as cards, undo after removing and save for later on its lines. Read before writing these settings."
---

# BFB Shop mini cart (`shop-mini-cart`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 2.0.0 or later, and BFB Elements Pro 2.0.0 or later for the groups marked Pro, WooCommerce active, the feature switches on (WordPress menu BFB Elements, Elements): `shop-mini-cart`, `shop-cart-lines`. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/shop-mini-cart.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/shop-mini-cart/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

## Where it lives
A feature, not an element: its groups are added to Bricks' own elements, on the Content tab after Bricks' own groups. By element:
- Mini cart (`woocommerce-mini-cart`): BFB Mini cart (`bfbeShopMiniCart`), BFB Mini cart look (`bfbeShopMiniCartLook`), BFB Cart lines (`bfbeShopCartLines`).

## Settings that decide the build

### Mini cart (`woocommerce-mini-cart`)

#### BFB Mini cart (`bfbeShopMiniCart`)
Free, switch `shop-mini-cart`.
- `bfbeShopMiniCartTitle` (text) **Panel title**. At the top of the panel, beside the close button.
- `bfbeShopMiniCartAdded` (text) **Announcement after adding**: placeholder Added: {product}. {cart}
- `bfbeShopMiniCartRemoved` (text) **Announcement after removing**: placeholder Removed: {product}. {cart}
- `bfbeShopMiniCartEmpty` (select) **When empty**: options: `woo` Show WooCommerce's text (default), `template` Show a template, `hide` Hide the whole mini cart
- `bfbeShopMiniCartTemplate` (select) **Template**: options: the site's own, read when the panel opens; only when `bfbeShopMiniCartEmpty` is `template`
Styling, in the schema file: `bfbeShopMiniCartEmptyPadding`.

#### BFB Mini cart look (`bfbeShopMiniCartLook`)
Free, switch `shop-mini-cart`.
- `bfbeShopMiniCartCountPlace` (select) **Count sits**: options: `static` After the amount, `absolute` On the link's corner; writes CSS
Styling, in the schema file: `bfbeShopMiniCartPanelMargin`, `bfbeShopMiniCartTitleTypography`, `bfbeShopMiniCartTitlePadding`, `bfbeShopMiniCartTextStart`, `bfbeShopMiniCartLineBackground`, `bfbeShopMiniCartLineBorder`, `bfbeShopMiniCartLinePadding`, `bfbeShopMiniCartLineShadow`, `bfbeShopMiniCartLineGap`, `bfbeShopMiniCartPictureBorder`, `bfbeShopMiniCartRemovePosition`, `bfbeShopMiniCartLinkHeight`, `bfbeShopMiniCartLinkWidth`, `bfbeShopMiniCartLinkPadding`, `bfbeShopMiniCartLinkAlign`, `bfbeShopMiniCartLinkBackground`, `bfbeShopMiniCartLinkBorder`, `bfbeShopMiniCartLinkTransition`, `bfbeShopMiniCartIconSize`, `bfbeShopMiniCartIconColor`, `bfbeShopMiniCartCountMargin`, `bfbeShopMiniCartCountShadow`, `bfbeShopMiniCartAmountHide`.

#### BFB Cart lines (`bfbeShopCartLines`)
Pro, switch `shop-cart-lines`.
- `bfbeShopCartLinesUndo` (select) **Show**: options: `on` On (default), `off` Off. A strip to bring back a removed item.
- `bfbeShopCartLinesUndoTime` (number) **Stays for (s)**: placeholder 12; only when `bfbeShopCartLinesUndo` is not `off`
- `bfbeShopCartLinesSave` (select) **Show**: options: `on` On (default), `off` Off. A button on each line.
- `bfbeShopCartLinesSaveText` (text) **Label**: placeholder Save for later; only when `bfbeShopCartLinesSave` is not `off`
Styling, in the schema file: `bfbeShopCartLinesUndoTypography`, `bfbeShopCartLinesUndoBackground`, `bfbeShopCartLinesUndoBorder`, `bfbeShopCartLinesUndoPadding`, `bfbeShopCartLinesUndoShadow`, `bfbeShopCartLinesUndoOver`, `bfbeShopCartLinesUndoPosition`, `bfbeShopCartLinesUndoBtnTypography`, `bfbeShopCartLinesUndoBtnBackground`, `bfbeShopCartLinesUndoBtnBorder`, `bfbeShopCartLinesUndoBtnPadding`, `bfbeShopCartLinesUndoBtnHover`, `bfbeShopCartLinesUndoBtnHoverColor`, `bfbeShopCartLinesSaveTypography`, `bfbeShopCartLinesSaveBackground`, `bfbeShopCartLinesSaveBorder`, `bfbeShopCartLinesSavePadding`, `bfbeShopCartLinesSaveHover`.
<!-- bfbe:generated:end -->

## Rendered DOM

Bricks' classic Mini cart keeps its markup; the feature adds attributes, a title, an empty box, and (with the script) the Undo strip and Save for later buttons:

```html
<div class="brxe-woocommerce-mini-cart bfbe-minicart--tpl bfbe-minicart--empty" data-bfbe-shop-need="cart,minicart,saved"
     data-bfbe-minicart='{"name":["Cart, %d item","Cart, %d items"],"added":"…","removed":"…"}' data-bfbe-minicart-empty="template"
     data-bfbe-cartlines='{"time":12,…}' data-bfbe-savelater-word="Save for later">
  <a class="mini-cart-link toggle-button bricks-woo-toggle" href="#" role="button" aria-label="Cart, 3 items"
     aria-expanded="false" aria-controls="bfbe-minicart-{id}" aria-haspopup="dialog">
    <span class="cart-icon">… <span class="cart-count">3</span></span><span class="cart-subtotal">…</span>
  </a>
  <div class="cart-detail off-canvas right cart-detail-{id}" id="bfbe-minicart-{id}" role="dialog"
       aria-labelledby="bfbe-minicart-{id}-title" aria-modal="true" tabindex="-1">
    <div class="bfbe-cartlines"><span class="bfbe-cartlines__text">Removed: …</span><button type="button" class="bfbe-cartlines__undo">Undo</button></div>
    <h2 class="bfbe-minicart__title" id="bfbe-minicart-{id}-title">My cart</h2>
    <div class="widget_shopping_cart_content">… WooCommerce's mini cart: li per line, + button.bfbe-savelater.bfbe-savelater--mini …</div>
    <div class="bfbe-minicart__empty" hidden>… the template …</div>
    <button class="bricks-mini-cart-close" …>…</button>
  </div>
</div>
```

- **The toggle** is a button named with the count, kept right after every change; `aria-expanded` follows Bricks' `show-cart-details` on the root. **The panel** is a dialog named by **Panel title** (`bfbeShopMiniCartTitle`), else "Shopping cart"; `aria-modal` only off-canvas.
- **With a title** the panel is a flex column and WooCommerce's content takes the rest of its height. `bfbeShopMiniCartTitleTypography` and `bfbeShopMiniCartTitlePadding` write `.bfbe-minicart__title` (default padding 30px 60px 0 30px).
- **Empty state.** `bfbe-minicart--empty` on the root while the cart is empty; `bfbeShopMiniCartEmpty: "template"` adds `bfbe-minicart--tpl` and the `.bfbe-minicart__empty` box (`bfbeShopMiniCartEmptyPadding`); `"hide"` adds `bfbe-minicart--hide` and `hidden` on the root.
- **Look controls** (BFB Mini cart look) are CSS only: `PanelMargin` on `.cart-detail.off-canvas`, `Line*` on `.cart-detail li`, `PictureBorder` on its `img`, `RemovePosition` on `.remove`, `TextStart` a margin on the line's options, quantity and Save for later, `Link*` on `.mini-cart-link`, `Icon*` on `.cart-icon svg`, `Count*` on `.cart-count`, `AmountHide` on `.cart-subtotal`.
- **BFB Cart lines.** The strip `.bfbe-cartlines` (`bfbeShopCartLinesUndo*`; `UndoBtn*` on `.bfbe-cartlines__undo`) is the panel's first child while offered; Save for later is `button.bfbe-savelater` (`bfbeShopCartLinesSave*`) at the end of each line `li` that is not `.bfbe-savelater-no`.

## Wiring to other elements

- **Hub and neighbours.** Start at `bfbe-shop`. The live tags and conditions (`{bfbe_cart_count}`, `{bfbe_cart_total}`, the cart conditions) are `bfbe-shop-tags-and-conditions`; the Saved for later loop (`bfbeShopSaved`) with BFB Saved Item Button is `bfbe-shop-loops` and `bfbe-saved-item-button`.
- **Everything that changes the cart refreshes it**: WooCommerce's buttons, and our own actions (BFB Cart Quantity, BFB Empty Cart Button, BFB Cart Shipping) whose answers carry WooCommerce's fragments.
- **A mini cart of your own layout** (Bricks' Cart contents loop in a Bricks popup) is not this element: build it as a BFB Live cart region (`bfbeLiveCart`, skill `bfbe-shop-cart-page`).
- **BFB Toast** with Show `cartAdd` speaks for adds; this element's add announcement then stays quiet (`bfbe-toast`).
- **The empty state's template** is a Bricks section or content template by id (`bfbeShopMiniCartTemplate`); read the target site's options before choosing one.
- The dialog's id comes from the element id, so give it a class in `_cssClasses` for your own CSS, never its id.

## Verified patterns

**A drawer with a title, lines as cards, and Undo over the title's line.** From the demo shop's header template (`dev/demo/shop/10-templates.php`, `.fh-minicart`). An off-canvas drawer 16px in from the window with rounded corners, the title "My cart" padded to clear the close button, each line a bordered card, the toggle a white pill with the count after the amount, Undo for 15 seconds laid over the title's line, Save for later on. Trimmed: the demo's SVG icon (sized there with `bfbeShopMiniCartIconSize`), colour variables, mobile values and the empty-state template.

```json
{
  "name": "woocommerce-mini-cart",
  "settings": {
    "icon": { "library": "themify", "icon": "ti-bag" }, "iconTypography": { "font-size": "20px" },
    "subtotalPosition": "row", "subtotalGap": "8",
    "cartDetailsOffCanvas": "right", "cartDetailsWidth": "420",
    "cartDetailsPadding": { "top": "16", "right": "28", "bottom": "28", "left": "28" },
    "cartDetailsBorder": { "radius": { "top": "24", "right": "24", "bottom": "24", "left": "24" } },
    "cartDetailsCloseIcon": { "library": "themify", "icon": "ti-close" },
    "cartDetailsClosePosition": { "top": "20", "right": "20" },
    "bfbeShopMiniCartTitle": "My cart",
    "bfbeShopMiniCartTitleTypography": { "font-size": "22px", "font-weight": "800", "line-height": "44px" },
    "bfbeShopMiniCartTitlePadding": { "top": "18", "right": "76", "bottom": "0", "left": "28" },
    "bfbeShopMiniCartPanelMargin": { "top": "16", "right": "16", "bottom": "16" },
    "bfbeShopMiniCartTextStart": "75px",
    "bfbeShopMiniCartLineBackground": { "hex": "#ffffff" },
    "bfbeShopMiniCartLineBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "16", "right": "16", "bottom": "16", "left": "16" } },
    "bfbeShopMiniCartLinePadding": { "top": "12", "right": "40", "bottom": "12", "left": "12" },
    "bfbeShopMiniCartLineGap": "10px",
    "bfbeShopMiniCartRemovePosition": { "top": "10", "right": "12" },
    "bfbeShopMiniCartLinkHeight": "44px",
    "bfbeShopMiniCartLinkPadding": { "top": "0", "right": "16", "bottom": "0", "left": "12" },
    "bfbeShopMiniCartLinkBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "999", "right": "999", "bottom": "999", "left": "999" } },
    "bfbeShopMiniCartCountPlace": "static",
    "bfbeShopCartLinesUndoTime": 15,
    "bfbeShopCartLinesUndoOver": true,
    "bfbeShopCartLinesUndoPosition": { "top": "18", "right": "70", "left": "20" },
    "bfbeShopCartLinesUndoBackground": { "hex": "#f6f6f8" },
    "bfbeShopCartLinesUndoPadding": { "top": "4", "right": "4", "bottom": "4", "left": "12" },
    "bfbeShopCartLinesSave": "on", "bfbeShopCartLinesSaveText": "Save for later",
    "_cssClasses": "site-minicart"
  }
}
```

**A dropdown with a template while empty.** From the fixture "SHOP P7a" (`fixture-shop-p7a`, `.mc-drop`). `bfbeShopMiniCartEmpty: "template"` shows the template in the panel instead of WooCommerce's text; Undo stays 20 seconds with a lifted strip. `79921` is the fixture site's template id: set the target site's own.

```json
{
  "name": "woocommerce-mini-cart",
  "settings": {
    "cartCount": "flex",
    "bfbeShopMiniCartEmpty": "template", "bfbeShopMiniCartTemplate": "79921",
    "bfbeShopCartLinesUndoTime": 20,
    "bfbeShopCartLinesUndoShadow": { "values": { "offsetX": "0", "offsetY": "6", "blur": "16", "spread": "0" }, "color": { "hex": "#10182833" } },
    "bfbeShopCartLinesUndoBtnPadding": { "top": "7", "right": "15", "bottom": "7", "left": "15" },
    "_cssClasses": "mc-drop"
  }
}
```

**A drawer that is gone while the cart is empty.** From the same fixture (`.mc-drawer`): `"hide"` removes the whole element, toggle included, until something is added.

```json
{ "name": "woocommerce-mini-cart", "settings": { "cartCount": "flex", "cartDetailsOffCanvas": "right", "cartDetailsCloseIcon": { "library": "themify", "icon": "ti-close" }, "bfbeShopMiniCartEmpty": "hide", "_cssClasses": "mc-drawer" } }
```

## Gotchas

- **The keyboard and screen-reader part has no switch.** Every classic Mini cart gets it while the Mini cart feature is on; the feature's switch on BFB Elements, Elements is the only way back to Bricks' element as it is. Bricks' experimental Mini Cart Builder is not covered. <!-- src: plugins/bfb-elements/includes/shop/class-mini-cart.php:3-6 ; docs/elements/shop-mini-cart.md "Limits" -->
- **Bricks pads the content, not the panel.** Bricks' **Padding** (`cartDetailsPadding`) writes `.widget_shopping_cart_content`, so the title keeps its own 30px 60px 0 30px: set `bfbeShopMiniCartTitlePadding` to line it up and clear the close button. <!-- src: bricks/includes/woocommerce/elements/woocommerce-mini-cart.php:395-405 ; src/elements/shop-mini-cart/shop-mini-cart.css:3-7 -->
- **The title needs the panel.** With **Hide cart details** (`hideCartDetails`) there is no panel, so no title, no Undo and no Save for later; Title typography and Title padding show only with a title. <!-- src: plugins/bfb-elements/includes/shop/class-mini-cart.php:421-427 ; plugins/bfb-elements/includes/shop/class-mini-cart.php:149-160 ; plugins/bfb-elements-pro/includes/shop/class-cart-lines.php:173-175 -->
- **The Undo strip comes before the title.** It is the panel's first child, so while offered it pushes the title down; with `bfbeShopCartLinesUndoOver` and `bfbeShopCartLinesUndoPosition` it sits over the title's line instead, as the demo sets it. <!-- src: src/elements/shop-cart-lines/shop-cart-lines.js:59 ; plugins/bfb-elements-pro/includes/shop/class-cart-lines.php:104-123 ; dev/demo/shop/10-templates.php:162 -->
- **Undo and the mini cart's Save for later exist only with the script.** The strip stays 3 to 120 seconds (12 unset), paused while the focus is in it; a gift's or an offer's line gets no Save for later, and where WooCommerce's own Save for Later in Cart is on, the Save for later controls are not offered at all. <!-- src: plugins/bfb-elements-pro/includes/shop/class-cart-lines.php:176-178 ; plugins/bfb-elements-pro/includes/shop/class-save-for-later.php:77-79 ; plugins/bfb-elements-pro/includes/shop/class-save-for-later.php:236-240 -->
- **Panel margin is for the drawer.** `bfbeShopMiniCartPanelMargin` shows only with Bricks' **Off-canvas** (`cartDetailsOffCanvas`) set; round the corners with Bricks' own `cartDetailsBorder`. <!-- src: plugins/bfb-elements/includes/shop/class-mini-cart.php:119-122 ; plugins/bfb-elements/includes/shop/class-mini-cart.php:142-148 -->
- **The template is shown beside WooCommerce's content.** It is hidden while the cart has lines, WooCommerce's own empty text is hidden with it, and a template that itself holds a mini cart is refused by Bricks. `bfbeShopMiniCartEmptyPadding` shows only with `"template"`. <!-- src: plugins/bfb-elements/includes/shop/class-mini-cart.php:431-439 ; src/elements/shop-mini-cart/shop-mini-cart.css:9-12 ; docs/elements/shop-mini-cart.md "Limits" -->
- **Hidden while empty beats a Display you set.** `"hide"` uses `display: none !important` on the hidden root; the builder always shows the element. <!-- src: src/elements/shop-mini-cart/shop-mini-cart.css:13-14 ; plugins/bfb-elements/includes/shop/class-mini-cart.php:356-360 -->
- **Icon size and colour reach an SVG icon only.** `bfbeShopMiniCartIconSize` and `bfbeShopMiniCartIconColor` write `.cart-icon svg`; a font icon takes Bricks' `iconTypography`. <!-- src: plugins/bfb-elements/includes/shop/class-mini-cart.php:254-266 -->
- **Count sits moves where Bricks measures from.** With `bfbeShopMiniCartCountPlace` set, the count leaves the icon's box, and Bricks' Count Top and Right then measure from the link. <!-- src: plugins/bfb-elements/includes/shop/class-mini-cart.php:113-117 ; plugins/bfb-elements/includes/shop/class-mini-cart.php:268-285 -->
- **One sentence per change.** `{product}` and `{cart}` fill the announcements; where a BFB Toast shows the added product, or WooCommerce printed its own notice after a post, the add is not said again. A panel opened by an add to cart leaves the focus where it was. <!-- src: docs/elements/shop-mini-cart.md "BFB Mini cart" ; src/elements/shop-mini-cart/shop-mini-cart.js:60-61 -->

## Never do

- Do not set `bfbeShopMiniCartTitleTypography` or `bfbeShopMiniCartTitlePadding` without `bfbeShopMiniCartTitle`.
- Do not set a title, Undo or Save for later on a mini cart with `hideCartDetails`.
- Do not set `bfbeShopMiniCartPanelMargin` without `cartDetailsOffCanvas`.
- Do not leave the Undo strip under a title without `bfbeShopCartLinesUndoOver` and a position if the title must not move.
- Do not pin `bfbeShopMiniCartTemplate` to an id without reading the target site's templates, or to a template holding a mini cart.
- Do not size a font icon with `bfbeShopMiniCartIconSize`; use Bricks' `iconTypography`.
- Do not build a popup cart of your own layout on this element; use a BFB Live cart region.
