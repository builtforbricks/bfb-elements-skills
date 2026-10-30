---
name: bfbe-shop-loops
description: "Use for the shop's query loop types on Bricks' Container, Block and Div (best sellers, related, recently viewed, variations, images, reviews, wishlist, compare, quote, saved for later, orders, order items and totals, product finder, product moments, pin product) and their set controls, with product cards built from Bricks' own elements (BFB Shop loops, `shop-loops`). Read before writing these settings."
---

# BFB Shop loops (`shop-loops`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 2.0.0 or later, and BFB Elements Pro 2.0.0 or later for the groups marked Pro, WooCommerce active, the feature switches on (WordPress menu BFB Elements, Elements): `shop-reviews-loop`, `shop-lists`, `shop-loops`, `shop-orders`, `shop-cart-lines`. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/shop-loops.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/shop-loops/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

## Where it lives
A feature, not an element: its groups are added to Bricks' own elements, on the Content tab after Bricks' own groups. By element:
- Block, Container and Div (`block`, `container`, `div`): BFB Shop reviews (`bfbeShopQbfbeShopReviews`), BFB Product finder (`bfbeShopQbfbeShopFinder`), BFB Wishlist (`bfbeShopQbfbeShopWishlist`), BFB Products being compared (`bfbeShopQbfbeShopCompare`), BFB Quote list (`bfbeShopQbfbeShopQuote`), BFB Shop products (`bfbeShopQbfbeShopProducts`), BFB Shop variations (`bfbeShopQbfbeShopVariations`), BFB Shop images (`bfbeShopQbfbeShopImages`), BFB Order totals (`bfbeShopQbfbeShopOrderTotals`), BFB Customer orders (`bfbeShopQbfbeShopOrders`), BFB Product moments (`bfbeShopQbfbeShopMoments`).

## Query loop types
Chosen as Bricks' Query, Type (`query.objectType`) on a Container, Block or Div with Use query loop on (`hasLoop`). Every one, with its set and its loop object, is in `../bfbe-schemas/references/shop/loops.json`.
- `bfbeShopCompare` **Products being compared**: loop object `post`; set controls in `bfbeShopQbfbeShopCompare`; Pro, switch `shop-lists`.
- `bfbeShopFinder` **BFB Shop product finder**: loop object `post`; set controls in `bfbeShopQbfbeShopFinder`; Pro.
- `bfbeShopImages` **BFB Shop images**: loop object `post`; set controls in `bfbeShopQbfbeShopImages`; Pro, switch `shop-loops`.
- `bfbeShopMoments` **BFB Product moments**: loop object `post`; set controls in `bfbeShopQbfbeShopMoments`; Pro.
- `bfbeShopOrderItems` **BFB Shop order items**: loop object `bfbeShopOrderItem`; no set controls; Pro, switch `shop-orders`.
- `bfbeShopOrderTotals` **BFB Shop order totals**: loop object `bfbeShopOrderTotal`; set controls in `bfbeShopQbfbeShopOrderTotals`; Pro, switch `shop-orders`.
- `bfbeShopOrders` **BFB Shop customer orders**: loop object `order`; set controls in `bfbeShopQbfbeShopOrders`; Pro, switch `shop-orders`.
- `bfbeShopPinProduct` **BFB Pin product**: loop object `post`; no set controls; Pro.
- `bfbeShopProducts` **BFB Shop products**: loop object `post`; set controls in `bfbeShopQbfbeShopProducts`; Pro, switch `shop-loops`.
- `bfbeShopQuote` **Quote list**: loop object `post`; set controls in `bfbeShopQbfbeShopQuote`; Pro, switch `shop-lists`.
- `bfbeShopReviews` **BFB Shop reviews**: loop object `comment`; set controls in `bfbeShopQbfbeShopReviews`; free, switch `shop-reviews-loop`.
- `bfbeShopSaved` **Saved for later**: loop object `post`; no set controls; Pro, switch `shop-cart-lines`.
- `bfbeShopVariations` **BFB Shop variations**: loop object `post`; set controls in `bfbeShopQbfbeShopVariations`; Pro, switch `shop-loops`.
- `bfbeShopWishlist` **Wishlist**: loop object `post`; set controls in `bfbeShopQbfbeShopWishlist`; Pro, switch `shop-lists`.

## Settings that decide the build

### Block, Container and Div (`block`, `container`, `div`)

#### BFB Shop reviews (`bfbeShopQbfbeShopReviews`)
Free, switch `shop-reviews-loop`.
The whole group shows only when `query.objectType` is `bfbeShopReviews`.
- `bfbeShopReviewsProduct` (select) **Reviews of**: options: `current` This product (default), `all` All products, `chosen` Chosen products; only when `query.objectType` is `bfbeShopReviews` and `hasLoop` is set
- `bfbeShopReviewsIds` (text) **Products**: placeholder 12, 34, BFBE-SKU; dynamic data accepted; only when `query.objectType` is `bfbeShopReviews` and `hasLoop` is set and `bfbeShopReviewsProduct` is `chosen`. Ids or SKUs, separated by commas.
- `bfbeShopReviewsCount` (number) **Reviews per page**: placeholder 6; only when `query.objectType` is `bfbeShopReviews` and `hasLoop` is set
- `bfbeShopReviewsMinRating` (number) **Minimum rating**: placeholder 1; only when `query.objectType` is `bfbeShopReviews` and `hasLoop` is set
- `bfbeShopReviewsVerified` (checkbox) **Verified buyers only**: only when `query.objectType` is `bfbeShopReviews` and `hasLoop` is set
- `bfbeShopReviewsOrder` (select) **Order**: options: `newest` Newest first (default), `highest` Highest rating first, `lowest` Lowest rating first; only when `query.objectType` is `bfbeShopReviews` and `hasLoop` is set

#### BFB Product finder (`bfbeShopQbfbeShopFinder`)
Pro.
The whole group shows only when `query.objectType` is `bfbeShopFinder`.
- `bfbeShopFindNone` (text) **Nothing matches**: placeholder Nothing matches your answers.; only when `query.objectType` is `bfbeShopFinder` and `hasLoop` is set
- `bfbeShopFindAgain` (text) **Start again words**: placeholder Start again; only when `query.objectType` is `bfbeShopFinder` and `hasLoop` is set. Bricks' own No results content, when set, shows instead.
Styling, in the schema file: `bfbeShopFindNoneBg`, `bfbeShopFindNoneBorder`, `bfbeShopFindNonePad`, `bfbeShopFindNoneType`, `bfbeShopFindNoneLink`.

#### BFB Wishlist (`bfbeShopQbfbeShopWishlist`)
Pro, switch `shop-lists`.
The whole group shows only when `query.objectType` is `bfbeShopWishlist`.
- `bfbeShopWishlistActions` (select) **Buttons on each row**: options: `on` On (default), `off` Off; only when `query.objectType` is `bfbeShopWishlist` and `hasLoop` is set
- `bfbeShopWishlistAfterMove` (select) **After Move to cart**: options: `remove` Take it off the list (default), `keep` Keep it on the list; only when `query.objectType` is `bfbeShopWishlist` and `hasLoop` is set and `bfbeShopWishlistActions` is not `off`
- `bfbeShopWishlistMoveText` (text) **Move to cart word**: placeholder Move to cart; only when `query.objectType` is `bfbeShopWishlist` and `hasLoop` is set and `bfbeShopWishlistActions` is not `off`. Add to cart while the row stays on the list.
- `bfbeShopWishlistRemoveText` (text) **Remove word**: placeholder Remove; only when `query.objectType` is `bfbeShopWishlist` and `hasLoop` is set and `bfbeShopWishlistActions` is not `off`
- `bfbeShopWishlistBoughtText` (text) **Mark as bought word**: placeholder Mark as bought; only when `query.objectType` is `bfbeShopWishlist` and `hasLoop` is set
- `bfbeShopWishlistMoveLook` (select) **Move to list: open list**: options: `native` As the browser draws it (default), `custom` Styled with the controls below; only when `query.objectType` is `bfbeShopWishlist` and `hasLoop` is set and `bfbeShopWishlistActions` is not `off`. Phones keep their own list either way.
- `bfbeShopWishlistType` (select) **Post type**: options: `product` Products (default), `post` Posts, `page` Pages, `bfbe_review` Review, `bfbe_feature` Feature visuals, `bricks_template` My Templates; only when `query.objectType` is `bfbeShopWishlist` and `hasLoop` is set
Styling, in the schema file: `bfbeShopWishlistMoveTypography`, `bfbeShopWishlistMoveBackground`, `bfbeShopWishlistMoveBorder`, `bfbeShopWishlistMovePadding`, `bfbeShopWishlistMoveChevron`, `bfbeShopWishlistMovePanelBg`, `bfbeShopWishlistMovePanelBorder`, `bfbeShopWishlistMovePanelShadow`, `bfbeShopWishlistMovePanelPadding`, `bfbeShopWishlistMoveOptTypography`, `bfbeShopWishlistMoveOptPadding`, `bfbeShopWishlistMoveOptHover`, `bfbeShopWishlistMoveHoverText`, `bfbeShopWishlistMoveOptOnBg`, `bfbeShopWishlistMoveOptOnColor`, `bfbeShopWishlistMoveTick`.

#### BFB Products being compared (`bfbeShopQbfbeShopCompare`)
Pro, switch `shop-lists`.
The whole group shows only when `query.objectType` is `bfbeShopCompare`.
- `bfbeShopCompareActions` (select) **Remove on each row**: options: `on` On (default), `off` Off; only when `query.objectType` is `bfbeShopCompare` and `hasLoop` is set
- `bfbeShopCompareRemoveText` (text) **Remove word**: placeholder Remove; only when `query.objectType` is `bfbeShopCompare` and `hasLoop` is set and `bfbeShopCompareActions` is not `off`

#### BFB Quote list (`bfbeShopQbfbeShopQuote`)
Pro, switch `shop-lists`.
The whole group shows only when `query.objectType` is `bfbeShopQuote`.
- `bfbeShopQuoteActions` (select) **Quantity and Remove on each row**: options: `on` On (default), `off` Off; only when `query.objectType` is `bfbeShopQuote` and `hasLoop` is set
- `bfbeShopQuoteUpdateText` (text) **Update word**: placeholder Update; only when `query.objectType` is `bfbeShopQuote` and `hasLoop` is set and `bfbeShopQuoteActions` is not `off`
- `bfbeShopQuoteRemoveText` (text) **Remove word**: placeholder Remove; only when `query.objectType` is `bfbeShopQuote` and `hasLoop` is set and `bfbeShopQuoteActions` is not `off`

#### BFB Shop products (`bfbeShopQbfbeShopProducts`)
Pro, switch `shop-loops`.
The whole group shows only when `query.objectType` is `bfbeShopProducts`.
- `bfbeShopSet` (select) **Set**: options: `best_sellers` Best sellers (default), `trending` Trending, `top_rated` Top rated, `new` New arrivals, `on_sale` On sale, `price_drops` Price drops, `back_in_stock` Back in stock, `bought` Bought before, `recent` Recently viewed, `hotspots` Pinned on an image; only when `query.objectType` is `bfbeShopProducts` and `hasLoop` is set
- `bfbeShopCount` (number) **Products per page**: placeholder 8; only when `query.objectType` is `bfbeShopProducts` and `hasLoop` is set
- `bfbeShopDays` (number) **Within the last days**: placeholder 30; only when `query.objectType` is `bfbeShopProducts` and `hasLoop` is set and `bfbeShopSet` is `trending` or `new` or `price_drops` or `back_in_stock`. New arrivals: 0 means the newest, however old.
- `bfbeShopMinReviews` (number) **Minimum reviews**: placeholder 1; only when `query.objectType` is `bfbeShopProducts` and `hasLoop` is set and `bfbeShopSet` is `top_rated`
- `bfbeShopHotspots` (text) **Element id**: placeholder abc123; only when `query.objectType` is `bfbeShopProducts` and `hasLoop` is set and `bfbeShopSet` is `hotspots`. Empty: the nearest BFB Image Hotspots.
- `bfbeShopRecentWhile` (select) **While there is nothing yet**: options: `` Nothing (default), `best_sellers` Best sellers, `trending` Trending, `top_rated` Top rated, `new` New arrivals, `on_sale` On sale, `price_drops` Price drops, `back_in_stock` Back in stock; only when `query.objectType` is `bfbeShopProducts` and `hasLoop` is set and `bfbeShopSet` is `recent`
- `bfbeShopSkipCurrent` (checkbox) **Leave out the product on this page**: only when `query.objectType` is `bfbeShopProducts` and `hasLoop` is set

#### BFB Shop variations (`bfbeShopQbfbeShopVariations`)
Pro, switch `shop-loops`.
The whole group shows only when `query.objectType` is `bfbeShopVariations`.
- `bfbeShopVariationsProduct` (text) **Product**: placeholder This product; dynamic data accepted; only when `query.objectType` is `bfbeShopVariations` and `hasLoop` is set. An id or SKU; empty means this product.
- `bfbeShopVariationsInStock` (checkbox) **In stock only**: only when `query.objectType` is `bfbeShopVariations` and `hasLoop` is set

#### BFB Shop images (`bfbeShopQbfbeShopImages`)
Pro, switch `shop-loops`.
The whole group shows only when `query.objectType` is `bfbeShopImages`.
- `bfbeShopImagesProduct` (text) **Product**: placeholder This product; dynamic data accepted; only when `query.objectType` is `bfbeShopImages` and `hasLoop` is set. An id or SKU; empty means this product.
- `bfbeShopImagesFollow` (checkbox) **Follow the chosen variation**: only when `query.objectType` is `bfbeShopImages` and `hasLoop` is set
- `bfbeShopImagesOption` (select) **Follow one option before the rest**: options: `off` Off, `pa_colour` Colour, `pa_material` Material, `pa_size` Size, `pa_warmth` Warmth; only when `query.objectType` is `bfbeShopImages` and `hasLoop` is set and `bfbeShopImagesFollow` is set. Its images show as soon as it is chosen.
- `bfbeShopImagesFeatured` (checkbox) **Leave out the featured image**: only when `query.objectType` is `bfbeShopImages` and `hasLoop` is set

#### BFB Order totals (`bfbeShopQbfbeShopOrderTotals`)
Pro, switch `shop-orders`.
The whole group shows only when `query.objectType` is `bfbeShopOrderTotals`.
- `bfbeShopTotalsLeave` (select) **Leave out**: options: `payment_method` Payment method, `order_total` Total; only when `query.objectType` is `bfbeShopOrderTotals` and `hasLoop` is set. Rows you show elsewhere on the page.

#### BFB Customer orders (`bfbeShopQbfbeShopOrders`)
Pro, switch `shop-orders`.
The whole group shows only when `query.objectType` is `bfbeShopOrders`.
- `bfbeShopOrdersPer` (number) **Orders per page**: placeholder 3; only when `query.objectType` is `bfbeShopOrders` and `hasLoop` is set
- `bfbeShopOrdersStatus` (select) **Statuses**: options: `account` As the account lists them (default), `paid` Paid; only when `query.objectType` is `bfbeShopOrders` and `hasLoop` is set. Paid means processing and completed.

#### BFB Product moments (`bfbeShopQbfbeShopMoments`)
Pro.
The whole group shows only when `query.objectType` is `bfbeShopMoments`.
- `bfbeShopMomentsPlayer` (text) **Element id**: placeholder abc123; only when `query.objectType` is `bfbeShopMoments` and `hasLoop` is set. Empty: the nearest BFB Video Player.
<!-- bfbe:generated:end -->

## Rendered DOM

A shop loop is Bricks' own query loop: Bricks repeats the looping Container, Block or Div once per row and renders its children for that row, exactly as in a posts loop. The type decides what a row is:

| Type (`query.objectType`) | A row is | Switch |
|---|---|---|
| `bfbeShopProducts`, `bfbeShopFinder`, `bfbeShopPinProduct`, `bfbeShopMoments` | a product post | `shop-loops` for products; finder needs BFB Advanced Forms; pins and moments come with Image Hotspots and Video Player |
| `bfbeShopWishlist`, `bfbeShopCompare`, `bfbeShopQuote` | a product, or a variation's own post | `shop-lists` |
| `bfbeShopSaved` | a saved product or variation | `shop-cart-lines` |
| `bfbeShopVariations` | a variation post (`product_variation`) | `shop-loops` |
| `bfbeShopImages` | an attachment post: the featured image, then the gallery | `shop-loops` |
| `bfbeShopReviews` | a review (`comment`); the current post is the reviewed product | `shop-reviews-loop` (free) |
| `bfbeShopOrders` | the signed-in customer's order | `shop-orders` |
| `bfbeShopOrderItems`, `bfbeShopOrderTotals` | a line of the order in hand, a total row of it | `shop-orders` |

What the shop adds to the rows:

- **Recently viewed** (`bfbeShopSet: "recent"`): the server draws the placeholder set's rows marked `data-bfbe-shop-loop="<page>:<element>"` and `data-bfbe-shop-placeholder="1"`, or, with none, Bricks' no-results content plus `div.bfbe-shop-loop__wait[data-bfbe-shop-loop]`. Once on screen, the browser sends its ids and the real rows replace them.
- **Images that follow the variation**: each row carries `data-bfbe-shop-loop-follow`, `data-bfbe-shop-product` and, with an option followed first, `data-bfbe-shop-loop-option="attribute_pa_colour"`; a choice redraws the rows on the server.
- **List loops**: each row's root carries `data-bfbe-list-row="<kind>:<page>:<element>"` and `data-bfbe-list-item="<product>:<variation>"`. With **Buttons on each row** on, the row's buttons go in a `div.bfbe-lrow__actions` before the root's closing tag, each a `form.bfbe-lrow__form` with a `button.bfbe-lrow__btn` (a quote row adds `input.bfbe-lrow__qty`). An empty list prints `div.bfbe-lrow__wait` beside Bricks' no-results content.
- **Saved for later** with nothing saved prints `div.bfbe-saved__wait`, for a guest's list from a cached page to fill in.
- **Product finder** with no match: `div.bfbe-find__none` with `p.bfbe-find__words` (**Nothing matches**) and `p.bfbe-find__again` holding the Start again link, styled by the `bfbeShopFindNone*` controls; Bricks' own no-results content, when set, shows in `div.bfbe-find__own` instead.
- **Files**: `shop-loops.min.js` loads only with a Recently viewed loop, a following images loop, or on a product page while recently viewed is remembered. The list loops ride the Lists feature's script. Every other set is server-side only.

## Wiring to other elements

- **Choosing a type.** Tick **Use query loop** (`hasLoop: true`) on a Container, Block or Div and set `query: { "objectType": "<type>" }`. The type's own group (**BFB Shop products**, **BFB Shop reviews**, ...) then shows on the element's Content tab; its keys sit beside `query`, not inside it.
- **A card from Bricks' own elements.** In a product row, Bricks' **Product title**, **Product price**, **Product rating**, **Product stock**, **Add to cart** and an **Image** with `{featured_image}` read the row's product, as do `{post_title}`, `{post_url}` and `{woo_*}` tags. BFB parts read it too: Product Badges, Wishlist Button, Compare Button, Quote List Button and every `{bfbe_product_*}` tag.
- **Which tags in which loop** (all under BFB Shop, `bfbe-shop-tags-and-conditions`):

| Loop | Tags that read the row |
|---|---|
| Product rows (products, lists, saved, finder, pins, moments) | `{bfbe_product_*}`, brand and EU tags, Bricks' product tags |
| Product moments | also `{bfbe_moment_time}`, `{bfbe_moment_seconds}`, `{bfbe_moment_words}`, `{bfbe_moment_chapter}` |
| Variations | Product title (the variation's name), price, stock, `{woo_product_sku}`, `{bfbe_variation_sku}` |
| Images | `{bfbe_product_image}` (`:size`), `{post_id}` (the attachment), `{post_title}` |
| Reviews | `{bfbe_review_rating}`, `{bfbe_review_stars:svg}`, `{bfbe_review_author}`, `{bfbe_review_date:format}`, `{bfbe_review_text}`, `{bfbe_review_verified}`, `{bfbe_review_product}`, `{bfbe_review_product_url}`, `{bfbe_review_photos}` (Pro) |
| Customer orders | every `{bfbe_order_*}` tag, for that order |
| Order items | `{bfbe_order_item_name}`, `_quantity`, `_price`, `_total`, `_sku`, `_options`, `_image:size`, `_url`; Bricks' product tags where the product still exists |
| Order totals | `{bfbe_order_total_label}`, `{bfbe_order_total_value}`, `{bfbe_order_total_key}` |

- **Nesting.** A **BFB Shop order items** loop inside a Customer orders row lists that order's lines. On a thank-you, view-order or order-pay page, or after a BFB Order Status lookup, it lists the page's order with no outer loop. Order totals reads the same order.
- **The finder** is filled by a BFB Advanced Forms form with **Find products from the answers** (`bfbe-form`); the form names the loop or takes the first finder loop on the page.
- **Pins and moments.** **Pinned on an image** (`bfbeShopSet: "hotspots"`) lists a BFB Image Hotspots' product pins, and **BFB Product moments** lists a BFB Video Player's moments. Leave **Element id** (`bfbeShopHotspots`, `bfbeShopMomentsPlayer`) empty to take the nearest one, else the only one on the page. A product pin's own block is a **BFB Pin product** loop of one row, set as it renders (`bfbe-hotspots`).
- **Row buttons.** Saved for later rows take **BFB Saved Item Button** (`bfbe-saved-item-button`), one for Move to cart, one for Remove. Wishlist, compare and quote rows draw their own buttons (above), or none with the row's **Buttons on each row** (or **Remove on each row**, **Quantity and Remove on each row**) set to `off`.
- **Pagination.** Bricks' **Pagination** element works on every type: set its Query to the loop. Live filters reach the products loop only.
- **The empty state** is Bricks' own: the query's **No results** text (`query.no_results_text`) or template, for every type. Recently viewed first shows **While there is nothing yet** (`bfbeShopRecentWhile`), and the finder its own box unless Bricks' no-results content is set.

## Verified patterns

**A product card in a Trending loop.** From the demo shop's product template (`bfb-demo-product`, "Trending this month"). `bfbeShopSkipCurrent` leaves out the product on the page; Bricks' product elements and the BFB parts all read the row's product. Trimmed: the demo's look, its hover effects and a card button label the panel hides without **Swatches on the card**.

```json
{
  "name": "block",
  "settings": { "hasLoop": true, "query": { "objectType": "bfbeShopProducts" }, "bfbeShopSet": "trending", "bfbeShopCount": 8, "bfbeShopDays": 30, "bfbeShopSkipCurrent": true, "_cssClasses": "card" },
  "children": [
    { "name": "block", "settings": { "_cssClasses": "card__media" }, "children": [
      { "name": "image", "settings": { "image": { "useDynamicData": "{featured_image}", "size": "woocommerce_single" }, "link": { "type": "external", "url": "{post_url}" } } },
      { "name": "bfbe-product-badges", "settings": { "max": 2, "layout": "stacked" } },
      { "name": "bfbe-wishlist-button", "settings": { "content": "icon" } }
    ] },
    { "name": "text-basic", "settings": { "text": "{bfbe_product_brand @fallback:'Our studio'}" } },
    { "name": "product-title", "settings": { "tag": "h3", "linkToProduct": true } },
    { "name": "product-rating", "settings": { "noRatingsText": "No reviews yet" } },
    { "name": "product-price", "settings": {} },
    { "name": "block", "settings": { "_cssClasses": "card__row" }, "children": [
      { "name": "product-add-to-cart", "settings": {} },
      { "name": "bfbe-compare-button", "settings": {} }
    ] }
  ]
}
```

**Recent orders with each order's pictures.** From the demo shop's account dashboard (`bfb-demo-account-dashboard`). A Customer orders loop of three, an Order items loop nested in each row, and Bricks' `no_results_text` for a customer with no orders yet.

```json
{
  "name": "block",
  "settings": { "hasLoop": true, "query": { "objectType": "bfbeShopOrders", "no_results_text": "Your orders show here once you place one." }, "bfbeShopOrdersPer": 3, "_cssClasses": "order-card" },
  "children": [
    { "name": "text-basic", "settings": { "text": "Order {bfbe_order_number}, {bfbe_order_status}" } },
    { "name": "text-basic", "settings": { "text": "{bfbe_order_date:j F Y}" } },
    { "name": "block", "settings": { "hasLoop": true, "query": { "objectType": "bfbeShopOrderItems" } }, "children": [
      { "name": "image", "settings": { "image": { "useDynamicData": "{bfbe_order_item_image}", "size": "woocommerce_gallery_thumbnail" } } }
    ] },
    { "name": "text-basic", "settings": { "text": "{bfbe_order_total}" } },
    { "name": "text-link", "settings": { "text": "View order", "link": { "type": "external", "url": "{bfbe_order_view_url}" } } }
  ]
}
```

**A wall of reviews from every product.** From the demo shop's home page ("Review"), with **Reviews of** set to All products in place of the demo's list of SKUs. Verified buyers with four stars or more, six per page; the stars are inline SVG with words for a screen reader.

```json
{
  "name": "block",
  "settings": { "hasLoop": true, "query": { "objectType": "bfbeShopReviews" }, "bfbeShopReviewsProduct": "all", "bfbeShopReviewsMinRating": 4, "bfbeShopReviewsVerified": true, "bfbeShopReviewsCount": 6 },
  "children": [
    { "name": "text-basic", "settings": { "text": "{bfbe_review_stars:svg}" } },
    { "name": "text-basic", "settings": { "text": "{bfbe_review_text}" } },
    { "name": "text-basic", "settings": { "text": "<strong>{bfbe_review_author}</strong> {bfbe_review_verified} &middot; <a href=\"{bfbe_review_product_url}\">{bfbe_review_product}</a>" } }
  ]
}
```

**A stacked gallery that follows the colour.** From the demo shop's stacked product template (`bfb-demo-product-stack`). `bfbeShopImagesFollow` redraws the rows for the chosen colour; one **Lightbox ID** on every row lets Bricks' lightbox page through the whole stack.

```json
{
  "name": "block",
  "settings": { "hasLoop": true, "query": { "objectType": "bfbeShopImages" }, "bfbeShopImagesFollow": true, "_cssClasses": "stack" },
  "children": [
    { "name": "image", "settings": { "image": { "useDynamicData": "{bfbe_product_image}", "size": "woocommerce_single" }, "link": "lightbox", "lightboxId": "stack", "lightboxImageSize": "full" } }
  ]
}
```

**A wishlist row.** From the demo shop's account lists template (`bfb-demo-account-lists`). Bricks' elements draw the product; the loop appends Move to cart and Remove inside the row, so its root stays a plain Block.

```json
{
  "name": "block",
  "settings": { "hasLoop": true, "query": { "objectType": "bfbeShopWishlist", "no_results_text": "Nothing on this list yet." }, "_cssClasses": "wish-row" },
  "children": [
    { "name": "image", "settings": { "image": { "useDynamicData": "{featured_image}", "size": "woocommerce_thumbnail" } } },
    { "name": "product-title", "settings": { "tag": "h4", "linkToProduct": true } },
    { "name": "product-price", "settings": {} }
  ]
}
```

## Gotchas

- **The type's controls need the loop.** Every set control is offered only with `hasLoop` on and `query.objectType` set to its type, and only on Container, Block and Div; written otherwise, it is dropped. <!-- src: plugins/bfb-elements/includes/shop/class-query-type.php:96-118 -->
- **Each type has its own switch.** Products, variations and images need **Shop loops**; orders, items and totals **Order loops** (their order tags need **Shop data**); reviews **Reviews loop**; the three lists **Lists**; saved for later **Cart lines**. The finder needs BFB Advanced Forms. <!-- src: plugins/bfb-elements-pro/includes/shop/class-loops.php:51-57 --> <!-- src: plugins/bfb-elements-pro/includes/shop/class-orders-set.php:47, 65 --> <!-- src: plugins/bfb-elements-pro/includes/shop/class-lists.php:78-83 --> <!-- src: plugins/bfb-elements-pro/includes/shop/class-save-for-later.php:64-67 --> <!-- src: plugins/bfb-elements-pro/includes/shop/class-finder.php:52-54 --> <!-- src: docs/elements/shop-orders.md "Switch" -->
- **Per page is the set's own control.** Products read **Products per page** (`bfbeShopCount`, 8), reviews `bfbeShopReviewsCount` (6), orders `bfbeShopOrdersPer` (3). Variations, images, saved for later and the three lists draw every row. <!-- src: plugins/bfb-elements-pro/includes/shop/class-products-set.php:136 --> <!-- src: plugins/bfb-elements-pro/includes/shop/class-variations-set.php:92 --> <!-- src: plugins/bfb-elements-pro/includes/shop/class-images-set.php:239 --> <!-- src: plugins/bfb-elements-pro/includes/shop/class-list-set.php:89 -->
- **Recently viewed is empty until switched on.** The visit is recorded only with **Remember recently viewed products** on (Shop, General), off by default, and with consent where BFB Cookie Consent asks for it. Until then the loop shows **While there is nothing yet**, or nothing. <!-- src: plugins/bfb-elements-pro/includes/shop/class-loops.php:79-95 --> <!-- src: docs/elements/shop-loops.md "Recently viewed" -->
- **Bought before is personal.** It lists what the signed-in customer bought, and a guest sees nothing; a page cache would serve one customer's products to the next, so keep it on account pages. <!-- src: docs/elements/shop-loops.md "BFB Shop products" -->
- **Sets count real data.** Best sellers leaves out products that never sold; Trending counts paid orders in the window, kept ten minutes; Back in stock counts restocks after the feature was on; Price drops needs the price log. A new shop shows empty sets. <!-- src: docs/elements/shop-loops.md "BFB Shop products" --> <!-- src: plugins/bfb-elements-pro/includes/shop/class-loops.php:128 -->
- **A variation row has no buy form.** Add to cart prints a link to the parent product with the options chosen, and Product meta and Product rating print nothing, since WooCommerce keeps them on the parent. <!-- src: docs/elements/shop-loops.md "BFB Shop variations" -->
- **Order loops answer only where an order is in hand.** Customer orders shows the signed-in customer's own; Order items and totals need a Customer orders row, an order page with its key, or a BFB Order Status lookup. A page that prints an order is marked not to be cached. <!-- src: docs/elements/shop-orders.md "BFB Shop order items", "Cached pages" -->
- **Live filters skip most types.** Bricks' filters reach post, term and user queries, so only the products loop takes them; the reviews, variations and images loops ignore them. <!-- src: plugins/bfb-elements/includes/shop/class-query-type.php:21-22 --> <!-- src: docs/elements/shop-loops.md "Pagination and filters" -->
- **Page two on a single post goes back to the post.** WordPress sends a paginated loop's later pages on a single product or post back to page one; paginate on a page or an archive. <!-- src: docs/elements/shop-loops.md "Pagination and filters" -->
- **List buttons are forms inside the row.** They are appended before the row root's closing tag, so a row root that is a link (`tag: "a"`) puts forms inside a link. A list view inside another query loop is not redrawn for guests. <!-- src: plugins/bfb-elements-pro/includes/shop/class-list-set.php:159-180 --> <!-- src: docs/elements/shop-lists.md "Limits" -->
- **A pin's block needs its loop set to edit it.** On the page the block is a Pin product loop as it renders; in the builder, set it yourself (Query loop, BFB Pin product) or edits inside it draw for the page instead. <!-- src: docs/elements/hotspots.md:97-99 -->

## Never do

- Do not write a set control without `hasLoop: true` and its type in `query.objectType`.
- Do not put a shop type on an element other than Container, Block or Div.
- Do not set Bricks' own posts per page for a product set; use `bfbeShopCount`.
- Do not use **Bought before** on a page a cache serves to everyone.
- Do not make a list loop's row element a link; its buttons are forms.
- Do not paginate a shop loop on a single product or post.
- Do not expect live filters on the reviews, variations or images loops.
