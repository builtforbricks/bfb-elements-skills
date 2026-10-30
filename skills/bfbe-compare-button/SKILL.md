---
name: bfbe-compare-button
description: "Use when adding a compare toggle to product cards or a product page, styling its pressed state, or wiring it to a compare tray and compare page, with BFB Compare Button (`bfbe-compare-button`). Read before writing its settings."
---

# BFB Compare Button (`bfbe-compare-button`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-compare-button.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/compare-button/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 1.17 KB, JS 0.78 KB (gzipped), no dependencies, loaded only on pages that use it.

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Button (`bfbeButton`)
- `textAdd` (text) **Words to add**: placeholder Compare; dynamic data accepted
- `textOn` (text) **Words when added**: placeholder Comparing; dynamic data accepted
- `content` (select) **Button shows**: options: `both` Icon and words (default), `icon` Icon only, `words` Words only
- `iconAdd` (icon) **Icon to add**: only when `content` is not `words`
- `iconOn` (icon) **Icon when added**: only when `content` is not `words`

### Look (`bfbeLook`)
- `iconPlace` (select) **Icon sits**: options: `row` Before the words (default), `row-reverse` After the words; writes CSS; only when `content` is not `icon` or `words`
Styling, in the schema file: `btnType`, `btnBackground`, `btnBorder`, `btnShadow`, `btnPadding`, `hoverBackground`, `hoverColor`, `hoverBorderColor`, `iconSize`, `iconColor`, `gap`, `onBackground`, `onColorText`, `onBorderColor`, `onColor`.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<form id="brxe-{id}" class="brxe-bfbe-compare-button bfbe-list bfbe-list--both" method="post"
      data-bfbe-list="compare" data-bfbe-list-act="list_toggle" data-bfbe-shop-need="compare"
      data-bfbe-list-off="Compare: Oak Serving Board" data-bfbe-list-on="Comparing: Oak Serving Board" data-bfbe-list-var="1">
  <input type="hidden" name="bfbe_shop_act" value="list_toggle"> <!-- + the nonce, the way back, kind=compare, product, variation=0 -->
  <button type="submit" class="bfbe-list__btn" aria-pressed="false" aria-label="Compare: Oak Serving Board">
    <span class="bfbe-list__icon bfbe-list__icon--add" aria-hidden="true"><svg …></span>
    <span class="bfbe-list__icon bfbe-list__icon--on" aria-hidden="true"><svg …></span>
    <span class="bfbe-list__word bfbe-list__word--add">Compare</span><span class="bfbe-list__word bfbe-list__word--on">Comparing</span>
  </button>
</form>
```

- The root is a real `form` posting to the page; `data-bfbe-list-var="1"` only on a variable product. **Button shows** `content` prints no icons (`words`) or no words (`icon`) and names the root `bfbe-list--{content}`.
- Both states are always printed. CSS shows one from `aria-pressed` on `.bfbe-list__btn`, never from a class; the default icons are two columns, the second filled and ticked.
- No script of its own: the Lists feature's `shop-lists.min.js` catches the submit, posts `list_toggle`, sets `aria-busy="true"` while it waits, then sets `aria-pressed` and `aria-label` on every compare button for that product from `data-bfbe-list-on` and `data-bfbe-list-off`.
- Where the Look controls write: `btnType`, `btnBorder`, `btnShadow`, `btnPadding` and **Icon sits** `iconPlace` (`flex-direction`) to `.bfbe-list__btn`; `btnBackground`, `onBackground`, `iconSize`, `iconColor`, `onColor`, `gap` to `--bfbe-list-*` properties on the root; `hover*` to the button's `:hover` and `:focus-visible`; `onColorText`, `onBorderColor` to `.bfbe-list__btn[aria-pressed="true"]`.
- Bricks' Style tab draws the `form`, not the button inside it. The markup and controls are the BFB Wishlist Button's and BFB Quote List Button's too (`src/elements/shop-lists/list-button.css`).

## Wiring to other elements

- **The product in hand**: the query loop row's product (a variation row stands for its parent), else the page's product. Nothing to point at; place it in a product loop or on a single product template.
- **BFB Compare Tray** (`bfbe-compare-tray`) shows what is being compared. The button prints no tray: place one tray, in the footer template, so every page has it. The two never name each other; both follow the visitor's compare list.
- **The compare page** is a Comparison Table with **Rows and columns from** `source: "compare"` (`bfbe-comparison-table`), or a query loop of type `bfbeShopCompare` (`bfbe-shop-loops`). Choose it as **Compare page** on BFB Elements, Shop, Customers, so `{bfbe_compare_url}` links to it.
- **Counts**: `{bfbe_compare_count}` in any Text is the live count, right on cached pages (`bfbe-shop` header pattern).
- **Interactions**: every change fires **List changed** (BFB Shop triggers, event `bfbe/woo/list-changed` on `body`, `detail.kind` `"compare"`), with the Shop data feature on (`bfbe-shop-tags-and-conditions`).
- For your own CSS give it a class in `_cssClasses`, never `_cssId`: component instances and loop rows share ids.

## Verified patterns

**Icon only on a product card, beside Add to cart.** From the demo shop's product card (`dev/demo/shop/lib.php`, the card builder, on the 2.4 site); the fixture `fixture-shop-p9` places the same button in each card of its loop. `_flexShrink` keeps its size beside the add button; it leaves the card on a phone. Trimmed: the demo's colours and type.

```json
{
  "name": "block",
  "settings": { "hasLoop": true, "query": { "objectType": "bfbeShopProducts" }, "bfbeShopSet": "new", "bfbeShopCount": 4, "_cssClasses": "card" },
  "children": [
    { "name": "image", "settings": { "image": { "useDynamicData": "{featured_image}", "size": "woocommerce_thumbnail" } } },
    { "name": "product-title", "settings": { "tag": "h3", "linkToProduct": true } },
    { "name": "product-price", "settings": {} },
    { "name": "block", "settings": { "_direction": "row", "_alignItems": "center", "_columnGap": "8px" }, "children": [
      { "name": "product-add-to-cart", "settings": {} },
      { "name": "bfbe-compare-button", "settings": { "content": "icon", "iconSize": "17", "btnPadding": { "top": "10", "right": "10", "bottom": "10", "left": "10" }, "onColor": { "hex": "#6e44ff" }, "onBackground": { "hex": "#f0ecff" }, "_flexShrink": "0", "_display:mobile_portrait": "none", "_cssClasses": "card-compare" } }
    ] }
  ]
}
```

**The three list buttons in one row on a product template.** From the demo shop's product template (`dev/demo/shop/10-templates.php`, "Lists and size guide"). Icon and words, the pressed state in the accent's tint; the Quote List Button's words changed. Trimmed: the Size Guide and the demo's type.

```json
{
  "name": "block",
  "settings": { "_direction": "row", "_flexWrap": "wrap", "_columnGap": "10px", "_rowGap": "10px" },
  "children": [
    { "name": "bfbe-wishlist-button", "settings": { "content": "both", "textAdd": "Save", "textOn": "Saved" } },
    { "name": "bfbe-compare-button", "settings": { "content": "both", "iconSize": "17", "gap": "8", "onColor": { "hex": "#6e44ff" }, "onBackground": { "hex": "#f0ecff" } } },
    { "name": "bfbe-quote-list-button", "settings": { "content": "both", "textAdd": "Add to a quote", "textOn": "On your quote" } }
  ]
}
```

## Gotchas

- **No tray of its own.** Since 29 October a page with compare buttons and no BFB Compare Tray has no tray; the buttons still work and say what they did. This may be revisited. <!-- src: plugins/bfb-elements-pro/elements/compare-button.php:7-10 --> <!-- src: docs/elements/compare-tray.md "Limits" -->
- **It prints nothing without a product.** Outside a product loop row or a product page it renders no markup on the page and a notice in the canvas. <!-- src: plugins/bfb-elements-pro/elements/compare-button.php:142-147 --> <!-- src: plugins/bfb-elements/includes/abstract-element.php:549-556 -->
- **Four products at most.** A fifth is refused, "You can compare up to 4 products. Remove one to add Walnut Salt Cellar.", said at once; the button stays unpressed. <!-- src: plugins/bfb-elements-pro/includes/shop/class-lists.php:57 --> <!-- src: plugins/bfb-elements-pro/includes/shop/class-lists.php:863-871 -->
- **Products only, never a variation.** A variable product is compared as itself, whatever option the shopper chose; the toggle drops the variation. <!-- src: plugins/bfb-elements-pro/includes/shop/class-lists.php:807-808 --> <!-- src: docs/elements/compare-button.md "Limits" -->
- **Needs the Lists feature.** With Lists off (BFB Elements, Elements) or WooCommerce inactive the button prints nothing on the page. <!-- src: plugins/bfb-elements-pro/elements/compare-button.php:136-140 -->
- **One sentence, said once.** With a BFB Compare Tray on the page and something compared, the tray's own region says the change; elsewhere the shop's shared status says it. Do not add a second announcement. <!-- src: src/elements/shop-lists/shop-lists.js:153-156 -->
- **A guest's page is kept from the cache.** A page drawn for a guest who compares something is marked `DONOTCACHEPAGE`; on a cached page the live answer sets each button right after load. <!-- src: plugins/bfb-elements-pro/includes/shop/class-lists.php:208-212 --> <!-- src: docs/elements/compare-button.md "Without the script" -->
- **The canvas never presses.** The canvas button is `type="button"` and always unpressed, so the pressed look shows only on the page. <!-- src: plugins/bfb-elements-pro/elements/compare-button.php:151 --> <!-- src: plugins/bfb-elements-pro/elements/compare-button.php:171 -->
- **The icon keys hide with words only.** `iconAdd`, `iconOn`, `iconSize`, `iconColor`, `onColor` need `content` other than `words`; `gap` and `iconPlace` need `both`. <!-- src: plugins/bfb-elements-pro/includes/class-list-look.php:27-28, 51-64 -->

## Never do

- Do not expect a tray from compare buttons alone; place one BFB Compare Tray, in the footer template.
- Do not place it outside a product loop row or a product page.
- Do not set `iconAdd`, `iconOn`, `iconSize`, `iconColor` or `onColor` with `content: "words"`, or `gap` and `iconPlace` unless `content` is `both`.
- Do not style the pressed state with a class; style `.bfbe-list__btn[aria-pressed="true"]` or use the Pressed controls.
- Do not add your own announcement of a compare change.
- Do not target it by `_cssId`; give it a class.
