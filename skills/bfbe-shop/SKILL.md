---
name: bfbe-shop
description: "Use for what Shop 2.0 is: the Shop settings page and its sub-pages, the feature switches, which shop skill covers what, building a shop from Bricks' own containers, the requirements, and the shop's theme style groups (BFB Shop, `shop`). Read before writing these settings."
---

# BFB Shop (`shop`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 2.0.0 or later, and BFB Elements Pro 2.0.0 or later for the groups marked Pro, WooCommerce active. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/shop.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/shop/

## What it is
The Shop in BFB Elements: features on Bricks' own WooCommerce elements and new shop elements, the Shop page, cached pages, live tags and what the visitor's browser keeps.

## Where it lives
WooCommerce active, then the WordPress menu BFB Elements, Elements (a switch per shop feature and per shop element) and BFB Elements, Shop (the settings, on sub-pages: General, Products, Pricing, Cart & checkout, Delivery, Customers, Search). A sub-page shows only when a part of the shop adds to it.

## Feature switches
- `shop-sorting` **Shop sorting** (free): Order products by SKU, stock or sales, with sold-out products last.
- `shop-promo-tiles` **Promo tiles** (free): A template of your own at chosen places in a product grid.
- `shop-reviews-loop` **Reviews loop** (free): Product reviews as a query loop, so they can sit anywhere in any layout.
- `shop-brands` **Brands** (free): The brand in the shop breadcrumbs, and brand tags for any element.
- `shop-legal` **EU price and product information** (free): The lowest price of the last 30 days, the unit price, and the maker and safety details.
- `shop-product-page` **Product page essentials** (free): Product data for search engines on every Bricks product template, and a first gallery image that loads at once.
- `shop-mini-cart` **Mini cart** (free): A mini cart that works for keyboard and screen readers, with your own empty state.
- `shop-account` **Account** (free): Your own account pages, a page after login or logout, and confirm fields on registration.
- `shop-filters` **Filters** (free): Collapsible categories in product filters.
- `shop-search-insights` **Search insights** (free): What shoppers search for, and the searches that found nothing.
- `shop-variation` **Variation data** (Pro): Price, SKU, stock and any detail that follow the variation the shopper chooses, in any element.
- `shop-loops` **Shop loops** (Pro): Best sellers, trending, top rated, new arrivals, recently viewed, bought before and more, as query loops.
- `shop-data` **Shop data** (Pro): Shop tags, conditions and interactions in Bricks' own pickers, right on cached pages.
- `shop-cards` **Product cards** (Pro): Swatches and add to cart on product cards, and the variation picker's behaviour.
- `shop-tabs` **Product tabs** (Pro): Extra product tabs with content from a Bricks template, per product, category or tag.
- `shop-gallery-video` **Gallery video** (Pro): Video in Bricks' product gallery, played by the Video Player.
- `shop-stock` **Stock** (Pro): Stock as a bar, and sold counts, following the variation.
- `shop-reviews` **Reviews** (Pro): Review photos, helpful votes and sorting on WooCommerce's reviews.
- `shop-buy` **Buying** (Pro): The BFB Buy Now straight to the checkout, and catalogue mode with ask for a price.
- `shop-forms` **Product options** (Pro): BFB Advanced Forms on the product page: options priced on the server and added with the product.
- `shop-quantity-breaks` **Quantity breaks** (Pro): A price table by quantity, the same on the page and in the cart.
- `shop-delivery` **Delivery** (Pro): Delivery estimates with a postcode check, and delivery dates and slots at checkout.
- `shop-checkout-rules` **Checkout rules** (Pro): A fee or discount by payment method, and hiding other rates when shipping is free.
- `shop-coupons` **Coupons** (Pro): Bricks' coupon field anywhere, coupons from a link, and coupons that apply themselves.
- `shop-cart-lines` **Cart lines** (Pro): Save for later, and undo after removing an item in the mini cart.
- `shop-share-cart` **Share a cart** (Pro): A link that rebuilds the cart on another device or for someone else.
- `shop-checkout-fields` **Checkout fields** (Pro): Your own checkout fields, saved to the order and shown everywhere WooCommerce shows an order.
- `shop-lists` **Lists** (Pro): The wishlist, compare and quote list engine, for guests and customers.
- `shop-live-cart` **Live cart** (Pro): Parts of the page drawn again after every cart change, popups included.
- `shop-orders` **Order loops** (Pro): The customer's orders and an order's items as query loops.
- `shop-swatch-filters` **Swatch filters** (Pro): A swatch look for Bricks' attribute filters.
- `shop-search` **Search** (Pro): Recent and popular searches under Bricks' live search, and synonyms.
- `shop-alerts` **Alerts** (Pro): Back-in-stock and price-drop alerts through BFB Advanced Forms.

## Which skill covers what
The settings the shop adds to Bricks' own elements, one skill per job:
- `bfbe-shop-tags-and-conditions`: Bricks' own dynamic data picker (group BFB Shop), Conditions (group BFB Shop) and Interactions (triggers under BFB Shop).
- `bfbe-shop-loops`: on `block`, `container`, `div`.
- `bfbe-shop-catalogue`: on `block`, `container`, `div`, `filter-checkbox`, `filter-radio`, `woocommerce-breadcrumbs`, `woocommerce-products`, `woocommerce-products-orderby`.
- `bfbe-shop-add-to-cart`: on `product-add-to-cart`, `woocommerce-products`.
- `bfbe-shop-product-gallery`: on `product-gallery`.
- `bfbe-shop-price-and-stock`: on `product-price`, `product-stock`.
- `bfbe-shop-reviews`: on `product-reviews`, `product-tabs`.
- `bfbe-shop-search`: on `filter-search`, `search`.
- `bfbe-shop-mini-cart`: on `woocommerce-mini-cart`.
- `bfbe-shop-cart-page`: on `block`, `container`, `div`, `woocommerce-cart-collaterals`, `woocommerce-cart-coupon`, `woocommerce-cart-items`.
- `bfbe-shop-checkout`: on `woocommerce-checkout-customer-details`, `woocommerce-checkout-order-review`, `woocommerce-checkout-thankyou`, `woocommerce-checkout-v2`, `woocommerce-form-field`.
- `bfbe-shop-account`: on `woocommerce-account-form-register`, `woocommerce-account-page`, `woocommerce-account-register-form`.

The shop's own elements, a skill each (a part inside one of them is in its parent's skill): `bfbe-applied-coupons`, `bfbe-bought-together`, `bfbe-bundle-builder`, `bfbe-buy-now`, `bfbe-cart-goals`, `bfbe-cart-quantity`, `bfbe-cart-shipping`, `bfbe-compare-button`, `bfbe-compare-tray`, `bfbe-delivery-estimate`, `bfbe-empty-cart-button`, `bfbe-linked-products`, `bfbe-offer`, `bfbe-order-status`, `bfbe-payment-icons`, `bfbe-product-3d`, `bfbe-product-badges`, `bfbe-product-layers`, `bfbe-product-questions`, `bfbe-quantity-breaks`, `bfbe-quote-list-button`, `bfbe-rating-summary`, `bfbe-review-form`, `bfbe-review-sort`, `bfbe-review-votes`, `bfbe-save-later-button`, `bfbe-saved-item-button`, `bfbe-size-guide`, `bfbe-spec-scales`, `bfbe-sticky-buy-bar`, `bfbe-tax-switch`, `bfbe-view-switch`, `bfbe-wishlist-action`, `bfbe-wishlist-bar`, `bfbe-wishlist-button`, `bfbe-withdrawal-button`.

## References
- `../bfbe-schemas/references/shop/loops.json`: 14 loops.
- `../bfbe-schemas/references/shop/tags.json`: 120 tags.
- `../bfbe-schemas/references/shop/conditions.json`: 12 conditions.
- `../bfbe-schemas/references/shop/interactions.json`: 4 interactions.

## Settings that decide the build
Theme style groups the shop adds to Bricks' Theme Styles (Bricks, Theme Styles), beside Bricks' own WooCommerce groups. Each prints nothing until a theme style sets it; a hover colour is Bricks' own `:hover` state on the control.

### BFB WooCommerce - Buttons (`bfbe-woo-buttons`)
Styling only, every key in the schema file: `transition`, `mainBackground`, `mainBorder`, `mainTypography`.

### BFB Form fields (`bfbe-fields`)
- `selectArrow` (select) **Arrow on selects**: options: `none` None; writes CSS
- `wooTickLook` (select) **Look**: options: `custom` Styled with the controls below; writes CSS
Styling, in the schema file: `fieldTypography`, `fieldBackground`, `fieldBorder`, `fieldPadding`, `fieldMinHeight`, `focusBorderColor`, `focusBoxShadow`, `focusOutline`, `labelTypography`, `wooBoxBackground`, `wooBoxBorder`, `wooBoxHeight`, `wooListBackground`, `wooListBorder`, `wooListShadow`, `wooListPadding`, `wooOptionTypography`, `wooOptionPadding`, `wooOptionBorder`, `wooOptionHover`, `wooOptionHoverText`, `wooOptionChosen`, `wooSearchBorder`, `wooTickSize`, `wooTickGap`, `wooTickBackground`, `wooTickBorder`, `wooTickRadioBorder`, `wooTickHover`, `wooTickOn`, `wooTickOnLine`, `wooTickMark`.

### BFB WooCommerce - Price, rating, stock (`bfbe-woo-product`)
Styling only, every key in the schema file: `priceTypography`, `oldPriceTypography`, `salePriceTypography`, `starColor`, `emptyStarColor`, `inStockTypography`, `lowStockTypography`, `outOfStockTypography`.
<!-- bfbe:generated:end -->

## Rendered DOM

The shop wraps nothing round a page. Bricks' shop elements keep their own markup (`brxe-product-price`, `brxe-woocommerce-mini-cart`); a feature adds attributes, classes or a part inside them, and each shop element has its own root, named in its skill. What the whole set shares:

```html
<span class='bfbe-shop-live' data-bfbe-shop-live='cart_count' data-bfbe-shop-fb='none'>3</span>
<span class='bfbe-shop-follow' data-bfbe-shop-follow='sku'>SHIRT-01</span>
<div class="bfbe-shop-when" hidden data-bfbe-shop-when="412:a1b2c3:412">… the element …</div>
<div class="bfbe-shop-when" data-bfbe-shop-when="412:d4e5f6:0" data-bfbe-shop-cart="now" style="display:contents">… the element …</div>
```

- **A live tag** (cart, lists, delivery) prints the server's value inside `span.bfbe-shop-live`, keyed by `data-bfbe-shop-live`. `data-bfbe-shop-live-html='1'` marks WooCommerce price markup; `data-bfbe-shop-fb` carries the tag's `@fallback` words.
- **A variation tag** prints the parent's value inside `span.bfbe-shop-follow`; Pro's follower rewrites it as the shopper chooses (`bfbe-shop-tags-and-conditions`).
- **A condition decided in the browser** wraps its element in `div.bfbe-shop-when`, marked `<page id>:<element id>:<post the conditions read>`. Without `data-bfbe-shop-cart` it starts `hidden`; the answer then removes the wrapper (shown) or the whole element.
- **A cart condition** keeps its wrapper: `data-bfbe-shop-cart="now"` was decided on the server, `"later"` waits for the answer, and every cart change sets `display:contents` or `hidden` again.
- After the first answer, `body` carries `bfbe-shop-live--ready`. Every announcement goes to one visually hidden live region, `#bfbe-shop-status` (polite) or `#bfbe-shop-status-alert`, made on first use.
- **The shared script**, `shop-live.min.js`, loads only on a page that printed a live marker or a condition wrapper, or whose shop element asked for it. It sets `window.bfbeShop` (`.act(name, fields)`), `window.bfbeShopStore`, `window.bfbeShopAnnounce(text, assertive)` and `window.bfbeShopLive()`, configured by `window.bfbeShopConfig`.
- **Its events**, on `document`: `bfbe:shop:ask` before each request, `bfbe:shop:live` with the answer, `bfbe:shop:cart` after a cart action of ours. On `document.body`: `bfbe:shop:variation` and the four interaction events.
- **Its requests**: one `GET /?wc-ajax=bfbe_shop_live` per page and per cart change, sent `Cache-Control: no-store`; actions are `POST /?wc-ajax=bfbe_shop_act`. Without the script, every cart and list change is a real `<form method="post">` with a submit button, never a link.

## Wiring to other elements

### What Shop 2.0 is, and what it needs

- The WooCommerce set of BFB Elements: features on Bricks' own shop elements, new elements only where Bricks has none, and shop data (dynamic tags, conditions, interaction triggers, query loop types) in Bricks' own pickers. Nothing replaces a Bricks shop element.
- A feature on a Bricks element is a group titled **BFB** something on that element's Content tab, after Bricks' own groups, with keys that start `bfbeShop`. Its skill is a `bfbe-shop-*` feature skill; its schema lists every host it reaches (`hosts`).
- Needs WooCommerce active, BFB Elements 2.0.0 (Bricks 2.3 or later, WordPress 6.5, PHP 8.1) and, for the Pro parts, BFB Elements Pro 2.0.0, which needs the free plugin at 2.0.0. Measured on Bricks 2.3.10 and 2.4.2, WooCommerce 11.1.2 and 11.2.1.
- Bricks 2.4's experimental shop elements (its "advanced modular elements" setting) get the features too, where that setting is on. With it off, they are not registered and nothing is attached to them.
- Shop elements are in the `bfb-elements` category like every BFB element. Each shop feature is a switch on BFB Elements, Elements, on unless turned off.

### The place-anything model

- **Every part is its own element**, laid out with Bricks' Block, Container and Div: BFB Buy Now beside Bricks' Add to cart, BFB Quantity Breaks under Product price, BFB Review Form beside Product reviews. No shop element has a position or arrangement control.
- **The product in hand.** A shop element or tag reads the product of the query loop row it sits in, else the page's product. A part therefore works on a single product template and in any product loop row with nothing to point at.
- **Lists are query loops** on a Container, Block or Div, with Bricks' own elements in each row (`bfbe-shop-loops`): product sets, reviews, images, variations, the wishlist, compare and quote lists, saved for later, orders. A product card is Bricks' Product title, Product price, Add to cart and an Image of `{featured_image}`, plus BFB parts such as Product Badges and Wishlist Button.
- **Nestable parents hold their parts**, with Bricks' elements beside them: BFB Offer (Offer Checkbox), BFB Bought Together (Bought Together Products, Bought Together Total), BFB Bundle Builder (Bundle Title, Bundle Progress, Bundle Products), BFB Compare Tray, BFB Wishlist Bar (Wishlist Action), BFB Sticky Buy Bar.
- **Two halves of one job are two instances**, each with **Shows** (`shows`): Wishlist Button `button` or `count`; Rating Summary `both`, `summary` or `bars`; Product Questions `both`, `list` or `form`; Size Guide `button` or `page`; Cart Goals `all`, `sentence`, `track` or `gifts`; Cart Quantity `both`, `qty` or `remove`; Order Status `both`, `form` or `answer`.
- **Bricks' own part steps aside the same way**: Product reviews with `bfbeShopReviewsFormShow: "hide"`, and BFB Review Form placed wherever the form belongs.
- **Parts meet through the shop's state, not through ids**: the cart, the visitor's lists, the order in hand and the live answer. Two Wishlist Buttons, a header count and a wishlist loop agree with no class or id between them.
- Where a control asks for an **Element id** (the set **Pinned on an image**, `bfbeShopHotspots`; **BFB Product moments**, `bfbeShopMomentsPlayer`), leave it empty to take the nearest BFB Image Hotspots or BFB Video Player.

### The Shop settings screens

WordPress menu **BFB Elements, Shop**: what applies to the whole shop, on sub-pages picked from pills and kept in the address as `&tab=`. A sub-page shows only when a part adds a card to it; the free plugin alone has General, Pricing, Customers and Search. Each Save stores its own sub-page only. Each element's own options stay on the element.

| Sub-page (`tab`) | Cards |
|---|---|
| General (`general`) | Page caching, Sorting, Search engines; Pro: Recently viewed, and a card to move lists another add-on kept, shown only when it finds some |
| Products (`products`) | Pro: Product badges, Size guides, Product tabs, Reviews, Age check |
| Pricing (`pricing`) | Price information for the EU; Pro: Prices with or without tax, Quantity discounts by category, Catalogue mode |
| Cart & checkout (`checkout`) | Pro: Cart goals, Coupons, Payment method fees, Free shipping, Checkout fields |
| Delivery (`delivery`) | Pro: Processing time, Working days and cut-off times, Transit times, Holidays, Delivery dates and time slots |
| Customers (`customers`) | Your account pages, WooCommerce's account pages, Where customers land; Pro: Wishlist and compare pages, Stock and price alerts |
| Search (`search`) | What shoppers search for; Pro: Search suggestions, Synonyms |

### Which skill for which job

| Job | Skill |
|---|---|
| Shop tags, conditions, interaction triggers | `bfbe-shop-tags-and-conditions` |
| Query loops: product sets, reviews, images, variations, lists, orders | `bfbe-shop-loops` |
| Shop archive: promo tiles, sorting, filters, swatch filters, brand breadcrumbs | `bfbe-shop-catalogue` |
| Add to cart and Products: option lists, swatches, ask for a price, cards | `bfbe-shop-add-to-cart` |
| Product gallery: first image, thumbnails, video and 3D slides | `bfbe-shop-product-gallery` |
| Product price and stock: lowest price, unit price, stock bar, sold count | `bfbe-shop-price-and-stock` |
| Product reviews and tabs: photos, votes, sort, tabs from templates | `bfbe-shop-reviews` |
| Search and Filter - Search: recent and popular searches, suggestions | `bfbe-shop-search` |
| Mini cart: accessible panel, empty state, undo, save for later | `bfbe-shop-mini-cart` |
| Cart page: cart table, coupons anywhere, live cart regions | `bfbe-shop-cart-page` |
| Checkout and thank-you: fields look, own checkout fields, delivery slots | `bfbe-shop-checkout` |
| Account page and registration | `bfbe-shop-account` |
| Badges from rules | `bfbe-product-badges` |
| Grid or list, columns, per page | `bfbe-view-switch` |
| Size table and size finder | `bfbe-size-guide` |
| Average and bars per star | `bfbe-rating-summary` |
| Questions and answers | `bfbe-product-questions` |
| Attributes as scales | `bfbe-spec-scales` |
| With or without VAT, site-wide | `bfbe-tax-switch` |
| A bar that follows the scroll with the buy button | `bfbe-sticky-buy-bar` |
| Products bought together, one button | `bfbe-bought-together` |
| Choose any N for a price | `bfbe-bundle-builder` |
| 360 degree spin, AR and 3D model | `bfbe-product-3d` |
| A product picture in layers, one per chosen option | `bfbe-product-layers` |
| Straight to the checkout | `bfbe-buy-now` |
| Price table by quantity | `bfbe-quantity-breaks` |
| One product per colour, as swatches | `bfbe-linked-products` |
| Review form, sort and helpful votes as parts | `bfbe-review-form`, `bfbe-review-sort`, `bfbe-review-votes` |
| Delivery estimate with a postcode check | `bfbe-delivery-estimate` |
| Goals on one track: free shipping, gifts, discounts | `bfbe-cart-goals` |
| An add-on offer with a checkbox | `bfbe-offer` |
| Empty the cart | `bfbe-empty-cart-button` |
| Coupons on the cart, each with Remove | `bfbe-applied-coupons` |
| A cart page laid out yourself: quantity, shipping choice | `bfbe-cart-quantity`, `bfbe-cart-shipping` |
| Save for later on a v2 cart line, and its saved rows | `bfbe-save-later-button`, `bfbe-saved-item-button` |
| Order lookup with a timeline | `bfbe-order-status` |
| Payment method icons | `bfbe-payment-icons` |
| WooCommerce's online withdrawal page | `bfbe-withdrawal-button` |
| Wishlist: the button, the lists bar and its actions | `bfbe-wishlist-button`, `bfbe-wishlist-bar`, `bfbe-wishlist-action` |
| Compare: the button and the tray | `bfbe-compare-button`, `bfbe-compare-tray` |
| Quote list | `bfbe-quote-list-button` |
| A switch that pauses the page's motion | `bfbe-motion-switch` |
| Product options priced on the server, stock and price alerts, the product finder, a quote's draft order, cart extras | `bfbe-form` |
| A quick order table of products, a shoppable list | `bfbe-dynamic-table` |
| The products being compared as a table | `bfbe-comparison-table` |
| A coupon to copy and apply | `bfbe-copy` |
| Product pins on an image, a pin per linked post | `bfbe-hotspots` |
| The gallery's video, products at moments of a video | `bfbe-video-player` |
| Added to the cart, a viewed product back or on sale | `bfbe-toast` |
| WooCommerce's store notice as a bar | `bfbe-notification-bar` |
| An order's delivery date or a product's release date | `bfbe-add-to-calendar` |
| An age check on products for adults | `bfbe-age-gate` |

## Verified patterns

**A buy box laid out with Bricks' blocks.** From the demo shop's product template (`bfb-demo-product`, "Buy box"). Bricks' product elements carry their BFB groups (the lowest price and unit price on Product price, the stock bar on Product stock); BFB parts sit between them, each where the layout wants it. Trimmed: the demo's look, the brand and rating rows, Linked Products, Spec Scales and the two alert forms.

```json
{
  "name": "block",
  "settings": { "_cssClasses": "buy-box" },
  "children": [
    { "name": "product-title", "settings": { "tag": "h1" } },
    { "name": "bfbe-product-badges", "settings": { "max": 3, "layout": "inline" } },
    { "name": "product-price", "settings": { "bfbeShopLowest": true, "bfbeShopUnit": true } },
    { "name": "bfbe-quantity-breaks", "settings": {} },
    { "name": "product-stock", "settings": { "bfbeShopStockBar": true, "bfbeShopStockBarText": "Only {left} left" } },
    { "name": "block", "settings": { "_cssClasses": "buy-row" }, "children": [
      { "name": "product-add-to-cart", "settings": { "buttonText": "Add to cart" } },
      { "name": "bfbe-buy-now", "settings": { "text": "Buy now", "takes": "alone" } }
    ] },
    { "name": "block", "settings": {}, "children": [
      { "name": "bfbe-wishlist-button", "settings": { "content": "both", "textAdd": "Save", "textOn": "Saved" } },
      { "name": "bfbe-compare-button", "settings": { "content": "both" } },
      { "name": "bfbe-size-guide", "settings": { "text": "Size guide" } }
    ] },
    { "name": "bfbe-delivery-estimate", "settings": { "show": "both" } }
  ]
}
```

**A review area with Bricks' form set aside.** From the same template ("Reviews"). Product reviews hides its own form (`bfbeShopReviewsFormShow: "hide"`) and BFB Review Form stands under the list; Rating Summary and Review Sort sit in their own column above. Trimmed: the form's and the list's look.

```json
{
  "name": "block",
  "settings": {},
  "children": [
    { "name": "block", "settings": {}, "children": [
      { "name": "heading", "settings": { "text": "What people say", "tag": "h2" } },
      { "name": "bfbe-rating-summary", "settings": { "stars": true, "text": "{average} out of 5, from {count} reviews", "figure": "count" } },
      { "name": "bfbe-review-sort", "settings": { "as": "select", "label": "Sort reviews" } }
    ] },
    { "name": "block", "settings": {}, "children": [
      { "name": "product-reviews", "settings": { "bfbeShopReviewsFormShow": "hide", "bfbeShopReviewsListTitle": "hide" } },
      { "name": "bfbe-review-form", "settings": {} }
    ] }
  ]
}
```

**Header icons that stay right on a cached page.** From the demo shop's header template (`bfb-demo-header`, "Icons"). The compare count is a live tag in a Bricks Text; the wishlist count is a second Wishlist Button with `shows: "count"`; Bricks' Mini cart carries its BFB group (`bfbeShopMiniCartTitle` names the panel). Trimmed: the icons, links and look.

```json
{
  "name": "block",
  "settings": { "_cssClasses": "header-icons" },
  "children": [
    { "name": "block", "settings": { "tag": "a", "link": { "type": "external", "url": "/compare/" } }, "children": [
      { "name": "text-basic", "settings": { "text": "Compare", "tag": "span" } },
      { "name": "text-basic", "settings": { "text": "{bfbe_compare_count}", "tag": "span" } }
    ] },
    { "name": "bfbe-wishlist-button", "settings": { "shows": "count", "countPlace": "beside" } },
    { "name": "woocommerce-mini-cart", "settings": { "bfbeShopMiniCartTitle": "My cart" } }
  ]
}
```

## Gotchas

- **No WooCommerce, no shop.** Without WooCommerce active the set adds nothing: no controls, no tags, no loop types, no admin page, no files. Settings saved earlier stay and act again once it is back. <!-- src: plugins/bfb-elements/includes/shop/class-shop.php:57-61 --> <!-- src: docs/elements/shop.md "Only with WooCommerce" -->
- **Pro's shop needs the free plugin at 2.0.0.** With an older free plugin, Pro stops its own boot and shows a notice; nothing of Pro's shop registers. <!-- src: plugins/bfb-elements-pro/bfb-elements-pro.php:27 --> <!-- src: plugins/bfb-elements-pro/includes/class-requirements.php:28 --> <!-- src: docs/SHOP-ARCHITECTURE-2026-10-21.md §3.1 -->
- **A switched-off feature registers nothing.** Its controls, tags, conditions or loop types are missing from Bricks' panels and pickers, so a key written for it is never read. Check the switch on BFB Elements, Elements before concluding a control is absent. <!-- src: plugins/bfb-elements/includes/shop/class-shop.php:49-52 --> <!-- src: plugins/bfb-elements/includes/class-element-switches.php:224-226 -->
- **A Shop sub-page appears only with a card on it.** The free plugin alone offers General, Pricing, Customers and Search; Products, Cart & checkout and Delivery come with Pro's parts. <!-- src: plugins/bfb-elements/includes/shop/class-admin.php:72-75 --> <!-- src: docs/SHOP-ARCHITECTURE-2026-10-21.md §3.12 -->
- **Live tags are live in text only.** In a link, an image or an attribute such as `href`, `src` or `style`, a live tag prints the server's value once and is never corrected after load, so a cached page keeps the first visitor's figure there. <!-- src: plugins/bfb-elements/includes/shop/class-tags.php:232-233 --> <!-- src: src/elements/shop-live/shop-live.js:163 -->
- **Visitor conditions decide on the server by default.** On a site behind a page cache, switch on **Check visitor conditions after the page loads** (Shop, General): elements with a personal condition then start hidden and appear after the answer, so they are absent without JavaScript. <!-- src: plugins/bfb-elements/includes/shop/class-admin.php:142-151 --> <!-- src: plugins/bfb-elements/includes/shop/class-conditions.php:10-24 -->
- **A cart condition puts a wrapper round its element.** `div.bfbe-shop-when` with `display:contents` keeps the flex or grid layout, but a child combinator (`.row > .note`) or `:nth-child()` on that element no longer matches. <!-- src: plugins/bfb-elements/includes/shop/class-conditions.php:353-355 -->
- **Hidden by a cart condition is not secret.** The element is in the page, hidden, so it can appear after a cart change. Only the customer conditions (bought, order count, total spent) leave a false element out of the page. <!-- src: plugins/bfb-elements/includes/shop/class-conditions.php:16, 26-33 -->
- **The theme style groups print nothing until set.** **BFB Form fields** leaves fields inside BFB Advanced Forms alone, and its tick box controls act only with **Look** (`wooTickLook`) set to `custom`. <!-- src: plugins/bfb-elements/includes/shop/class-theme-styles.php:17-18, 50, 241 -->
- **The 2.3 builder can lag one save.** On Bricks 2.3.10 the canvas's single-element re-render skips the seam a feature uses to change a shop element's finished markup, so such a change can show only after the next save; the page is right. <!-- src: plugins/bfb-elements/includes/shop/class-woo-elements.php:13-17 --> <!-- src: docs/SHOP-ARCHITECTURE-2026-10-21.md §3.2 -->
- **A part outside its parent shows a note in the builder.** Offer Checkbox, Bought Together Products and Total, and the three Bundle parts say "Place this inside" their parent in the canvas; BFB Saved Item Button prints nothing outside a Saved for later loop. <!-- src: plugins/bfb-elements-pro/elements/bundle-title.php:95 --> <!-- src: docs/elements/saved-item-button.md "Saved item" -->
- **Passive browser storage waits for consent.** Recently viewed products are kept only with consent where BFB Cookie Consent is on the site (its Preferences category); lists a visitor builds are kept regardless, as they asked for them. <!-- src: docs/elements/shop.md "What the visitor's browser keeps" --> <!-- src: docs/elements/shop-lists.md "What is kept where" -->

## Never do

- Do not build a stand-in for a Bricks shop element from other elements; use Bricks' element and its BFB group.
- Do not put a live tag in a link, image or attribute where it must follow the visitor on a cached page.
- Do not style an element that carries a cart condition through `>` or `:nth-child()`; give it a class.
- Do not hide content meant for buyers only behind a cart condition; use a customer condition.
- Do not set a tick box control in **BFB Form fields** without `wooTickLook: "custom"`.
- Do not place Offer Checkbox, Bought Together or Bundle parts outside their parent, or a Saved Item Button outside a Saved for later loop.
- Do not point a shop part at another by `_cssId`; leave Element id fields empty to take the nearest.
