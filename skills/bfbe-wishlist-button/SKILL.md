---
name: bfbe-wishlist-button
description: "Use when adding a save-to-wishlist toggle to a product page, a product card or a loop of posts, or a wishlist count with a heart for the header, with BFB Wishlist Button (`bfbe-wishlist-button`). Read before writing its settings."
---

# BFB Wishlist Button (`bfbe-wishlist-button`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-wishlist-button.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/wishlist-button/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 1.02 KB, JS none (gzipped), no dependencies, loaded only on pages that use it.

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Ungrouped
- `shows` (select) **Shows**: options: `button` The button (default), `count` A count for the header

### Button (`bfbeButton`)
The whole group shows only when `shows` is not `count`.
- `postType` (select) **Saves**: options: `product` Products (default), `post` Posts, `page` Pages, `bfbe_review` Review, `bfbe_feature` Feature visuals, `bricks_template` My Templates
- `textAdd` (text) **Words to add**: placeholder Add to wishlist; dynamic data accepted
- `textOn` (text) **Words when saved**: placeholder In your wishlist; dynamic data accepted
- `content` (select) **Button shows**: options: `both` Icon and words (default), `icon` Icon only, `words` Words only
- `iconAdd` (icon) **Icon to add**: only when `content` is not `words`
- `iconOn` (icon) **Icon when saved**: only when `content` is not `words`

### Header count (`bfbeCount`)
The whole group shows only when `shows` is `count`.
- `countHide` (select) **Hide while empty**: options: `on` On (default), `off` Off. Appears once something is added, with no reload.
- `countPlace` (select) **Badge place**: options: `corner` Over the icon corner (default), `beside` Beside the icon
- `countIcon` (icon) **Icon**
Styling, in the schema file: `countIconSize`, `countIconColor`, `countBadgeBg`, `countBadgeColor`, `countBadgeSize`, `countBadgeBorder`, `countBadgeTypography`.

### Look (`bfbeLook`)
The whole group shows only when `shows` is not `count`.
- `iconPlace` (select) **Icon sits**: options: `row` Before the words (default), `row-reverse` After the words; writes CSS; only when `content` is not `icon` or `words`
Styling, in the schema file: `btnType`, `btnBackground`, `btnBorder`, `btnShadow`, `btnPadding`, `hoverBackground`, `hoverColor`, `hoverBorderColor`, `iconSize`, `iconColor`, `gap`, `onBackground`, `onColorText`, `onBorderColor`, `onColor`.
<!-- bfbe:generated:end -->

## Rendered DOM

Two shapes, chosen by **Shows** (`shows`). The button (`button`, the default) is a real form with one toggle:

```html
<form id="brxe-{id}" class="brxe-bfbe-wishlist-button bfbe-list bfbe-wish bfbe-list--both" method="post"
      data-bfbe-list="wishlist" data-bfbe-list-act="list_toggle" data-bfbe-shop-need="wishlist"
      data-bfbe-list-off="Add to wishlist: Linen Shirt" data-bfbe-list-on="In your wishlist: Linen Shirt" data-bfbe-list-var="1">
  <input type="hidden" name="bfbe_shop_act" value="list_toggle"> <!-- + _bfbe_nonce when signed in, kind, product, variation -->
  <button type="submit" class="bfbe-list__btn" aria-pressed="false" aria-label="Add to wishlist: Linen Shirt">
    <span class="bfbe-list__icon bfbe-list__icon--add" aria-hidden="true"><svg …></span><span class="bfbe-list__icon bfbe-list__icon--on" aria-hidden="true"><svg …></span>
    <span class="bfbe-list__word bfbe-list__word--add">Add to wishlist</span><span class="bfbe-list__word bfbe-list__word--on">In your wishlist</span>
  </button>
</form>
```

- `bfbe-list--both`, `--icon` or `--words` follows **Button shows** (`content`); Icon only leaves out the words' spans, Words only the icons'. `data-bfbe-list-var="1"` marks a variable product.
- Both states are always in the markup. CSS shows one from `aria-pressed` alone, never from a class, so style the saved state on `.bfbe-list__btn[aria-pressed="true"]`.
- The script sets `aria-pressed` and swaps `aria-label` between the two `data-bfbe-list-*` names after each answer, and sets `aria-busy="true"` while it posts.
- Where Look writes: `btnPadding`, `btnType`, `btnBorder`, `btnShadow`, the hover keys and `iconPlace` (`flex-direction`) to `.bfbe-list__btn`; `btnBackground`, `onBackground`, `iconSize`, `iconColor`, `gap` and `onColor` to `--bfbe-list-*` properties on the root; `onColorText` and `onBorderColor` to the pressed button.

The header count (`count`) is a link with a live number:

```html
<a class="brxe-bfbe-wishlist-button bfbe-wcount bfbe-wcount--corner" href="/wishlist/" data-bfbe-wcount="hide"
   data-bfbe-shop-need="wishlist" data-one="Wishlist, %d item" data-many="Wishlist, %d items" hidden style="display:none">
  <span class="bfbe-wcount__icon" aria-hidden="true"><svg …></span>
  <span class="bfbe-wcount__badge" aria-hidden="true"><span class='bfbe-shop-live' data-bfbe-shop-live='wishlist_count'>0</span></span>
  <span class="bfbe-sr bfbe-wcount__name">Wishlist, 0 items</span>
</a>
```

- `bfbe-wcount--corner` puts the badge over the icon's corner, `--beside` next to it (**Badge place**, `countPlace`). With no Wishlist page set the root is a `span` with no `href`.
- `hidden` and `style="display:none"` come only with **Hide while empty** on and nothing saved; the script removes both after the first add and keeps `.bfbe-wcount__name` in step with the number.
- The Header count keys write `--bfbe-wcount-*` properties on the root; `countBadgeBorder` and `countBadgeTypography` write to `.bfbe-wcount__badge`.

## Wiring to other elements

- **The product in hand.** The button saves the product of the query loop row it sits in, else the page's product, so one element in a product template or a card serves every product. A variation row saves its parent. See `bfbe-shop-loops` for product cards.
- **Other post types.** **Saves** (`postType`) set to a public post type saves the post of that type in the loop row or on the page: a recipe, an article. Its options are the site's own public types.
- **The variation chosen.** On a variable product's page the button reads `variation_id` from WooCommerce's `form.variations_form` for the same product; on a card with no such form it saves the product alone.
- **Everything else follows the list, not an id.** Every Wishlist Button, the header count, `{bfbe_wishlist_count}` and every Wishlist loop on the page update from one answer with no class between them (`bfbe-shop`, "The place-anything model").
- **The wishlist loop** (`bfbeShopWishlist`, skill `bfbe-shop-loops`) lists what the buttons saved, products by default; a second loop with **Post type** (`bfbeShopWishlistType`) set to the same type lists saved posts.
- **The header count links to the Wishlist page**: WordPress menu BFB Elements, Shop, Customers, **Wishlist page**. `{bfbe_wishlist_url}` links there too, for a Bricks Text or Button of your own.
- **Named lists and sharing** are BFB Wishlist Bar and BFB Wishlist Action (`bfbe-wishlist-bar`, `bfbe-wishlist-action`). For a customer the button fills the list in hand, the one **Choose the list shown** last picked.
- **Interactions.** Each change fires **List changed** (`bfbeListChanged`, the event `bfbe/woo/list-changed` on `document.body`, `detail` with `kind`, `product`, `variation`, `added`, `ids`) in Bricks' Interactions, with the **Shop data** switch on (`bfbe-shop-tags-and-conditions`).
- Give the element a class in `_cssClasses` for your own CSS, never `_cssId`: component instances share ids.

## Verified patterns

**A count beside the bag in a header.** From the 2.4 demo shop's header template (`dev/demo/shop/10-templates.php`, "Wishlist count"). `shows: "count"` with the badge beside a 20px heart, hidden until the first add; the colours are the demo's, as hex. Trimmed: the pill's padding, border and hover, and the demo's own heart icon.

```json
{
  "name": "bfbe-wishlist-button",
  "settings": { "shows": "count", "countPlace": "beside", "countIconSize": "20px", "countIconColor": { "hex": "#101828" }, "countBadgeBg": { "hex": "#6e44ff" }, "countBadgeColor": { "hex": "#ffffff" }, "countBadgeSize": "18px", "_cssClasses": "header-wish" }
}
```

**A heart over a product card's picture.** From the demo shop's product card (`dev/demo/shop/lib.php`, "Wishlist heart"), here in Bricks' own products query. Icon only, a round white button pinned to the picture's corner; `onColor` turns the filled heart purple once saved. Its name still says "Add to wishlist: <product>".

```json
{
  "name": "block",
  "settings": { "hasLoop": true, "query": { "objectType": "post", "post_type": [ "product" ], "posts_per_page": 8 }, "_cssClasses": "card", "_position": "relative" },
  "children": [
    { "name": "image", "settings": { "image": { "useDynamicData": "{featured_image}", "size": "woocommerce_single" } } },
    { "name": "bfbe-wishlist-button", "settings": { "content": "icon", "iconSize": "18", "btnPadding": { "top": "9", "right": "9", "bottom": "9", "left": "9" }, "btnBackground": { "hex": "#ffffff" }, "btnBorder": { "width": { "top": "0", "right": "0", "bottom": "0", "left": "0" }, "radius": { "top": "999", "right": "999", "bottom": "999", "left": "999" } }, "onColor": { "hex": "#6e44ff" }, "onBackground": { "hex": "#ffffff" }, "_cssClasses": "card__wish", "_position": "absolute", "_top": "10px", "_right": "10px", "_zIndex": "2" } },
    { "name": "product-title", "settings": { "tag": "h3", "linkToProduct": true } },
    { "name": "product-price", "settings": {} }
  ]
}
```

**A wishlist of articles.** From the P9 fixture (`fixture-shop-p9`, "A wishlist of posts", and `fixture-shop-p9-wishlist`, "Notes kept"). **Saves** `post` with its own words and the icon after them; the Wishlist loop below needs `bfbeShopWishlistType: "post"` to list them, as it shows products otherwise.

```json
{
  "name": "block",
  "settings": {},
  "children": [
    { "name": "block", "settings": { "hasLoop": true, "query": { "objectType": "post", "post_type": [ "post" ] } }, "children": [
      { "name": "heading", "settings": { "text": "{post_title}", "tag": "h4" } },
      { "name": "bfbe-wishlist-button", "settings": { "postType": "post", "textAdd": "Keep this note", "textOn": "Kept", "iconPlace": "row-reverse" } }
    ] },
    { "name": "heading", "settings": { "text": "Notes kept", "tag": "h3" } },
    { "name": "block", "settings": { "hasLoop": true, "query": { "objectType": "bfbeShopWishlist" }, "bfbeShopWishlistType": "post" }, "children": [
      { "name": "heading", "settings": { "text": "{post_title}", "tag": "h4" } }
    ] }
  ]
}
```

## Gotchas

- **No product, no button.** Outside a product page or a product loop row (or a post of the type **Saves** names) the site prints nothing and the canvas says "Place it on a product page or in a product loop." <!-- src: plugins/bfb-elements-pro/elements/wishlist-button.php:217-223 ; plugins/bfb-elements-pro/includes/shop/class-lists.php:690-707 -->
- **The Lists switch must be on.** With WooCommerce or the **Lists** feature off, the element prints nothing on the site and "Needs WooCommerce and the Lists feature on." in the builder. <!-- src: plugins/bfb-elements-pro/elements/wishlist-button.php:206-211 -->
- **The canvas never shows the saved state.** In the builder the toggle is a `type="button"`, never pressed, and the header count always shows at 0, so both can be styled; the page differs. <!-- src: plugins/bfb-elements-pro/elements/wishlist-button.php:227, 247, 278 -->
- **`shows: "count"` hides the button's groups.** Button and Look are offered only for the button; the count has its own Header count group, so `textAdd`, `content` or `btn*` keys on a count are dropped. <!-- src: plugins/bfb-elements-pro/elements/wishlist-button.php:53-55 -->
- **The count needs the Wishlist page.** With none chosen (or not published) it is a plain `span` with no link, and the builder says to choose it under BFB Elements, Shop, Customers. <!-- src: plugins/bfb-elements-pro/elements/wishlist-button.php:267-268, 290, 298-300 -->
- **A hidden count beats your Display.** At 0 with **Hide while empty** on, the root carries `hidden` and an inline `display:none`, so a `_display` set on it cannot show it; `countHide: "off"` keeps 0 on screen. <!-- src: plugins/bfb-elements-pro/elements/wishlist-button.php:285-289 -->
- **The count is the list in hand.** It counts the wishlist only (not compare or quote), and for a customer the list **Choose the list shown** picked, so it changes when they switch lists. <!-- src: plugins/bfb-elements-pro/elements/wishlist-button.php:266 ; plugins/bfb-elements-pro/includes/shop/class-lists.php:190-200 -->
- **A cached page starts unpressed.** The server draws the visitor's state; a cached copy shows nothing pressed and 0 until the shared script's answer, so the states need JavaScript there. A guest page drawn with a saved row sends `DONOTCACHEPAGE`. <!-- src: docs/elements/wishlist-button.md "What the visitor gets" ; plugins/bfb-elements-pro/includes/shop/class-lists.php:208-212 -->
- **Guests and customers keep different lists.** A guest has one list in their WooCommerce session and browser store, joined to their account when they sign in; only customers get named lists, share links and the registry. With WooCommerce's own Wishlists on, a customer's first list is WooCommerce's. <!-- src: docs/elements/shop-lists.md "What is kept where", "WooCommerce's own Wishlists" -->
- **A variable product is pressed for any variation.** The variation goes with the press only where WooCommerce's variation form for that product is on the page; on a card the product is saved with none, and its loop row then offers "Select options" in place of Move to cart. <!-- src: src/elements/shop-lists/shop-lists.js:24-33 ; plugins/bfb-elements-pro/includes/shop/class-lists.php:709-717 ; plugins/bfb-elements-pro/includes/shop/class-wishlist-set.php:175-176 -->
- **A list holds a hundred rows.** The next press is refused with "This list is full at 100. Remove one first." and the button stays unpressed. <!-- src: plugins/bfb-elements-pro/includes/shop/class-lists.php:57, 869 -->

## Never do

- Do not place the button outside a product page, a product loop row or a post of the type **Saves** names.
- Do not set Button or Look keys on a Wishlist Button with `shows: "count"`; use the Header count group.
- Do not style the saved state with a class; use `[aria-pressed="true"]` or the Pressed controls.
- Do not expect the count to link anywhere until the Wishlist page is chosen on the Shop page.
- Do not set `_display` on a header count to keep it on screen at 0; set `countHide: "off"`.
- Do not expect saved posts in a Wishlist loop without `bfbeShopWishlistType` set to their type.
- Do not give it a `_cssId` for styling or wiring; use `_cssClasses`.
