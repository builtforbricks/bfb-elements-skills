---
name: bfbe-shop-tags-and-conditions
description: "Use for the {bfbe_*} dynamic tags of the group BFB Shop (product, cart, order, customer, variation facts, live after load on cached pages), the shop conditions and the shop interaction triggers (BFB Shop tags and conditions, `shop-tags-and-conditions`). Read before writing these settings."
---

# BFB Shop tags and conditions (`shop-tags-and-conditions`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 2.0.0 or later, and BFB Elements Pro 2.0.0 or later for the groups marked Pro, WooCommerce active, the feature switches on (WordPress menu BFB Elements, Elements): `shop-data`, `shop-variation`. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/shop-tags-and-conditions.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/shop/ (the Shop), and a page for each feature this skill spans: https://builtforbricks.com/bfb-elements/docs/shop-data/, https://builtforbricks.com/bfb-elements/docs/shop-variation/

## What it is
The website documents this by feature; each line is the approved summary from that feature's page.
- `shop-data` (https://builtforbricks.com/bfb-elements/docs/shop-data/): The shop facts Bricks has no tag or condition for, in Bricks' own pickers: dynamic data tags under BFB Shop for products, coupons and orders, conditions under BFB Shop for the cart, the customer, the product and the order, and four shop triggers in the Interactions panel. These are Pro. The live cart tags (number of items, subtotal, total, tax, shipping, coupon discount, what is left to free shipping) are free: they come with the free plugin wherever WooCommerce is active, with no switch, and stay right on cached pages.
- `shop-variation` (https://builtforbricks.com/bfb-elements/docs/shop-variation/): Dynamic data tags under BFB Shop that print the parent product's value and change as the shopper chooses a variation: SKU, price, stock status, stock quantity, weight, dimensions, GTIN, description and the meta values you allow. Put them in any element on the product page; the follower watches WooCommerce's own variations form, and a reset puts the product's own values back.

## Where it lives
Not an element and no control: Bricks' own dynamic data picker (group BFB Shop), Conditions (group BFB Shop) and Interactions (triggers under BFB Shop). Tags and triggers come with the switch `shop-data` (Pro) and the free parts that register their own; variation facts with `shop-variation`.

## Dynamic tags (120)
Each tag's label, argument, contexts and live key are in `../bfbe-schemas/references/shop/tags.json`. By area:
- Product (24): `{bfbe_product_lowest_price}` (free), `{bfbe_product_unit_price}` (free), `{bfbe_product_net_quantity}` (free), `{bfbe_product_net_unit}` (free), `{bfbe_product_maker}` (free), `{bfbe_product_eu_contact}` (free), `{bfbe_product_warnings}` (free), `{bfbe_product_instructions_url}` (free), `{bfbe_product_discount}`, `{bfbe_product_discount_percent}`, `{bfbe_product_sale_start:iso}`, `{bfbe_product_sale_end:iso}`, `{bfbe_product_stock_left}`, `{bfbe_product_stock_percent}`, `{bfbe_product_sold:30}`, `{bfbe_product_price_range}`, `{bfbe_product_rating_count:5}`, `{bfbe_product_in_cart}`, `{bfbe_product_video}`, `{bfbe_product_image:size}`, `{bfbe_product_brand:link}` (free), `{bfbe_product_brand_logo:size}` (free), `{bfbe_product_brand_description}` (free), `{bfbe_product_brand_url}` (free).
- Shop (3): `{bfbe_shop_guarantee}` (free), `{bfbe_shop_free_shipping_minimum}` (free), `{bfbe_shop_store_notice}` (free).
- Review (9): `{bfbe_review_rating}` (free), `{bfbe_review_stars:svg}` (free), `{bfbe_review_author}` (free), `{bfbe_review_date:format}` (free), `{bfbe_review_text}` (free), `{bfbe_review_verified}` (free), `{bfbe_review_product}` (free), `{bfbe_review_product_url}` (free), `{bfbe_review_photos:size}`.
- Cart (11): `{bfbe_cart_count}` (free), `{bfbe_cart_subtotal}` (free), `{bfbe_cart_total}` (free), `{bfbe_cart_free_shipping_left}` (free), `{bfbe_cart_tax}` (free), `{bfbe_cart_shipping}` (free), `{bfbe_cart_discount}` (free), `{bfbe_cart_line_options}`, `{bfbe_cart_line_price}`, `{bfbe_cart_coupons}`, `{bfbe_cart_share_url}`.
- Order (31): `{bfbe_order_field:key}`, `{bfbe_order_delivery_date:format}`, `{bfbe_order_delivery_range}`, `{bfbe_order_item_name}`, `{bfbe_order_item_quantity}`, `{bfbe_order_item_price}`, `{bfbe_order_item_total}`, `{bfbe_order_item_sku}`, `{bfbe_order_item_options}`, `{bfbe_order_item_image:size}`, `{bfbe_order_item_url}`, `{bfbe_order_number}`, `{bfbe_order_total}`, `{bfbe_order_subtotal}`, `{bfbe_order_tax}`, `{bfbe_order_shipping_total}`, `{bfbe_order_discount}`, `{bfbe_order_date:format}`, `{bfbe_order_status}`, `{bfbe_order_email}`, `{bfbe_order_payment_method}`, `{bfbe_order_shipping_method}`, `{bfbe_order_items_count}`, `{bfbe_order_customer_name}`, `{bfbe_order_billing_address}`, `{bfbe_order_shipping_address}`, `{bfbe_order_view_url}`, `{bfbe_order_withdrawal_url}`, `{bfbe_order_total_label}`, `{bfbe_order_total_value}`, `{bfbe_order_total_key}`.
- Coupon (3): `{bfbe_coupon_expiry:CODE}`, `{bfbe_coupon_amount:CODE}`, `{bfbe_coupon_description:CODE}`.
- Delivery (3): `{bfbe_delivery_date}`, `{bfbe_delivery_range}`, `{bfbe_delivery_cutoff}`.
- Find (1): `{bfbe_find_again_url}`.
- Wishlist (5): `{bfbe_wishlist_count}`, `{bfbe_wishlist_url}`, `{bfbe_wishlist_name}`, `{bfbe_wishlist_saved}`, `{bfbe_wishlist_registry}`.
- Compare (2): `{bfbe_compare_count}`, `{bfbe_compare_url}`.
- Quote (1): `{bfbe_quote_count}`.
- Offer (6): `{bfbe_offer_name}`, `{bfbe_offer_price}`, `{bfbe_offer_regular}`, `{bfbe_offer_percent}`, `{bfbe_offer_link}`, `{bfbe_offer_image}`.
- Customer (1): `{bfbe_customer_order_count}`.
- Moment (4): `{bfbe_moment_time}`, `{bfbe_moment_seconds}`, `{bfbe_moment_words}`, `{bfbe_moment_chapter}`.
- Saved (1): `{bfbe_saved_count}`.
- Added (2): `{bfbe_added_product_name}`, `{bfbe_added_product_image}`.
- Recent (4): `{bfbe_recent_product_name}`, `{bfbe_recent_product_image}`, `{bfbe_recent_product_url}`, `{bfbe_recent_product_note}`.
- Variation (9): `{bfbe_variation_sku}`, `{bfbe_variation_price}`, `{bfbe_variation_stock_status}`, `{bfbe_variation_stock_qty}`, `{bfbe_variation_weight}`, `{bfbe_variation_dimensions}`, `{bfbe_variation_gtin}`, `{bfbe_variation_description}`, `{bfbe_variation_meta:key}`.

## Conditions (12)
Group BFB Shop in Bricks' Conditions; compare options and value controls in `../bfbe-schemas/references/shop/conditions.json`.
- `bfbe_shop_cart_total` **Cart total**: compare `==` is, `!=` is not, `>=` is at least, `<=` is at most, `>` is more than, `<` is less than; personal, follows the cart; Pro.
- `bfbe_shop_cart_items` **Cart items**: compare `==` is, `!=` is not, `>=` is at least, `<=` is at most, `>` is more than, `<` is less than; personal, follows the cart; Pro.
- `bfbe_shop_product_in_cart` **Cart**: compare `contains` contains the product, `contains_not` does not contain the product; personal, follows the cart; Pro.
- `bfbe_shop_category_in_cart` **Cart categories**: compare `contains` contains, `contains_not` does not contain; personal, follows the cart; Pro.
- `bfbe_shop_coupon_applied` **Coupons applied**: compare `contains` contains, `contains_not` does not contain; personal, follows the cart; Pro.
- `bfbe_shop_bought` **Customer bought**: compare `contains` contains the product, `contains_not` does not contain the product; personal; Pro.
- `bfbe_shop_order_count` **Customer order count**: compare `==` is, `!=` is not, `>=` is at least, `<=` is at most, `>` is more than, `<` is less than; personal; Pro.
- `bfbe_shop_total_spent` **Customer total spent**: compare `==` is, `!=` is not, `>=` is at least, `<=` is at most, `>` is more than, `<` is less than; personal; Pro.
- `bfbe_shop_shipping_country` **Shipping country**: compare `==` is, `!=` is not, `contains` contains, `contains_not` does not contain; personal, follows the cart; Pro.
- `bfbe_shop_stock_left` **Product stock left**: compare `==` is, `!=` is not, `>=` is at least, `<=` is at most, `>` is more than, `<` is less than; Pro.
- `bfbe_shop_sale_ends_within` **Product sale ends within (days)**: compare `==` is, `!=` is not, `>=` is at least, `<=` is at most, `>` is more than, `<` is less than; Pro.
- `bfbe_shop_order_found` **Order found**: compare `==` is, `!=` is not; Pro.

## Interaction triggers
In Bricks' Interactions, the Trigger select, under BFB Shop (Pro, switch `shop-data`):
- `bfbeVariationChosen` **Variation chosen**: the event `bfbe/woo/variation-chosen` on `document.body`.
- `bfbeListChanged` **List changed**: the event `bfbe/woo/list-changed` on `document.body`.
- `bfbeGoalReached` **Cart goal reached**: the event `bfbe/woo/goal-reached` on `document.body`.
- `bfbeProductAdded` **Product added**: the event `bfbe/woo/product-added` on `document.body`.
<!-- bfbe:generated:end -->

## Rendered DOM

Tags, conditions and triggers are Bricks' own mechanisms, so they add no element. What they leave in the page:

```html
<p class="brxe-text-basic">Ships free from <span class='bfbe-shop-live' data-bfbe-shop-live='cart_free_shipping_left' data-bfbe-shop-live-html='1'>…price…</span></p>
<p class="brxe-text-basic">SKU <span class='bfbe-shop-follow' data-bfbe-shop-follow='sku'>SHIRT-01</span></p>
<div class="bfbe-shop-when" data-bfbe-shop-when="412:d4e5f6:0" data-bfbe-shop-cart="now" style="display:contents"><div class="brxe-block">…</div></div>
```

- **A plain tag** prints its value as escaped words, or as WooCommerce's own price markup and the stars' inline SVG. A literal brace in a value is printed `&#123;`, so Bricks' own pass leaves it alone.
- **A live tag** (its `live` key in `tags.json`) prints the server's value inside `span.bfbe-shop-live`; the shared script rewrites it after load and after every cart change. `data-bfbe-shop-fb` carries the `@fallback` words.
- **A variation tag** (its `follows` fact) prints the parent's value inside `span.bfbe-shop-follow`, rewritten when the shopper chooses: `sku`, `price_html`, `stock_status`, `stock_qty`, `weight`, `dimensions`, `gtin`, `description`, `lowest_price`, `unit_price`, `meta:<key>`.
- **In a link control** a tag gives plain words. **In an image control** it gives an attachment id or a URL; `{bfbe_review_photos}` gives several ids, which Bricks' Image Gallery reads.
- **A condition** decided on the server leaves nothing: the element is printed or not. Decided in the browser, it leaves the `div.bfbe-shop-when` wrapper (`bfbe-shop`, Rendered DOM).
- **A trigger** is written by Bricks into the element's `data-interactions`, as Bricks' own are. `shop-data.min.js` (0.48 KB gzipped) loads only on a page whose element uses one of the four.

## Wiring to other elements

### Tag syntax and the thing in hand

`{bfbe_<name>:<arg>:<arg> @fallback:'words' @static}`. Arguments follow colons (`{bfbe_product_sold:30}`, `{bfbe_coupon_expiry:SUMMER5:Y-m-d}`). `@fallback:'words'` prints while there is no value; `@static` prints a live or variation tag once, with no marker.

A product tag reads the **product in hand**: the row's product in a query loop, else the page's product. An order tag reads the **order in hand**: a Customer orders or Order items row, the thank-you or order-pay page with the order's key, the account's view-order page, or the order a BFB Order Status found on this request.

### Tags by job

Every tag's label, argument, contexts, live key and source is in `../bfbe-schemas/references/shop/tags.json`.

| Job | Tags | Where it answers | Switch |
|---|---|---|---|
| Cart figures, live | `{bfbe_cart_count}`, `_subtotal`, `_total`, `_tax`, `_shipping`, `_discount`, `_free_shipping_left`; Pro `{bfbe_cart_coupons}`, `{bfbe_cart_share_url}` | any page | core; `shop-coupons`, `shop-share-cart` |
| Shop-wide words | `{bfbe_shop_free_shipping_minimum}`, `{bfbe_shop_store_notice}`, `{bfbe_shop_guarantee}` | any page | core; `shop-legal` |
| A cart row | `{bfbe_cart_line_options}`, `{bfbe_cart_line_price}` | a row of Bricks' Cart contents loop | Pro |
| EU price and product facts | `{bfbe_product_lowest_price}`, `_unit_price`, `_net_quantity`, `_net_unit`, `_maker`, `_eu_contact`, `_warnings`, `_instructions_url` | product in hand | `shop-legal` |
| Brand | `{bfbe_product_brand}` (`:link`), `_brand_logo:size`, `_brand_description`, `_brand_url` | product in hand | `shop-brands` |
| Sale, stock, sales | `{bfbe_product_discount}`, `_discount_percent`, `_sale_start`, `_sale_end` (`:iso`, `:unix` or a date format), `_stock_left`, `_stock_percent`, `_sold:days`, `_price_range`, `_rating_count:stars`, `_in_cart` (live) | product in hand | `shop-data` |
| Following the variation | `{bfbe_variation_sku}`, `_price`, `_stock_status`, `_stock_qty`, `_weight`, `_dimensions`, `_gtin`, `_description`, `_meta:key` | product in hand, beside its add to cart form | `shop-variation` |
| Media | `{bfbe_product_video}` (`:poster`, `:captions`); `{bfbe_product_image:size}` (the row's in an images loop, else the featured image) | product in hand | `shop-gallery-video`; `shop-loops` |
| A review | `{bfbe_review_rating}`, `_stars:svg`, `_author`, `_date:format`, `_text`, `_verified`, `_product`, `_product_url`; Pro `_photos:size` | a reviews loop row | `shop-reviews-loop`; `shop-reviews` |
| An order | `{bfbe_order_number}`, `_total`, `_subtotal`, `_tax`, `_shipping_total`, `_discount`, `_date:format`, `_status`, `_email`, `_payment_method`, `_shipping_method`, `_items_count`, `_customer_name`, `_billing_address`, `_shipping_address`, `_view_url`, `_withdrawal_url`; `_field:key`; `_delivery_date:format`, `_delivery_range` | order in hand | `shop-data`; `shop-checkout-fields`; `shop-delivery` |
| Order lines and totals | `{bfbe_order_item_*}` (name, quantity, price, total, sku, options, image, url); `{bfbe_order_total_label}`, `_value`, `_key`; `{bfbe_customer_order_count}` (live) | an Order items row; an Order totals row; any page | `shop-orders` |
| A coupon | `{bfbe_coupon_expiry:CODE}`, `{bfbe_coupon_amount:CODE}`, `{bfbe_coupon_description:CODE}` | an element's own settings | `shop-data` |
| Delivery, live | `{bfbe_delivery_date}`, `{bfbe_delivery_range}`, `{bfbe_delivery_cutoff}` | any page | `shop-delivery` |
| Lists | `{bfbe_wishlist_count}`, `{bfbe_compare_count}`, `{bfbe_quote_count}`, `{bfbe_saved_count}` (live); `{bfbe_wishlist_url}`, `{bfbe_compare_url}`; `{bfbe_wishlist_name}`, `_saved`, `_registry` (the list shown) | any page | `shop-lists`; `shop-cart-lines` |
| Inside one element | `{bfbe_offer_*}` (in BFB Offer); `{bfbe_added_product_*}`, `{bfbe_recent_product_*}` (in BFB Toast); `{bfbe_moment_*}` (a Product moments row); `{bfbe_find_again_url}` (a finder's no-results content) | that element | Pro |

### Conditions

Group **BFB Shop** in Bricks' Conditions, stored in Bricks' `_conditions`: a list of sets, any of which may hold, each a list of rows that must all hold, `{"key": "bfbe_shop_cart_total", "compare": ">=", "value": "50"}`. Every value but Order found's is text and accepts dynamic data. All twelve are Pro, switch `shop-data`; compare options are in `../bfbe-schemas/references/shop/conditions.json`.

- **Cart** (follow the cart with no reload): `bfbe_shop_cart_total`, `bfbe_shop_cart_items`, `bfbe_shop_product_in_cart` (an id or SKU), `bfbe_shop_category_in_cart` (a slug; a child's parents count), `bfbe_shop_coupon_applied` (a code), `bfbe_shop_shipping_country` (a country code, `RO`).
- **Customer** (decided once for the page): `bfbe_shop_bought` (an id or SKU), `bfbe_shop_order_count`, `bfbe_shop_total_spent`.
- **Product** (always on the server): `bfbe_shop_stock_left`, `bfbe_shop_sale_ends_within` (days).
- **Order**: `bfbe_shop_order_found` (`yes` or `no`): an order tag has an order in hand here.
- Whenever a set holds a cart condition, the whole set is decided again on each cart change, Bricks' own rows included. So a Bricks **Dynamic data** row (`"key": "dynamic_data"`) beside a cart row follows the cart too.

### Interaction triggers

In Bricks' Interactions, **Trigger**, under BFB Shop: `bfbeVariationChosen`, `bfbeListChanged`, `bfbeGoalReached`, `bfbeProductAdded`. Write them in Bricks' `_interactions` rows with Bricks' own actions; **Run once** works as on any trigger. Each listens for a CustomEvent on `document.body`, also usable from a site's own script:

- `bfbe/woo/variation-chosen`: `{ form, productId, variationId, variation }`.
- `bfbe/woo/list-changed`: `{ kind, list, product, productId, variation, added, action, ids }`.
- `bfbe/woo/goal-reached`: `{ goal, label, reward }`, from BFB Cart Goals.
- `bfbe/woo/product-added`: `{ productId, variationId, quantity }`.

## Verified patterns

**Cart sums that follow the cart.** From the demo shop's own cart page (`your-cart`, "Summary"). Each figure is a live tag; the Discount row shows only while the cart has a discount. Its cart row makes the set follow every cart change, and its Dynamic data row reads the tag with `@static`, so it compares the figure, not the live marker. Trimmed: the Delivery and VAT rows (built like Discount) and the free delivery notes.

```json
{
  "name": "block",
  "settings": { "_cssClasses": "cart-sums" },
  "children": [
    { "name": "block", "settings": { "_cssClasses": "sum" }, "children": [
      { "name": "text-basic", "settings": { "text": "Subtotal" } },
      { "name": "text-basic", "settings": { "text": "{bfbe_cart_subtotal}" } }
    ] },
    { "name": "block", "settings": { "_cssClasses": "sum", "_conditions": [ [
      { "key": "bfbe_shop_cart_items", "compare": ">=", "value": "1" },
      { "key": "dynamic_data", "dynamic_data": "{bfbe_cart_discount @static}", "compare": "empty_not" }
    ] ] }, "children": [
      { "name": "text-basic", "settings": { "text": "Discount" } },
      { "name": "text-basic", "settings": { "text": "{bfbe_cart_discount}" } }
    ] },
    { "name": "block", "settings": { "_cssClasses": "sum" }, "children": [
      { "name": "text-basic", "settings": { "text": "Total" } },
      { "name": "text-basic", "settings": { "text": "{bfbe_cart_total}" } }
    ] }
  ]
}
```

**An order lookup answered with tags.** From the order fixture (`fixture-shop-p8`, "The answer from tags"). BFB Order Status shows only its form; the block under it carries **Order found** and builds the answer from order tags and an Order items loop, which read the order the lookup found.

```json
{
  "name": "block",
  "settings": {},
  "children": [
    { "name": "bfbe-order-status", "settings": { "shows": "form", "buttonText": "Look it up" } },
    { "name": "block", "settings": { "_conditions": [ [ { "key": "bfbe_shop_order_found", "compare": "==", "value": "yes" } ] ] }, "children": [
      { "name": "text-basic", "settings": { "text": "Order {bfbe_order_number}: {bfbe_order_status}, {bfbe_order_items_count} items" } },
      { "name": "block", "settings": { "hasLoop": true, "query": { "objectType": "bfbeShopOrderItems" } }, "children": [
        { "name": "text-basic", "settings": { "text": "{bfbe_order_item_image:thumbnail} {bfbe_order_item_name} x {bfbe_order_item_quantity}" } }
      ] }
    ] }
  ]
}
```

**Sale facts and an in-cart note on each product row.** From the shop data fixture (`fixture-shop-data`), in a Bricks products loop (its `post__in` list left out). The row's `{post_id}` is the value of **Cart**, so each row asks about its own product; the note follows the cart.

```json
{
  "name": "container",
  "settings": { "hasLoop": true, "query": { "objectType": "post", "post_type": [ "product" ], "posts_per_page": 4 } },
  "children": [
    { "name": "text-basic", "settings": { "text": "{post_title}: save {bfbe_product_discount_percent @fallback:'0'}%, sale ends {bfbe_product_sale_end @fallback:'never'}" } },
    { "name": "text-basic", "settings": { "text": "This one is in your cart.", "_conditions": [ [ { "key": "bfbe_shop_product_in_cart", "compare": "contains", "value": "{post_id}" } ] ] } }
  ]
}
```

**Facts that follow the variation, and a trigger.** From the variation fixture (`fixture-shop-variation`), on a page with the product's own add to cart form. The tags print the parent's values and change with the choice; **Variation chosen** sets an attribute a stylesheet can answer.

```json
{
  "name": "block",
  "settings": {},
  "children": [
    { "name": "text-basic", "settings": { "text": "SKU {bfbe_variation_sku}, {bfbe_variation_price}, {bfbe_variation_stock_qty @fallback:'n/a'} left" } },
    { "name": "text-basic", "settings": { "text": "Your choice is ready.", "_interactions": [ { "id": "shvar1", "trigger": "bfbeVariationChosen", "action": "setAttribute", "target": "self", "actionAttributeKey": "data-chosen", "actionAttributeValue": "yes" } ] } }
  ]
}
```

## Gotchas

- **Live in text only.** In a link control, an image control or an attribute (`href`, `src`, `style`), a live tag prints the server's value once and is never corrected, so on a cached page it keeps the first visitor's figure. <!-- src: plugins/bfb-elements/includes/shop/class-tags.php:232-233 --> <!-- src: src/elements/shop-live/shop-live.js:163-165 -->
- **A tag outside its contexts prints its fallback.** A text-only tag in a link or image control gives its `@fallback` words or nothing; `tags.json` lists each tag's `contexts`. <!-- src: plugins/bfb-elements/includes/shop/class-tags.php:214-215 -->
- **Compare with `@static`.** Bricks' Dynamic data condition reads a live tag's marker markup, not its figure, so `empty_not` holds even with no discount; `{bfbe_cart_discount @static}` gives the plain value. <!-- src: plugins/bfb-elements/includes/shop/class-tags.php:235-239 --> <!-- src: dev/demo/shop (your-cart page, Sum: Discount) -->
- **Coupon tags answer in element settings only.** Written into a post's content or a review's text they stay as typed (`inPageText: false`). <!-- src: plugins/bfb-elements/includes/shop/class-tags.php:211 --> <!-- src: skills/bfbe-schemas/references/shop/tags.json (coupon tags) -->
- **Order tags need an order in hand.** Elsewhere, and with a wrong order key, they print their fallback or nothing. A page that prints an order is marked not to be cached. <!-- src: docs/elements/shop-data.md "Order tags" --> <!-- src: docs/elements/shop-orders.md "Cached pages" -->
- **Variation tags follow one form.** They need **Variation data** on and the product's own variations form on the page, and speak for the closest product template or product root; off, they print the parent's value. Where every variation costs the same, WooCommerce sends no price and the parent's stays. <!-- src: docs/elements/shop-variation.md "How the following works", "The tags" -->
- **Sale dates suit Bricks' Countdown.** Plain, `{bfbe_product_sale_end}` prints the store's local time, `2026-10-31 11:59`; set the Countdown's time zone to the store's. `{bfbe_product_stock_percent}` counts from the stock the tag first saw. <!-- src: docs/elements/shop-data.md "Product tags" -->
- **Offer, Toast and moment tags live inside their element.** Outside BFB Offer the offer tags print nothing; the Toast tags are placeholders its script fills; the moment tags read a Product moments row. <!-- src: plugins/bfb-elements-pro/includes/shop/class-offer.php:438-446 --> <!-- src: plugins/bfb-elements-pro/includes/shop/class-toast-shop.php:1-14 -->
- **Personal conditions decide on the server unless switched.** With **Check visitor conditions after the page loads** on (Shop, General), an element with a cart or customer condition starts hidden and waits for the answer; product conditions always decide on the server. <!-- src: plugins/bfb-elements/includes/shop/class-conditions.php:10-24 --> <!-- src: docs/elements/shop-data.md "Conditions" -->
- **Customer conditions never come back.** An element hidden by Customer bought, order count or total spent is not printed; a cart condition's element stays in the page, hidden. <!-- src: plugins/bfb-elements/includes/shop/class-conditions.php:26-33 -->
- **A product with no sale end never qualifies** for **Product sale ends within (days)**, whatever the number. <!-- src: plugins/bfb-elements-pro/includes/shop/class-data-conditions.php:27-28 --> <!-- src: docs/elements/shop-data.md "Conditions" -->
- **Variation chosen ignores resets.** It runs on a real choice only, and an element inside a variations form answers only its own form's choice. <!-- src: src/elements/shop-data/shop-data.js:33-36 -->
- **Product added needs a dispatcher.** In 2.0.0 none of the shop's own scripts sends `bfbe/woo/product-added`, so the trigger runs only for that event sent by a site's own script; BFB Toast's **When a product is added to the cart** reacts to adds by itself. <!-- src: src/elements/shop-data/shop-data.js:15; grep of src/elements for the event name, 2026-10-30 --> <!-- src: docs/elements/toast.md "With WooCommerce" -->
- **Triggers need Bricks' runner.** The bridge calls `bricksUtils.maybeRunOnceInteractions`; where Bricks does not offer it, our triggers do nothing. <!-- src: src/elements/shop-data/shop-data.js:4-7 -->

## Never do

- Do not put a live tag in a link, image or attribute that must stay right on a cached page.
- Do not compare a live tag in a Dynamic data condition without `@static`.
- Do not write a coupon tag into a post's content or a review; put it in an element's own setting.
- Do not use order tags away from an order in hand.
- Do not use `{bfbe_variation_*}` away from its product's add to cart form.
- Do not guard content meant for buyers only with a cart condition; use a customer condition.
- Do not rely on **Product added** without a script of the site's own that sends `bfbe/woo/product-added`.
