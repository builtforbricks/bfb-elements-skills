---
name: bfbe-shop-tags-and-conditions
description: "Use for the {bfbe_*} dynamic tags of the group BFB Shop (product, cart, order, customer, variation facts, live after load on cached pages), the shop conditions and the shop interaction triggers (BFB Shop tags and conditions, `shop-tags-and-conditions`). Read before writing these settings."
---

# BFB Shop tags and conditions (`shop-tags-and-conditions`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 2.0.0 or later, and BFB Elements Pro 2.0.0 or later for the groups marked Pro, WooCommerce active, the feature switches on (WordPress menu BFB Elements, Elements): `shop-data`, `shop-variation`. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/shop-tags-and-conditions.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/shop-tags-and-conditions/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

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

_Not written yet._

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
