---
name: bfbe-quote-list-button
description: "Use when adding Add to quote to products, building a quote list page, or a form that turns the quote list into a WooCommerce draft order, with BFB Quote List Button (`bfbe-quote-list-button`). Read before writing its settings."
---

# BFB Quote List Button (`bfbe-quote-list-button`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-quote-list-button.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/quote-list-button/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 0.55 KB, JS none (gzipped), no dependencies, loaded only on pages that use it.

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Button (`bfbeButton`)
- `textAdd` (text) **Words to add**: placeholder Add to quote; dynamic data accepted
- `textOn` (text) **Words when added**: placeholder On your quote list; dynamic data accepted
- `content` (select) **Button shows**: options: `both` Icon and words (default), `icon` Icon only, `words` Words only
- `iconAdd` (icon) **Icon to add**: only when `content` is not `words`
- `iconOn` (icon) **Icon when added**: only when `content` is not `words`
- `quantity` (checkbox) **Quantity field**

### Look (`bfbeLook`)
- `iconPlace` (select) **Icon sits**: options: `row` Before the words (default), `row-reverse` After the words; writes CSS; only when `content` is not `icon` or `words`
Styling, in the schema file: `btnType`, `btnBackground`, `btnBorder`, `btnShadow`, `btnPadding`, `hoverBackground`, `hoverColor`, `hoverBorderColor`, `iconSize`, `iconColor`, `gap`, `onBackground`, `onColorText`, `onBorderColor`, `onColor`, `qtyTypography`, `qtyBackground`, `qtyBorder`, `qtyPadding`, `qtyWidth`, `qtyGap`.

### Quantity arrows (`bfbeQtyArrows`)
The whole group shows only when `quantity` is set.
- `qtySpinArrows` (select) **Arrows**: options: `browser` The browser's, `inside` Ours, inside the box, `stepper` A − and a + beside it, `none` None; only when `quantity` is set
Styling, in the schema file: `qtySpinArrowSize`, `qtySpinArrowWidth`, `qtySpinArrowGap`, `qtySpinArrowColor`, `qtySpinArrowBg`, `qtySpinArrowHover`, `qtySpinArrowHoverBg`, `qtySpinArrowLine`, `qtySpinArrowBorder`.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<form id="brxe-{id}" class="brxe-bfbe-quote-list-button bfbe-list bfbe-list--both bfbe-list--qty" method="post"
      data-bfbe-list="quote" data-bfbe-list-act="list_toggle" data-bfbe-shop-need="quote" data-bfbe-list-var="1"
      data-bfbe-list-off="Add to quote: Everyday Crew Tee" data-bfbe-list-on="On your quote list: Everyday Crew Tee">
  <input type="hidden" name="bfbe_shop_act" value="list_toggle"> <!-- + the nonce, the way back, kind=quote, product, variation -->
  <label class="bfbe-list__qty-box" for="…"><span class="bfbe-sr">Quantity</span>
    <input class="bfbe-list__qty" id="…" type="number" name="qty" min="1" max="999" step="1" value="1" inputmode="numeric"></label>
  <button type="submit" class="bfbe-list__btn" aria-pressed="false" aria-label="Add to quote: Everyday Crew Tee">
    <span class="bfbe-list__icon bfbe-list__icon--add" aria-hidden="true">…</span><span class="bfbe-list__icon bfbe-list__icon--on" aria-hidden="true">…</span>
    <span class="bfbe-list__word bfbe-list__word--add">Add to quote</span><span class="bfbe-list__word bfbe-list__word--on">On your quote list</span>
  </button>
</form>
```

- The toggle is the BFB Compare Button's (`bfbe-compare-button`, Rendered DOM): a real `form`, both states printed, shown from `aria-pressed`, the same Look keys writing to the same parts. Default icons: a sheet with a plus, then with a tick.
- **Quantity field** `quantity` adds `bfbe-list--qty` (no wrap) and the labelled number box before the button. **Arrows** `qtySpinArrows` `inside`, `stepper` or `none` wrap it in `span.bfbe-spin` with `.bfbe-spin__btn` buttons; `browser` (unset) leaves the input bare.
- The quantity controls write to `.bfbe-list__qty` (`qtyTypography`, `qtyBackground`, `qtyBorder`, `qtyPadding`, `qtyWidth`, default 4.5em); `qtyGap` is the root's gap.
- No script of its own: the Lists feature's `shop-lists.min.js` posts `list_toggle` with the variation chosen and the quantity, then sets `aria-pressed` and `aria-label` on every quote button for the product.

**The quote page.** A query loop of type **Quote list** (`bfbeShopQuote`): each row's root carries `data-bfbe-list-row="quote:<page>:<element>"` and `data-bfbe-list-item="<product>:<variation>"`. With **Quantity and Remove on each row** on, `div.bfbe-lrow__actions` holds two forms: `input.bfbe-lrow__qty` with `button.bfbe-lrow__update`, and `button.bfbe-lrow__remove`. Off, a `span.bfbe-lrow__qty-read` "Quantity: 3".

## Wiring to other elements

- **The product in hand**: the loop row's product (a variation row stands for its parent), else the page's. On a product page the press reads the variation from WooCommerce's `form.variations_form` for that product, and, with no Quantity field, the quantity from its `input.qty`: place it on the same template as Bricks' Add to cart.
- **The quote list** is a query loop: `hasLoop: true`, `query.objectType: "bfbeShopQuote"` on a Block, Container or Div, group **BFB Quote list**: **Quantity and Remove on each row** `bfbeShopQuoteActions` (`on` or `off`), **Update word** `bfbeShopQuoteUpdateText`, **Remove word** `bfbeShopQuoteRemoveText`. The empty state is Bricks' `query.no_results_text` (`bfbe-shop-loops`).
- **The count**: `{bfbe_quote_count}` (**Quote list: how many lines, live**) in any Text.
- **The request**: a BFB Advanced Forms form (`bfbe-form`) with `actions: ["bfbe-quote-order"]` (**Create a draft order from the quote list**). Its group **Draft order**: **Email from the answer** `bfbeQuoteEmail`, **Name from the answer** `bfbeQuoteName`, **When the list is empty** `bfbeQuoteEmpty`. Field keys there are the fields' **Key**.
- After a send with the script, the shop's live answer is asked again, so the loop, the count and every button on the page show the emptied list.
- **Interactions**: every change fires **List changed** (`detail.kind` `"quote"`) with the Shop data feature on (`bfbe-shop-tags-and-conditions`).
- For your own CSS give it a class in `_cssClasses`, never `_cssId`: loop rows and component instances share ids.

## Verified patterns

**On a product template, under Add to cart.** From the template `bfbe-shop-product-p9` on the dev site ("The three lists" row, after Bricks' Add to cart). The first Quote List Button reads the variation and quantity from WooCommerce's form above it; the second, "Quote with its own quantity", sends its own box. **Arrows** is added here to show the group the field opens.

```json
{
  "name": "block",
  "settings": { "_rowGap": "16px" },
  "children": [
    { "name": "product-add-to-cart", "settings": {} },
    { "name": "block", "settings": { "_direction": "row", "_columnGap": "12px", "_cssClasses": "p9-buttons" }, "children": [
      { "name": "bfbe-compare-button", "settings": { "_cssClasses": "cmp" } },
      { "name": "bfbe-quote-list-button", "settings": { "_cssClasses": "qt" } },
      { "name": "bfbe-quote-list-button", "settings": { "quantity": true, "qtySpinArrows": "stepper", "_cssClasses": "qt-own" } }
    ] }
  ]
}
```

**The quote page: the lines and the request form side by side.** From the demo shop's Quote page (`dev/demo/shop/20-pages.php`, "Quote", the 2.4 site). A Quote list loop with Bricks' elements in each row and its Update and Remove; the form makes the draft order and empties the list. Trimmed: the demo's look and the Company field.

```json
{
  "name": "block",
  "settings": { "_display": "grid", "_gridTemplateColumns": "minmax(0, 1.4fr) minmax(0, 1fr)", "_gridTemplateColumns:tablet_portrait": "minmax(0, 1fr)", "_gridGap": "40px", "_alignItems": "start" },
  "children": [
    { "name": "block", "settings": { "_rowGap": "16px" }, "children": [
      { "name": "text-basic", "settings": { "text": "{bfbe_quote_count} lines on your quote" } },
      { "name": "block", "settings": { "hasLoop": true, "query": { "objectType": "bfbeShopQuote", "no_results_text": "Your quote is empty. Use Add to a quote on any product." }, "bfbeShopQuoteActions": "on", "_direction": "row", "_columnGap": "16px", "_alignItems": "center" }, "children": [
        { "name": "image", "settings": { "image": { "useDynamicData": "{featured_image}", "size": "thumbnail" }, "_width": "72px" } },
        { "name": "block", "settings": { "_rowGap": "2px" }, "children": [
          { "name": "heading", "settings": { "text": "{post_title}", "tag": "h4" } },
          { "name": "text-basic", "settings": { "text": "{woo_product_price}" } }
        ] }
      ] }
    ] },
    { "name": "bfbe-form", "settings": { "actions": [ "bfbe-quote-order" ], "bfbeQuoteEmpty": "Add a product to your quote first.", "successMessage": "Thank you. We will send a priced order within two working days." }, "children": [
      { "name": "bfbe-form-text", "settings": { "label": "Your name", "key": "name", "type": "text", "required": true } },
      { "name": "bfbe-form-text", "settings": { "label": "Email", "key": "email", "type": "email", "required": true } },
      { "name": "bfbe-form-text", "settings": { "label": "Anything we should know", "key": "message", "type": "textarea" } },
      { "name": "bfbe-form-button", "settings": { "kind": "send", "sendText": "Send for a quote" } }
    ] }
  ]
}
```

## Gotchas

- **A variable product needs its options first.** The press sends the variation chosen in WooCommerce's form; on a card there is none, so it is refused, "Choose the options first: Everyday Crew Tee." Each variation is its own line. <!-- src: plugins/bfb-elements-pro/includes/shop/class-lists.php:819-822 --> <!-- src: src/elements/shop-lists/shop-lists.js:24-33 -->
- **On a card a variable product reads as any line.** Without a chosen variation the button shows pressed when any variation is on the list, and its press is still refused as above. <!-- src: plugins/bfb-elements-pro/includes/shop/class-lists.php:709-716 --> <!-- src: src/elements/shop-lists/shop-lists.js:42 -->
- **Where the quantity comes from.** With **Quantity field** on, its box; off, the product form's quantity on a product page, else 1; kept between 1 and 999. <!-- src: src/elements/shop-lists/shop-lists.js:145-148 --> <!-- src: plugins/bfb-elements-pro/includes/shop/class-lists.php:873 -->
- **A second press takes the line off.** The button is a toggle: pressed again for the same variation it removes the line, whatever the quantity. Quantities change in the quote loop's Update. <!-- src: plugins/bfb-elements-pro/includes/shop/class-lists.php:861-876 -->
- **Grouped and external products cannot be quoted.** The press is refused, "Kitchen Starter Set cannot go on a quote list." Fifty lines at most: "This list is full at 50. Remove one first." <!-- src: plugins/bfb-elements-pro/includes/shop/class-lists.php:815-818 --> <!-- src: plugins/bfb-elements-pro/includes/shop/class-lists.php:57, 864-871 -->
- **The quantity's look needs the field.** The Quantity controls in Look and the whole **Quantity arrows** group show only with `quantity` set. <!-- src: plugins/bfb-elements-pro/elements/quote-list-button.php:43, 113, 121 -->
- **The action needs the Lists feature.** **Create a draft order from the quote list** and the **Draft order** group are added to BFB Advanced Forms only with WooCommerce active and Lists on. <!-- src: plugins/bfb-elements-pro/includes/class-form-actions.php:1640-1676 -->
- **The draft order cannot be paid yet.** It is a WooCommerce order in Pending payment at the shop's prices now; it asks no payment until the shop sends WooCommerce's Customer invoice email, so the account shows no Pay before then. <!-- src: plugins/bfb-elements-pro/includes/class-form-actions.php:1920-1944 --> <!-- src: docs/elements/quote-list-button.md "The draft order" -->
- **Five requests an hour from one address.** Past that the form answers "Too many quote requests from here just now" and makes no order; the filter `bfbe_shop_quote_hourly_limit` changes the five. <!-- src: plugins/bfb-elements-pro/includes/class-form-actions.php:1907-1918 -->
- **The email and the name come from field keys.** `bfbeQuoteEmail` empty takes the first email field answered, else a signed-in customer's own; `bfbeQuoteName` empty reads the key `name` and splits it at the first space. <!-- src: plugins/bfb-elements-pro/includes/class-form-actions.php:1945-1959, 1999-2005 -->
- **It prints nothing without a product.** Outside a product loop row or a product page it renders no markup on the page and a notice in the canvas. <!-- src: plugins/bfb-elements-pro/elements/quote-list-button.php:164-169 --> <!-- src: plugins/bfb-elements/includes/abstract-element.php:549-556 -->

## Never do

- Do not place a Quote List Button for a variable product on a card where no WooCommerce variation form is on the page; it can only be refused.
- Do not set the `qty*` keys or `qtySpinArrows` without `quantity: true`.
- Do not tell visitors a second press adds more; it removes the line. Put the quote loop with **Quantity and Remove on each row** on the quote page.
- Do not build the quote request without `actions: ["bfbe-quote-order"]` on a BFB Advanced Forms form.
- Do not promise a pay link on sending; the shop prices the order and sends WooCommerce's invoice.
- Do not place it outside a product loop row or a product page.
- Do not target it by `_cssId`; give it a class.
