---
name: bfbe-cart-quantity
description: "Use when placing, wiring or styling BFB Cart Quantity (`bfbe-cart-quantity`): plus, minus and Remove for each line of a cart page or mini cart laid out yourself, inside a row of Bricks' Cart contents query loop, with or without a BFB Live cart region. Read before writing its settings."
---

# BFB Cart Quantity (`bfbe-cart-quantity`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-cart-quantity.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/cart-quantity/

## What it is
Plus, minus and Remove for each line of a cart page you lay out yourself, placed inside a row of Bricks' Cart contents query loop, with Bricks' experimental shop setting off. The stepper follows WooCommerce's quantity rules for the line, and every change is a real form post that works before any script runs; the script makes it instant. Inside a Live cart region the row is drawn again; elsewhere the page reloads once the change is answered.

**Not for:** It is for a Cart contents loop, not a products loop or a product page, where Bricks' Add to cart element has its own quantity. It has no Undo after Remove; the mini cart's Undo is in the Cart lines feature.

**Costs a page:** CSS 0.80 KB, JS 2.33 KB (gzipped), plus shop-live, loaded only on pages that use it.

**Nestable:** no · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** no

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Quantity (`bfbeCartQty`)
- `shows` (select) **Shows**: options: `both` Quantity and Remove (default), `qty` Quantity only, `remove` Remove only. Quantity and Remove by default, or Quantity only, or Remove only. Place two elements in one row, one of each, to put the stepper and Remove apart.
- `removeWord` (text) **Remove word**: placeholder Remove; only when `shows` is not `qty`. The word on the Remove button, "Remove" unless you set one.
- `removeIcon` (icon) **Remove icon**: only when `shows` is not `qty`. None unless you set one; it sits before the word.
- `removeWordHidden` (checkbox) **Icon only**: only when `shows` is not `qty` and `removeIcon` is set. With a Remove icon set, the word goes and the icon stands alone, such as an × in a circle; the button keeps its name for screen readers.
- `minusIcon` (icon) **Minus icon**: only when `shows` is not `remove`. A plain minus unless set.
- `plusIcon` (icon) **Plus icon**: only when `shows` is not `remove`. A plain plus unless set.

### Look (`bfbeCartQtyLook`)
Styling only, every key in the schema file: `size`, `inputWidth`, `stepperBorder`, `stepperBackground`, `dividerColor`, `numberTypography`, `buttonIconSize`, `buttonColor`, `buttonBackground`, `buttonHoverColor`, `buttonHoverBackground`, `removeTypography`, `removeIconSize`, `removeColor`, `removeBackground`, `removeBorder`, `removePadding`, `removeHoverColor`, `removeHoverBackground`, `gap`.

## What it guarantees for accessibility (do not undo)
- The stepper is a group named "Quantity: <the line>", its buttons "Decrease quantity: ..." and "Increase quantity: ...", and Remove "Remove: ...".
- Each change is said once, politely: "Quantity 3: <the line>. Cart: 3 items, 84,00 €." A refusal is said assertively, in WooCommerce's words where it has them.
- After a redraw or a reload the focus goes back to the same control.
- Without the script plus, minus and Remove are real submit buttons, and Enter in the number presses Update.
<!-- bfbe:generated:end -->

## Rendered DOM

Inside a Cart contents row (in a query loop Bricks gives the element no id, so every look control writes under the element's class):

```html
<div class="brxe-{id} bfbe-cartqty" data-bfbe-cartqty="{line key}" data-bfbe-shop-need="cart" data-bfbe-cartqty-words='{"qty":"Quantity %1$s: %2$s.","removed":"Removed: %s."}'>
  <div class="bfbe-cartqty__notices" role="status">… WooCommerce's notice, after a no-script post …</div>
  <form class="bfbe-cartqty__form" method="post">
    <input type="hidden" name="bfbe_shop_act" value="cart_qty"> … <input type="hidden" name="key" value="{line key}">
    <button type="submit" class="bfbe-cartqty__update">Update</button>
    <div class="bfbe-cartqty__stepper" role="group" aria-label="Quantity: Harbour Linen Shirt, Ink, S">
      <button type="submit" class="bfbe-cartqty__step bfbe-cartqty__minus" name="step" value="-1" data-bfbe-step="-1" aria-label="Decrease quantity: …"><svg …/></button>
      <input type="number" class="bfbe-cartqty__input" id="bfbe-cartqty-{id}-{key}" name="qty" value="2" min="1" max="5" step="1" data-bfbe-qty="2" aria-label="Quantity: …">
      <button type="submit" class="bfbe-cartqty__step bfbe-cartqty__plus" name="step" value="1" data-bfbe-step="1" aria-label="Increase quantity: …"><svg …/></button>
    </div>
  </form>
  <form class="bfbe-cartqty__drop" method="post">… cart_remove …
    <button type="submit" class="bfbe-cartqty__remove" aria-label="Remove: …"><i …></i><span class="bfbe-cartqty__word">Remove</span></button>
  </form>
</div>
```

- **Shows** (`shows`) `qty` drops the Remove form, `remove` drops the stepper's form. A line of fixed quantity prints `span.bfbe-cartqty__fixed` (the number, with a hidden "Quantity: …") instead of the stepper.
- **States.** `html.bfbe-cartqty-js` once the script runs, which hides `.bfbe-cartqty__update`; `aria-busy="true"` on the stepper while a change is answered; `disabled` on minus at the line's minimum and on plus at its maximum.
- **Where controls write.** `size`, `inputWidth`, `dividerColor`, `buttonIconSize` and `removeIconSize` set custom properties on the root; `stepper*` write `.bfbe-cartqty__stepper`, `numberTypography` the input and `.bfbe-cartqty__fixed`, `button*` `.bfbe-cartqty__step`, `remove*` `.bfbe-cartqty__remove`, `gap` the root.

## Wiring to other elements

- **The row is the wiring.** Place it inside a Container, Block or Div with `hasLoop: true` and `query: { "objectType": "wooCart" }` (Bricks' **Cart contents**). The element reads the row's cart line from the loop: no key, class or id to set.
- **Beside it in the row**: Bricks' Image of `{featured_image}`, `{woo_cart_product_name}` or `{post_title}`, the row tags `{bfbe_cart_line_options}` and `{bfbe_cart_line_price}`, and Bricks' `{woo_cart_subtotal}` for the line's total (`bfbe-shop-tags-and-conditions`).
- **A BFB Live cart region** (`bfbeLiveCart: true` on an element that holds the loop, skill `bfbe-shop-cart-page`) draws the row again after each change and puts the focus back on the same control. Outside one, the page reloads instead.
- **Two instances, placed apart.** One with `shows: "qty"` and one with `shows: "remove"` in the same row put the stepper and Remove where the layout wants them.
- **Others that follow its answer**: Bricks' Mini cart (WooCommerce's fragments), the live cart tags (`{bfbe_cart_total}`), BFB Cart Shipping and BFB Cart Goals.
- **Bricks 2.4's v2 cart** (its experimental shop setting) has Bricks' own Cart quantity for its lines; this element is for the Cart contents loop, on Bricks 2.3 and 2.4.
- Give it a class in `_cssClasses` for your own CSS; component instances and loop rows share ids.

## Verified patterns

**A cart line as a card, in a live region.** From the demo shop's "Your own cart" page (`dev/demo/shop/20-pages.php`, `fh_cart_row()` in `dev/demo/shop/lib.php`). The region holds the Cart contents loop; each row is a card with the picture, name, options, price each, the stepper as a pill and the line's total. Trimmed: the demo's colour variables, responsive widths and the region's summary column.

```json
{
  "name": "block",
  "settings": { "bfbeLiveCart": true, "_rowGap": "12px", "_cssClasses": "cart-lines" },
  "children": [
    { "name": "block", "settings": { "hasLoop": true, "query": { "objectType": "wooCart" }, "_cssClasses": "cart-row", "_direction": "row", "_flexWrap": "wrap", "_alignItems": "center", "_columnGap": "20px", "_rowGap": "14px", "_padding": { "top": "16", "right": "16", "bottom": "16", "left": "16" } }, "children": [
      { "name": "image", "settings": { "image": { "useDynamicData": "{featured_image}", "size": "woocommerce_thumbnail" }, "_width": "96px" } },
      { "name": "block", "settings": { "_rowGap": "4px", "_flexGrow": "1" }, "children": [
        { "name": "text-basic", "settings": { "text": "<a href=\"{post_url}\">{post_title}</a>" } },
        { "name": "text-basic", "settings": { "text": "{bfbe_cart_line_options}" } },
        { "name": "text-basic", "settings": { "text": "{bfbe_cart_line_price} each" } }
      ] },
      { "name": "bfbe-cart-quantity", "settings": {
        "size": "38px", "inputWidth": "42px", "gap": "14px",
        "stepperBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "999", "right": "999", "bottom": "999", "left": "999" } },
        "stepperBackground": { "hex": "#ffffff" },
        "numberTypography": { "font-size": "15px", "font-weight": "700" },
        "buttonHoverColor": { "hex": "#6e44ff" }, "buttonHoverBackground": { "hex": "#f0ecff" },
        "removeTypography": { "font-size": "13px", "font-weight": "600" }, "removeColor": { "hex": "#667085" }, "removeHoverColor": { "hex": "#c2410c" },
        "_cssClasses": "row-qty"
      } },
      { "name": "text-basic", "settings": { "text": "{woo_cart_subtotal}" } }
    ] }
  ]
}
```

**A Remove as an × in a circle.** From the fixture "SHOP Q2: the cart parts with their inner looks set" (`fixture-shop-custom-cart-styled`, `.row-qty`). **Icon only** (`removeWordHidden`) needs `removeIcon`; the border's 50% corners and the padding make the circle. The fixture's red divider is left out.

```json
{
  "name": "block",
  "settings": { "hasLoop": true, "query": { "objectType": "wooCart" }, "_direction": "row", "_alignItems": "center", "_columnGap": "16px" },
  "children": [
    { "name": "text-basic", "settings": { "text": "{woo_cart_product_name}" } },
    { "name": "bfbe-cart-quantity", "settings": {
      "buttonIconSize": "22px",
      "removeIcon": { "library": "themify", "icon": "ti-close" }, "removeWordHidden": true, "removeIconSize": "14px",
      "removeBackground": { "hex": "#eeeeee" },
      "removeBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#333333" }, "radius": { "top": "50%", "right": "50%", "bottom": "50%", "left": "50%" } },
      "removePadding": { "top": "6", "right": "6", "bottom": "6", "left": "6" },
      "removeHoverBackground": { "hex": "#111111" }, "removeHoverColor": { "hex": "#ffffff" },
      "_cssClasses": "row-qty"
    } },
    { "name": "text-basic", "settings": { "text": "{woo_cart_subtotal}" } }
  ]
}
```

**Remove only, in a list of its own.** From the fixture "SHOP Q2: a cart page of its own layout" (`fixture-shop-custom-cart`, `.rm-qty`): a second Cart contents loop where each row is the name and a "Take out" button.

```json
{
  "name": "block",
  "settings": { "hasLoop": true, "query": { "objectType": "wooCart" }, "_direction": "row", "_columnGap": "16px" },
  "children": [
    { "name": "text-basic", "settings": { "text": "{woo_cart_product_name}" } },
    { "name": "bfbe-cart-quantity", "settings": { "shows": "remove", "removeWord": "Take out", "_cssClasses": "rm-qty" } }
  ]
}
```

## Gotchas

- **Outside a Cart contents row it prints nothing.** A products loop, a product page or a plain container gets no output; the builder shows "Place BFB Cart Quantity inside a Cart contents query loop." <!-- src: plugins/bfb-elements-pro/elements/cart-quantity.php:347-353 ; plugins/bfb-elements-pro/includes/shop/class-cart-parts.php:116-133 -->
- **Outside a Live cart region every change reloads the page.** The reload waits until the presses stop and the live answer has arrived, then puts the sentence and the focus back; WooCommerce's own cart refresh never redraws a Cart contents loop. <!-- src: src/elements/cart-quantity/cart-quantity.js:8-12 ; src/elements/cart-quantity/cart-quantity.js:78-106 -->
- **Some lines have no stepper.** A product sold individually, a BFB Offer line, a BFB Cart Goals gift and a line whose maximum is its minimum show the number as text; a gift has no Remove either. <!-- src: plugins/bfb-elements-pro/includes/shop/class-cart-parts.php:199-233 ; plugins/bfb-elements-pro/elements/cart-quantity.php:388-391 -->
- **The limits are WooCommerce's.** The minimum is at least 1, the maximum is the stock where it is managed without back-orders; a larger number is set to the maximum with WooCommerce's stock words, and a typed 0 removes the line. <!-- src: docs/elements/cart-quantity.md "The rules for each line" ; plugins/bfb-elements-pro/includes/shop/class-cart-parts.php:7-12 -->
- **A Form fields theme style reaches the number.** The **BFB Form fields** group's field border, padding and minimum height apply to every `input[type=number]`, the stepper's included; the demo resets them on `.bfbe-cartqty__input` with a rule of its own. <!-- src: plugins/bfb-elements/includes/shop/class-theme-styles.php:50 ; dev/demo/shop/lib.php:1064 -->
- **Icon only needs an icon.** `removeWordHidden` and `removeIconSize` show only with `removeIcon` set; the word goes, the name "Remove: …" stays for screen readers. <!-- src: plugins/bfb-elements-pro/elements/cart-quantity.php:91-98 ; plugins/bfb-elements-pro/elements/cart-quantity.php:278-288 ; plugins/bfb-elements-pro/elements/cart-quantity.php:414-418 -->
- **There is no Undo after a Remove here.** The row is redrawn away or the page reloads; Undo is the mini cart's (BFB Cart lines). <!-- src: docs/elements/cart-quantity.md "Limits" -->
- **Without the script each change is a form.** Plus and minus post one step, the number has an Update button, and WooCommerce's notice prints above the stepper of the changed line, since a page laid out with Bricks prints no notices of its own. <!-- src: plugins/bfb-elements-pro/elements/cart-quantity.php:384-398 ; plugins/bfb-elements-pro/includes/shop/class-cart-parts.php:251-263 -->
- **The canvas is inert.** In the builder the buttons do nothing and the number is read-only. <!-- src: plugins/bfb-elements-pro/elements/cart-quantity.php:398-407 -->

## Never do

- Do not place it outside a row of a Cart contents loop (`query.objectType: "wooCart"`).
- Do not put `bfbeLiveCart` on the looping element; put it on an element that holds the loop.
- Do not expect a stepper on a sold-individually, offer or gift line.
- Do not set `removeWordHidden` or `removeIconSize` without `removeIcon`.
- Do not leave a Form fields theme style's height and padding on the stepper's number; reset them under the element's class.
- Do not point CSS at the element's id; inside a loop use its class.
