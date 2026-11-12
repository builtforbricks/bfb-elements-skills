---
name: bfbe-hotspots
description: "Use when building an image with clickable pins, such as a shop-the-look photo, product tags, an annotated picture or one pin per post of a query (a product's linked features, placed by their own fields), with BFB Image Hotspots (`bfbe-hotspots`). Each pin is a real button that opens its own nested block beside the pin or as a card grown from the dot; read before writing its settings."
---

# BFB Image Hotspots (`bfbe-hotspots`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-hotspots.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/hotspots/

## What it is
An image with pins, each a real button that opens its own nested block as a tooltip or as a card grown from the pin. Each pin's expanded state is written into the HTML, opening a panel moves focus into it, and Escape returns focus to the pin. Color, size and icon can be set per pin in the same list, and a link can lie over a whole panel.

**Not for:** Pins sit at percentages of one picture, each a number or a post's own field, and each opens a block you place yourself. It does not zoom or pan, and it cannot make one pin per post of a query.

**Costs a page:** CSS 1.83 KB, JS 2.51 KB (gzipped), no dependencies, loaded only on pages that use it. Only where used, a product card in Image Hotspots and the Video Player: shop the look, and the add from a video moment: CSS 0.58 KB, JS 1.09 KB.

**Nestable:** yes · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Nestable: any Bricks element goes inside (blocks, headings, text, images, a form).
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-hotspots",
    "settings": {},
    "children": [
        {
            "name": "block",
            "settings": {}
        },
        {
            "name": "block",
            "settings": {}
        }
    ]
}
```

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Image (`bfbeImage`)
- `image` (image) **Image**. Choose the picture the pins sit on. With none chosen, the page draws nothing, while the builder shows a stand-in.
Styling, in the schema file: `imageBorder`.

### Pins (`bfbePins`)
- `pins` (repeater) **Pins**. One row per pin with its Name, Left (%) and Top (%), Text on the pin, Icon, Link on the whole panel, Colour and Size. Pin 2 opens the second block inside the element, and so on.
- `openOn` (select) **Opens on**: options: `click` Click (default), `hover` Hover and click. Click is the default. Hover and click also opens a panel when the pointer enters a pin.
- `pinIcon` (icon) **On every pin**. Choose an icon for every pin. A pin with its own Icon keeps it.
- `pulse` (checkbox) **Pulse**. Tick it to make a ring pulse from each pin at the Pulse speed, 2 seconds unless set.
Styling, in the schema file: `size`, `pinBackground`, `pinText`, `pinTypography`, `pinBorder`, `pinPadding`, `pinShadow`, `iconSize`, `iconColor`, `pulseColor`, `pinHoverBackground`.

### Panels (`bfbePanel`)
- `panelStyle` (select) **Panel**: options: `tooltip` Beside the pin (default), `expand` Grown from the pin. Beside the pin, a tooltip, is the default. Grown from the pin makes the dot itself grow into the card. Style each panel on its block's own Style tab.
- `expandFrom` (select) **Grows towards**: options: `auto` Where there is room (default), `tl` Right and down, `tr` Left and down, `bl` Right and up, `br` Left and up; only when `panelStyle` is `expand`. Where there is room is the default. Pick Right and down, Left and down, Right and up or Left and up so the card extends from the pin's position.
- `placement` (select) **Panel side**: options: `auto` Wherever there is room (default), `top` Top, `bottom` Bottom, `left` Left, `right` Right; only when `panelStyle` is not `expand`. Wherever there is room is the default. Pick Top, Bottom, Left or Right to choose a side. The tooltip flips to the other side when it would not fit.
Styling, in the schema file: `panelMinWidth`, `panelBlur`.

### Motion (`bfbeMotion`)
- `panelEffect` (select) **Panel effect**: options: `fade` Fade (default), `rise` Rise, `scale` Scale, `none` None. Choose how a panel appears: Fade (the default), Rise, Scale or None.
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS. Snappy by default. Pick another curve from the list, or Custom to type your own in Custom curve.
Styling, in the schema file: `duration`, `easingCustom`, `pulseSpeed`, `pulseScale`.

### In the builder (`bfbeBuilder`)
- `builderView` (select) **Show it**: options: `open` Open, so you can style them (default), `closed` Closed, as the site leaves it, `live` Working, as on the site. Open, the default, lays the panels out for styling, Closed matches the site at rest, and Working lets a click open a panel in the canvas.

## What it guarantees for accessibility (do not undo)
- Each pin is a native button whose aria-expanded is in the server-rendered HTML, with aria-controls naming its own panel.
- Enter or Space opens a panel and moves focus into it; Escape closes it and returns focus to the pin.
- A pin's name is its visible text plus a hidden Name, which reads Pin and its number when empty.
- With Hover and click, a panel also opens as the pointer enters a pin; keyboard focus on a pin does not open it.
- A pin's link is a real anchor laid over the panel and labeled with the pin's name.
- Under reduced motion the pulse is switched off and panels beside the pin open without a transition.
- A product pin's accessible name is its product's name.
<!-- bfbe:generated:end -->

## Rendered DOM

The fixture's numbered tooltip after the script has run, trimmed (`is-ready`, the panel class, `popover`, `tabindex`, the wrapper and the inline hiding are the script's):

```html
<div id="brxe-770918" class="brxe-bfbe-hotspots bfbe-hotspots bfbe-hotspots--fx-fade bfbe-hotspots--pulse is-ready"
     data-bfbe-open-on="click" data-bfbe-placement="auto" data-bfbe-style="tooltip" data-bfbe-from="auto">
  <div class="bfbe-hotspots__stage">
    <img class="bfbe-hotspots__img" src="..." alt="(the attachment's own alt text)">
    <div class="bfbe-hotspots__pins">
      <button type="button" class="bfbe-hotspots__pin" style="left:56%;top:14%" aria-expanded="false"
              aria-controls="brxe-a3c167" data-bfbe-pin="0" data-bfbe-x="56" data-bfbe-y="14">
        <span class="bfbe-hotspots__text">1</span><span class="bfbe-sr"> Sofa</span></button>
    </div>
  </div>
  <div class="bfbe-hotspots__panels">
    <div id="brxe-a3c167" class="brxe-block bfbe-hotspots__panel" popover="auto" tabindex="-1" style="display: none;">
      <div class="bfbe-hotspots__inner">...the block's own children...</div>
    </div>
  </div>
</div>
```

- Root: `bfbe-hotspots--fx-fade`, `--fx-rise`, `--fx-scale` or `--fx-none` from **Panel effect**; `bfbe-hotspots--pulse` when **Pulse** is ticked; `is-ready` once the script has run. Builder canvas alone: `bfbe-hotspots--canvas` (Open view), `bfbe-hotspots--still` (Closed), `data-bfbe-live="1"` (Working).
- Pins: a `<button>` per pin that has a block, `aria-expanded` toggled on open, `data-bfbe-pin` counted from 0. `bfbe-hotspots__pin--dot` when nothing visible is inside (a circle of the Size); a pin with no block is a `<span class="bfbe-hotspots__pin bfbe-hotspots__pin--plain">`. An icon is `.bfbe-hotspots__icon`; the pulse ring is `.bfbe-hotspots__pin::before`.
- Beside the pin: each block becomes a `popover="auto"` in the top layer, `position: fixed`, with `data-side` naming the side it opened on; open reads `:popover-open` (`.is-shown` where popovers are missing).
- Grown from the pin: the holder is `.bfbe-hotspots__panels.bfbe-hotspots__panels--in`, inside the stage after the pins. Each block is `inert` until open and `.is-shown` when open, with `data-bfbe-corner` (`tl`, `tr`, `bl`, `br`) and inline `--bfbe-hs-w`, `--bfbe-hs-h`, `--bfbe-hs-r-*` measured from the block; `.bfbe-hotspots__inner` carries the block's padding inline.
- A pin's **Link on the whole panel** adds `.bfbe-hotspots__panel--link` and a last child `<a class="bfbe-hotspots__link" aria-label="(pin name)">`.
- **A product pin** (WooCommerce, **Shows** `bfbeShopContent: "product"`) is the same `<button>` plus `data-bfbe-block="<block id>"`, its hidden name the product's name. Its block renders as a one-row query loop of type `bfbeShopPinProduct`, so it carries Bricks' looping class `brxe-<id>`, and every element in that row keeps its `id` (Pro gives it back), so the block's Style tab and its children's still apply. Bricks' empty `.brx-query-trail` after the loop is hidden. A product pin lays no link over its panel. With its product gone, it is the plain `<span>` and its block draws nothing.
- **Pins from a query (2.1.0).** A pin whose block loops prints, in its place among the pins, `<div class="bfbe-hotspots__pin bfbe-hotspots__pin--rows">` (`display: contents`, no pulse of its own) holding one `<button class="bfbe-hotspots__pin">` per result. Each carries `data-bfbe-block="<block id>"`, `data-bfbe-row` (from 0), its own `data-bfbe-x` and `data-bfbe-y`, and inline `--bfbe-hs-pin:inherit;--bfbe-hs-size:inherit`, so the listed pin's Colour and Size reach every copy. On the page each repeated block gets the id `bfbe-hsq-<block id>-<n>`, which the pin's `aria-controls` names.
- Where controls write: `size`, `pinBackground`, `pinText`, `pinHoverBackground`, `iconSize`, `iconColor`, `pulseColor`, `panelMinWidth`, `panelBlur` to root variables (`--bfbe-hs-size`, `--bfbe-hs-pin`, `--bfbe-hs-text`, `--bfbe-hs-pin-hover`, `--bfbe-hs-icon`, `--bfbe-hs-icon-color`, `--bfbe-hs-pulse`, `--bfbe-hs-panel-min`, `--bfbe-hs-panel-blur`); `duration`, `easing` to `--bfbe-duration`, `--bfbe-ease`; `pinTypography`, `pinBorder`, `pinPadding`, `pinShadow` to `.bfbe-hotspots__pin`; per pin `pinColor`, `pinSize` to `.bfbe-hotspots__pin:nth-child(n)`; `imageBorder` to `.bfbe-hotspots__img`. No element control paints the panel: its look is the block's.

## Wiring to other elements

- **Pins to blocks, by position.** Pin n opens the element's nth direct child, whatever element it is. `aria-controls` names the child's `brxe-<id>`; where Bricks prints no id (a component, a query loop, "element attributes as needed"), the script falls back to the position and gives the block the id `bfbe-hs-<n>`.
- **Pins from a query (2.1.0).** Give a pin's nested Block, Container, Div or Section Bricks' **Use query loop** (`hasLoop: true` and `query` on that block, a Bricks query: posts, or an ACF Relationship field as `"objectType": "acf_<field name>"`, are the measured ones). The pin then repeats once per result, its block once per result. Its **Left (%)** `x`, **Top (%)** `y`, **Name** `name`, **Text on the pin** `label` and **Link on the whole panel** `link` are read in each result's context: `{acf_pin_x}` and `{acf_pin_y}` place each post's pin, `{acf_feature_no}` numbers it, and a link of `{"type": "external", "url": "{post_url}"}` opens the post. Listed pins and looping pins mix in one `pins` list, still one block per row.
- Find the element or a panel by a class in `_cssClasses`, never `_cssId`: component instances share ids, and a panel's id may be one the script gave it. Several panels styled alike take one global class on their blocks.
- **Product pins (shop the look, 2.0.0).** With WooCommerce active, each pin row gains **Shows** `bfbeShopContent` (`block`, the default, or `product`), **Product** `bfbeShopProduct` (a product id, as a string) and **Or from dynamic data** `bfbeShopProductFrom` (a tag giving an id or SKU, read for the post or loop row, such as `{cf_look_product}`). A product pin's **Name** and **Link on the whole panel** are not offered. Its nested block holds Bricks' own **Product title**, **Product price**, **Add to cart** and an **Image** of `{featured_image}`, laid out with Bricks' Block, Container and Div; Add to cart's own swatches and BFB groups work there (`bfbe-shop-add-to-cart`).
- **The pinned products elsewhere.** A Shop products loop with the set **Pinned on an image** (`bfbeShopSet: "hotspots"`) lists a picture's product pins, in pin order, anywhere on the page; its **Element id** `bfbeShopHotspots` is empty for the nearest Image Hotspots. See `bfbe-shop-loops`; it replaces the list this element printed under the picture before 2.0.0 shipped, and the element itself has no list or card controls.
- **Out.** It dispatches no event. Read `aria-expanded` on `.bfbe-hotspots__pin`; beside the pin, each panel also fires the browser's `toggle` event.
- **Re-running.** `window.bfbeHotspots()` initialises every `.bfbe-hotspots`; the script calls it after `bricks/ajax/pagination/completed`, `bricks/ajax/load_page/completed`, `bricks/ajax/query_result/displayed` and `bricks/ajax/popup/loaded`, so it works inside an AJAX popup.
- **BFB Dark Mode Toggle.** In its dark state a pin's words turn black or white from the fill, unless **Text colour** `pinText` is set. The class `bfbe-keep` in `_cssClasses` keeps the toggle's page recolour off the element and everything in it, pins and panels included.
- Apart from the Pinned on an image loop, no other BFB element targets it, and it targets none.

## Verified patterns

**Shop the look: dark cards grown from pulsing dots.** From the demo page `demo-bfb-hotspots`. `panelStyle: "expand"` grows each card out of its 22px white dot and `pulse` rings the dots; the card's look is on each block. The image `url` is replaced with https://example.com/..., and `3143` is the demo site's media id: use an attachment id from the target site.

```json
{
  "name": "bfbe-hotspots",
  "settings": {
    "image": {"id": 3143, "filename": "bfbe-demo-hollis-velvet.jpg", "size": "full", "url": "https://example.com/wp-content/uploads/bfbe-demo-hollis-velvet.jpg", "full": "https://example.com/wp-content/uploads/bfbe-demo-hollis-velvet.jpg"},
    "panelStyle": "expand",
    "size": "22px",
    "pinBackground": {"hex": "#ffffff"},
    "pinBorder": {"width": {"top": 5, "right": 5, "bottom": 5, "left": 5}, "style": "solid", "color": {"rgb": "rgba(255, 255, 255, 0.4)"}},
    "pulse": true,
    "pins": [{"name": "Jacket", "x": 43, "y": 47}, {"name": "Trousers", "x": 47, "y": 76}, {"name": "Shirt", "x": 52, "y": 35}]
  },
  "children": [
    {"name": "block", "settings": {"_direction": "column", "_rowGap": "4px", "_background": {"color": {"hex": "#101828"}}, "_typography": {"color": {"hex": "#ffffff"}}}, "children": [{"name": "text-basic", "settings": {"text": "The velvet jacket, £420", "tag": "p"}}, {"name": "text-basic", "settings": {"text": "Cotton velvet, half-canvassed, a single vent.", "tag": "p"}}]},
    {"name": "block", "settings": {"_direction": "column", "_rowGap": "4px", "_background": {"color": {"hex": "#101828"}}, "_typography": {"color": {"hex": "#ffffff"}}}, "children": [{"name": "text-basic", "settings": {"text": "The trousers, £260", "tag": "p"}}, {"name": "text-basic", "settings": {"text": "Flat front, a touch of taper.", "tag": "p"}}]},
    {"name": "block", "settings": {"_direction": "column", "_rowGap": "4px", "_background": {"color": {"hex": "#101828"}}, "_typography": {"color": {"hex": "#ffffff"}}}, "children": [{"name": "text-basic", "settings": {"text": "The Crew, in cream, £160", "tag": "p"}}, {"name": "text-basic", "settings": {"text": "Under a suit or over a shirt.", "tag": "p"}}]}
  ]
}
```

**Numbered notes beside the pin.** From the fixture page `fixture-hotspots` ("Beside the pin, on click, with numbers and a pulse"). `label` puts a number on each pin, `pinText` makes it dark on the white fill, and pin 2's own `pinColor` turns it amber. The frosted look on each block is the fixture's own, and `panelBlur` softens the photo under it. Image `url` replaced with https://example.com/...; `969` is the development site's media id, so use the target site's own.

```json
{
  "name": "bfbe-hotspots",
  "settings": {
    "_cssClasses": "bfbe-keep",
    "image": {"id": 969, "filename": "bfbe-living-room.jpg", "size": "full", "url": "https://example.com/wp-content/uploads/bfbe-living-room.jpg", "full": "https://example.com/wp-content/uploads/bfbe-living-room.jpg"},
    "size": "24px",
    "pinBackground": {"hex": "#ffffff"},
    "pinText": {"hex": "#111111"},
    "pinBorder": {"width": {"top": "6", "right": "6", "bottom": "6", "left": "6"}, "style": "solid", "color": {"rgb": "rgba(255, 255, 255, 0.45)"}},
    "panelBlur": "14px",
    "pulse": true,
    "pins": [{"name": "Sofa", "x": 56, "y": 14, "label": "1"}, {"name": "Coffee table", "x": 39, "y": 47, "label": "2", "pinColor": {"hex": "#e0a020"}}]
  },
  "children": [
    {"name": "block", "settings": {"_background": {"color": {"rgb": "rgba(255, 255, 255, 0.82)"}}, "_typography": {"color": {"hex": "#111111"}, "font-size": "15px"}, "_widthMax": "260px", "_padding": {"top": 16, "right": 18, "bottom": 18, "left": 18}}, "children": [{"name": "heading", "settings": {"text": "Sofa", "tag": "h3"}}, {"name": "text-basic", "settings": {"text": "Three seats, light grey. 1,290 €"}}]},
    {"name": "block", "settings": {"_background": {"color": {"rgb": "rgba(255, 255, 255, 0.82)"}}, "_typography": {"color": {"hex": "#111111"}, "font-size": "15px"}, "_widthMax": "260px", "_padding": {"top": 16, "right": 18, "bottom": 18, "left": 18}}, "children": [{"name": "heading", "settings": {"text": "Coffee table", "tag": "h3"}}, {"name": "text-basic", "settings": {"text": "Turned teak. 420 €"}}]}
  ]
}
```

**Linked product cards, opened on hover.** From `fixture-hotspots` ("a link on the whole card, 500ms"), two of its four pins kept. Each pin's `link` lays a real anchor over its card, `newTab` on the first; `openOn: "hover"` opens a card as the pointer enters its dot, and `duration: 500` slows the growth. Image `url` replaced with https://example.com/...; `968` is the development site's media id.

```json
{
  "name": "bfbe-hotspots",
  "settings": {
    "image": {"id": 968, "filename": "bfbe-outfit.jpg", "size": "full", "url": "https://example.com/wp-content/uploads/bfbe-outfit.jpg", "full": "https://example.com/wp-content/uploads/bfbe-outfit.jpg"},
    "panelStyle": "expand",
    "openOn": "hover",
    "duration": 500,
    "size": "24px",
    "pinBackground": {"hex": "#ffffff"},
    "pins": [{"name": "Wool coat", "x": 32, "y": 60, "link": {"type": "external", "url": "https://example.com/wool-coat", "newTab": true}}, {"name": "Chain bag", "x": 24, "y": 92, "link": {"type": "external", "url": "https://example.com/chain-bag"}}]
  },
  "children": [
    {"name": "block", "settings": {"_background": {"color": {"rgb": "rgba(255, 255, 255, 0.82)"}}, "_widthMax": "260px", "_padding": {"top": 16, "right": 18, "bottom": 18, "left": 18}}, "children": [{"name": "heading", "settings": {"text": "Wool coat", "tag": "h3"}}, {"name": "text-basic", "settings": {"text": "Cream, double breasted. 290 €"}}]},
    {"name": "block", "settings": {"_background": {"color": {"rgb": "rgba(255, 255, 255, 0.82)"}}, "_widthMax": "260px", "_padding": {"top": 16, "right": 18, "bottom": 18, "left": 18}}, "children": [{"name": "heading", "settings": {"text": "Chain bag", "tag": "h3"}}, {"name": "text-basic", "settings": {"text": "Black and silver. 240 €"}}]}
  ]
}
```

**Shop the look: pins that show products.** From the demo shop's lookbook page (`lookbook`, the living room), two of its nine pins, with the dev site's media id `79059` and product ids `79028` and `78883` in place of the demo's: use the target site's own. Each pin's block is set to Query loop, type BFB Pin product, so it keeps its product in the builder too; Bricks' product elements inside it read the pin's product. Trimmed: the demo's pin look, the card's layout blocks and every style on Add to cart.

```json
{
  "name": "bfbe-hotspots",
  "settings": {
    "image": {"id": 79059, "filename": "wool-throw-blanket.png", "size": "large", "url": "https://example.com/wp-content/uploads/wool-throw-blanket.png", "full": "https://example.com/wp-content/uploads/wool-throw-blanket.png"},
    "size": "30px",
    "pinBackground": {"hex": "#ffffff"},
    "pinText": {"hex": "#101828"},
    "pulse": true,
    "panelMinWidth": "280px",
    "pins": [{"x": 51, "y": 50, "bfbeShopContent": "product", "bfbeShopProduct": "79028"}, {"x": 14, "y": 58, "bfbeShopContent": "product", "bfbeShopProduct": "78883"}]
  },
  "children": [
    {"name": "block", "settings": {"hasLoop": true, "query": {"objectType": "bfbeShopPinProduct"}}, "children": [
      {"name": "image", "settings": {"image": {"useDynamicData": "{featured_image}", "size": "woocommerce_thumbnail"}}},
      {"name": "product-title", "settings": {"tag": "h4", "linkToProduct": true}},
      {"name": "product-price", "settings": {}},
      {"name": "product-add-to-cart", "settings": {}}
    ]},
    {"name": "block", "settings": {"hasLoop": true, "query": {"objectType": "bfbeShopPinProduct"}}, "children": [
      {"name": "image", "settings": {"image": {"useDynamicData": "{featured_image}", "size": "woocommerce_thumbnail"}}},
      {"name": "product-title", "settings": {"tag": "h4", "linkToProduct": true}},
      {"name": "product-price", "settings": {}},
      {"name": "product-add-to-cart", "settings": {}}
    ]}
  ]
}
```

**Pins placed by each post's own fields, in a query loop.** From the fixture `fixture-hotspots-loop` (1.3.0): the element sits in a Block with **Use query loop** (`hasLoop` and `query` on the Block), and each pin's `x` and `y` are dynamic tags, here two ACF number fields, so every post places its pins from its own values. A pin can mix a tag on one axis with a number on the other.

```json
{
  "name": "bfbe-hotspots",
  "settings": {
    "image": {"id": 3143, "size": "large", "url": "https://example.com/wp-content/uploads/room.jpg"},
    "builderView": "live",
    "pins": [{"name": "{post_title}", "x": "{acf_pin_left}", "y": "{acf_pin_top}"}, {"name": "Detail", "x": 10, "y": 90}]
  },
  "children": [
    {"name": "block", "children": [{"name": "text-basic", "settings": {"text": "{post_excerpt}"}}]},
    {"name": "block", "children": [{"name": "text-basic", "settings": {"text": "A fixed second pin."}}]}
  ]
}
```

**One numbered pin per post, from a query (2.1.0).** From the fixture `fixture-hotspots-armchair` (the wide crop): one pin row and one block that loops, so five feature posts give five pins, each placed by its post's ACF number fields and numbered by a third. The card is the block's own Style tab, designed once. The fixture's post type and post ids are replaced by `post` and `menu_order`: use the site's own type. Media id `89968` is the development site's; image `url` replaced with https://example.com/....

```json
{
  "name": "bfbe-hotspots",
  "settings": {
    "image": {"id": 89968, "size": "full", "url": "https://example.com/wp-content/uploads/armchair-wide.jpg"},
    "size": "34px",
    "pinBackground": {"hex": "#1f3a33"},
    "pinText": {"hex": "#ffffff"},
    "pulse": true,
    "pins": [{"x": "{acf_bfbe_feat_wx}", "y": "{acf_bfbe_feat_wy}", "label": "{acf_bfbe_feat_no}"}],
    "_cssClasses": "armchair-wide"
  },
  "children": [
    {"name": "block", "settings": {"hasLoop": true, "query": {"objectType": "post", "post_type": ["post"], "orderby": "menu_order", "order": "ASC", "posts_per_page": 5}, "_rowGap": "6px", "_widthMax": "280px", "_background": {"color": {"hex": "#1f3a33"}}, "_typography": {"color": {"hex": "#ffffff"}}}, "children": [
      {"name": "heading", "settings": {"text": "{post_title}", "tag": "h4"}},
      {"name": "text-basic", "settings": {"text": "{post_excerpt}"}}
    ]}
  ]
}
```

**A product's linked posts, one pin each, beside a listed pin (2.1.0).** From the product template `bfbe-hsrel-product`: the picture is the product's `{featured_image}`, pin 1 is a listed pin, and pin 2's block loops over the product's ACF Relationship field `bfbe_hs_features` (Bricks' query type `acf_bfbe_hs_features`). Each linked post's pin is placed by its own fields, named for its post (no `name`) and links to it; its `pinColor` colours every copy. Three linked posts give three pins, none gives none.

```json
{
  "name": "bfbe-hotspots",
  "settings": {
    "image": {"useDynamicData": "{featured_image}", "size": "large"},
    "_cssClasses": "hsrel",
    "pins": [
      {"name": "Plain", "x": 10, "y": 90},
      {"x": "{acf_bfbe_hs_x}", "y": "{acf_bfbe_hs_y}", "link": {"type": "external", "url": "{post_url}"}, "pinColor": {"hex": "#0000ff"}}
    ]
  },
  "children": [
    {"name": "block", "children": [{"name": "text-basic", "settings": {"text": "Block of Plain"}}]},
    {"name": "block", "settings": {"hasLoop": true, "query": {"objectType": "acf_bfbe_hs_features"}}, "children": [{"name": "text-basic", "settings": {"text": "About {post_title}"}}]}
  ]
}
```

## Gotchas

- **No picture, no output.** With `image` empty the page renders nothing, while the canvas shows Bricks' placeholder photograph. An `id` that is not an attachment on this site also renders nothing, even beside a working `url`; an image with no `id` falls back to its `url`. <!-- src: plugins/bfb-elements-pro/elements/hotspots.php:500, :508, :515; measured 2026-10-08 through bfbe_defaults_render: id 999999 with an https url rendered 0 bytes, the url alone rendered -->
- **Alt text comes from the media library.** The element has no alt control: with an `id` the image takes the attachment's Alternative Text, and an image given by `url` alone gets `alt=""`. <!-- src: plugins/bfb-elements-pro/elements/hotspots.php:501, :503; measured 2026-10-08: id 3143 printed its library alt -->
- **Pins and blocks pair by position, and the insert tree has no pins.** As inserted there are two empty blocks and no `pins`, so nothing opens. A pin with no block is a `<span>` that opens nothing; a block past the last pin is never hidden and shows under the picture. The notices "Add a pin." and "One nested block per pin." stay in the canvas. <!-- src: plugins/bfb-elements-pro/elements/hotspots.php:419, :592, :595, :674, :683; src/elements/hotspots/hotspots.js:99; measured 2026-10-08 on a planted copy of the fixture: the extra block display flex, 63px tall -->
- **The panel's look is the block's own Style tab.** The element sets **Min width** `panelMinWidth` and **Blur behind** `panelBlur`; background, padding, border, corners, shadow and width go on each block, which outranks the defaults (Canvas, `.9em 1.1em`, 8px corners). Blur behind shows through a translucent block background alone. <!-- src: docs/elements/hotspots.md "Round 412"; src/elements/hotspots/hotspots.css:73, :89 -->
- **A panel is as narrow as its content allows.** It sizes to `min-content` and never under **Min width** (240px unset), so a paragraph wraps at 240px. Set **Width** `_width` on the block, or `panelMinWidth`, for a wider card. <!-- src: src/elements/hotspots/hotspots.css:78, :79; docs/elements/hotspots.md "Round 412"; measured 2026-10-08: 240px open, wider with a width on the block -->
- **The picture draws at its own pixel width.** The stage is `fit-content` and the image is never stretched, so the chosen `size` sets the width, capped by the container and placed at its start. The fixture's `large` (896px) sat left in an 1100px container. <!-- src: src/elements/hotspots/hotspots.css:19, :20; measured 2026-10-08 on fixture-views-hotspots -->
- **A light pin gets light words.** A pin's text and icon default to the page's `Canvas` colour, so a white `pinBackground` with **Text colour** `pinText` unset reads white on white. Set `pinText`, and `iconColor` for an icon, with any light fill. <!-- src: src/elements/hotspots/hotspots.css:6, :55; docs/elements/hotspots.md "Round 394" -->
- **Grown from the pin drops the pin's text and the Panel effect.** With `panelStyle: "expand"`, **Text on the pin** `label` is not rendered and **Panel effect** `panelEffect` changes nothing; `duration` and `easing` still time the growth. The dot does not scale on hover in this style. <!-- src: plugins/bfb-elements-pro/elements/hotspots.php:626; src/elements/hotspots/hotspots.css:113, :144, :167; measured 2026-10-08: transition 0.7s under fx-none, transform none under fx-rise -->
- **Where there is room means where the pin sits.** With **Grows towards** `expandFrom` on `auto`, a pin past 55% down grows up and past 55% across grows left; the viewport is not consulted. <!-- src: src/elements/hotspots/hotspots.js:110 -->
- **A link takes the pointer from the panel's content.** With a pin's `link`, everything in the panel but links and buttons ignores clicks, so a form field there cannot be used. A link is laid for http, https, mailto, tel and relative addresses. <!-- src: src/elements/hotspots/hotspots.css:171, :172; src/elements/hotspots/hotspots.js:139 -->
- **Closed panels are hidden inline.** The script puts `display: none` inline on each closed panel, which outranks a Display set on the block; a `display` with `!important` beats it and keeps the panel on screen after it closes. <!-- src: src/elements/hotspots/hotspots.js:118; docs/elements/hotspots.md "Every starter card showed on the site"; measured 2026-10-08: display flex, 99px tall after a close -->
- **Left and Top take dynamic data (1.3.0).** `x` and `y` accept a tag (`{acf_...}`, `{cf_...}`) as well as a number. The tag is resolved per post, then read as a percentage: a decimal comma reads as a point, a value outside 0 to 100 is held to the edge, and a tag that resolves empty (the post has no value) puts the pin in the middle, at 50. Before Pro 1.3.0 a tag there read as 0. <!-- src: plugins/bfb-elements-pro/elements/hotspots.php:86, :95, :482, :621; docs/elements/hotspots.md "Pin positions from dynamic data (1.3)"; measured 2026-10-16 with dev/hotspots-loop-probe.cjs, 27 readings on Bricks 2.4.2 and 2.3.10 -->
- **In a query loop the pins follow the post, their number does not.** Each pin's **Name** `name`, **Text on the pin** `label` and position resolve per post, but every post has the same number of pins and the same nested blocks, filled by their own tags. For one pin per result, loop the pin's block instead (2.1.0, below). <!-- src: plugins/bfb-elements-pro/elements/hotspots.php:621-641; measured 2026-10-16 on Bricks 2.4.2: three posts, each pin's name and text its own post title, each position its own fields -->
- **A looping block repeats its pin, from Pro 2.1.0.** Only a Block, Container, Div or Section with `hasLoop` does, only when there is one block per pin row, and never for a product pin (`bfbeShopContent: "product"`). A query with no results gives no pin, and the row's other pins stay. <!-- src: plugins/bfb-elements-pro/elements/hotspots.php:612-631, :834, :856 ; docs/elements/hotspots.md "Pins from a query (2.1)" -->
- **At most 200 pins from one block.** Results past the 200th get no pin, so give the block's query a limit. <!-- src: plugins/bfb-elements-pro/elements/hotspots.php:46-47, :862 -->
- **A pin with no Name takes its post's title.** Only in a loop of posts (an ACF Relationship of posts included); over terms or users an empty Name reads "Pin" and its number, so set `name` there. <!-- src: plugins/bfb-elements-pro/elements/hotspots.php:762-766 -->
- **Colour and Size belong to the row, not the result.** A looping pin's own `pinColor` and `pinSize` apply to every pin it repeats into; for a colour per result, use a tag in Text on the pin or the block's content. <!-- src: plugins/bfb-elements-pro/elements/hotspots.php:684-694, :801 ; docs/elements/hotspots.md "Pins from a query (2.1)" -->
- **Results loaded later get no pin.** The pins are drawn with the page, so a block whose loop adds results by AJAX (infinite scroll, Load more, live filters) shows those blocks with no pins. <!-- src: docs/elements/hotspots.md "Pins from a query (2.1)" -->
- **The canvas runs the query as last saved.** In the builder the pins come from the block's saved query; save after changing it to see its pins. The Working view opens each pin's own block. <!-- src: plugins/bfb-elements-pro/elements/hotspots.php:626-629, :873-888 ; docs/elements/hotspots.md "Pins from a query (2.1)" -->
- **A position is a percentage of one picture.** For another crop at a breakpoint, place a second Image Hotspots with its own picture and its own pair of fields, and hide one per breakpoint with `_display`. <!-- src: dev/fixtures/hotspots-armchair.php:113-163 -->
- **A product pin's block must be a Block, Container or Div.** Only those are given the Pin product loop as they render; another element there shows no product. A variation picked by SKU shows its parent product, and the options are Add to cart's to choose. <!-- src: plugins/bfb-elements-pro/includes/shop/class-hotspot-products.php:142-145, 212-220 --> <!-- src: docs/elements/hotspots.md "In a shop: shop the look (2.0.0)" -->
- **In the builder, set the block's loop yourself.** The page needs no step, but in the canvas an element edited inside a product pin's block without `hasLoop` and `query.objectType: "bfbeShopPinProduct"` draws for the page instead, and a notice names the pins. The canvas reads pins from the saved page, so a product just picked shows after a save; until found, the shop's first product stands in. <!-- src: plugins/bfb-elements-pro/elements/hotspots.php:598-607 --> <!-- src: plugins/bfb-elements-pro/includes/shop/class-pin-product.php:70-75 --> <!-- src: docs/elements/hotspots.md "In a shop: shop the look (2.0.0)" -->
- **A product pin whose product is gone opens nothing.** A deleted product, or a tag with no answer on this post, makes it a plain pin and its block draws nothing; nothing warns on the page. <!-- src: plugins/bfb-elements-pro/elements/hotspots.php:660-671 -->
- **A product pin keeps no name or link of its own.** `name` and `link` are hidden for `bfbeShopContent: "product"`, and the pin is named for its product; **Text on the pin** `label`, Icon, Colour and Size still apply. <!-- src: plugins/bfb-elements-pro/includes/shop/class-hotspot-products.php:84-89 --> <!-- src: plugins/bfb-elements-pro/elements/hotspots.php:632-634 -->
- **The canvas is not the page.** **Show it** `builderView` defaults to Open: every panel listed under the picture in the default look, grown ones outside the stage. Closed shows the picture and its pins; Working opens a panel on click, as the site does. <!-- src: plugins/bfb-elements-pro/elements/hotspots.php:559, :695; src/elements/hotspots/hotspots.css:179, :185 -->

## Never do

- Do not leave `image` empty or carry a media `id` from another site; use an attachment id from the target site.
- Do not let `pins` and the nested blocks fall out of step: one block per pin, in the same order, nothing else as a direct child.
- Do not set `expandFrom` without `panelStyle: "expand"`, or `placement` with it; do not set `pulseColor`, `pulseSpeed` or `pulseScale` without `pulse: true`.
- Do not style panels through `.bfbe-hotspots__panel` in custom CSS; set the look on each block's Style tab.
- Do not give a panel block `display` with `!important`.
- Do not put form fields in a panel whose pin has a `link`.
- Do not write a tag into `x` or `y` for a site on Pro older than 1.3.0; there it reads as 0, the top left corner.
- Do not give a product pin (`bfbeShopContent: "product"`) a `name` or a `link`, or a nested element other than a Block, Container or Div.
- Do not leave a product pin's block without `hasLoop` and `query.objectType: "bfbeShopPinProduct"` when it will be edited in the builder.
- Do not loop a pin's block on a site older than Pro 2.1.0, or with fewer blocks than pin rows, and expect a pin per result.
- Do not leave a looping pin's block query without a limit, or rely on results loaded by AJAX getting pins.
- Do not find the element or a panel by `_cssId`; use a class in `_cssClasses`.
- Do not set `popover`, `tabindex` or `aria-*` on the panel blocks or the pins; the element and its script set them.
