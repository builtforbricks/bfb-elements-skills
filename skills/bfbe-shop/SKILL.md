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
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

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
- `shop-filters` **Filters** (free): Collapsible categories in product filters, and filters that understand variations.
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

The shop's own elements, a skill each (a part inside one of them is in its parent's skill): `bfbe-applied-coupons`, `bfbe-bought-together`, `bfbe-bundle-builder`, `bfbe-buy-now`, `bfbe-cart-goals`, `bfbe-cart-quantity`, `bfbe-cart-shipping`, `bfbe-compare-button`, `bfbe-compare-tray`, `bfbe-delivery-estimate`, `bfbe-empty-cart-button`, `bfbe-linked-products`, `bfbe-offer`, `bfbe-order-status`, `bfbe-payment-icons`, `bfbe-product-3d`, `bfbe-product-badges`, `bfbe-product-questions`, `bfbe-quantity-breaks`, `bfbe-quote-list-button`, `bfbe-rating-summary`, `bfbe-review-form`, `bfbe-review-sort`, `bfbe-review-votes`, `bfbe-save-later-button`, `bfbe-saved-item-button`, `bfbe-size-guide`, `bfbe-spec-scales`, `bfbe-sticky-buy-bar`, `bfbe-tax-switch`, `bfbe-view-switch`, `bfbe-wishlist-action`, `bfbe-wishlist-bar`, `bfbe-wishlist-button`, `bfbe-withdrawal-button`.

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

_Not written yet._

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
