---
name: bfbe-shop-loops
description: "Use for the shop's query loop types on Bricks' Container, Block and Div (best sellers, related, recently viewed, variations, images, reviews, wishlist, compare, quote, saved for later, orders, order items and totals, product finder, product moments, pin product) and their set controls, with product cards built from Bricks' own elements (BFB Shop loops, `shop-loops`). Read before writing these settings."
---

# BFB Shop loops (`shop-loops`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 2.0.0 or later, and BFB Elements Pro 2.0.0 or later for the groups marked Pro, WooCommerce active, the feature switches on (WordPress menu BFB Elements, Elements): `shop-reviews-loop`, `shop-orders`. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/shop-loops.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/shop-loops/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

## Where it lives
A feature, not an element: its groups are added to Bricks' own elements, on the Content tab after Bricks' own groups. By element:
- Block, Container and Div (`block`, `container`, `div`): BFB Shop reviews (`bfbeShopQbfbeShopReviews`), BFB Product finder (`bfbeShopQbfbeShopFinder`), BFB Wishlist (`bfbeShopQbfbeShopWishlist`), BFB Products being compared (`bfbeShopQbfbeShopCompare`), BFB Quote list (`bfbeShopQbfbeShopQuote`), BFB Shop products (`bfbeShopQbfbeShopProducts`), BFB Shop variations (`bfbeShopQbfbeShopVariations`), BFB Shop images (`bfbeShopQbfbeShopImages`), BFB Order totals (`bfbeShopQbfbeShopOrderTotals`), BFB Customer orders (`bfbeShopQbfbeShopOrders`), BFB Product moments (`bfbeShopQbfbeShopMoments`).

## Query loop types
Chosen as Bricks' Query, Type (`query.objectType`) on a Container, Block or Div with Use query loop on (`hasLoop`). Every one, with its set and its loop object, is in `../bfbe-schemas/references/shop/loops.json`.
- `bfbeShopCompare` **Products being compared**: loop object `post`; set controls in `bfbeShopQbfbeShopCompare`; Pro.
- `bfbeShopFinder` **BFB Shop product finder**: loop object `post`; set controls in `bfbeShopQbfbeShopFinder`; Pro.
- `bfbeShopImages` **BFB Shop images**: loop object `post`; set controls in `bfbeShopQbfbeShopImages`; Pro.
- `bfbeShopMoments` **BFB Product moments**: loop object `post`; set controls in `bfbeShopQbfbeShopMoments`; Pro.
- `bfbeShopOrderItems` **BFB Shop order items**: loop object `bfbeShopOrderItem`; no set controls; Pro, switch `shop-orders`.
- `bfbeShopOrderTotals` **BFB Shop order totals**: loop object `bfbeShopOrderTotal`; set controls in `bfbeShopQbfbeShopOrderTotals`; Pro, switch `shop-orders`.
- `bfbeShopOrders` **BFB Shop customer orders**: loop object `order`; set controls in `bfbeShopQbfbeShopOrders`; Pro, switch `shop-orders`.
- `bfbeShopPinProduct` **BFB Pin product**: loop object `post`; no set controls; Pro.
- `bfbeShopProducts` **BFB Shop products**: loop object `post`; set controls in `bfbeShopQbfbeShopProducts`; Pro.
- `bfbeShopQuote` **Quote list**: loop object `post`; set controls in `bfbeShopQbfbeShopQuote`; Pro.
- `bfbeShopReviews` **BFB Shop reviews**: loop object `comment`; set controls in `bfbeShopQbfbeShopReviews`; free, switch `shop-reviews-loop`.
- `bfbeShopSaved` **Saved for later**: loop object `post`; no set controls; Pro.
- `bfbeShopVariations` **BFB Shop variations**: loop object `post`; set controls in `bfbeShopQbfbeShopVariations`; Pro.
- `bfbeShopWishlist` **Wishlist**: loop object `post`; set controls in `bfbeShopQbfbeShopWishlist`; Pro.

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
Pro.
The whole group shows only when `query.objectType` is `bfbeShopWishlist`.
- `bfbeShopWishlistActions` (select) **Buttons on each row**: options: `on` On (default), `off` Off; only when `query.objectType` is `bfbeShopWishlist` and `hasLoop` is set
- `bfbeShopWishlistAfterMove` (select) **After Move to cart**: options: `remove` Take it off the list (default), `keep` Keep it on the list; only when `query.objectType` is `bfbeShopWishlist` and `hasLoop` is set and `bfbeShopWishlistActions` is not `off`
- `bfbeShopWishlistMoveText` (text) **Move to cart word**: placeholder Move to cart; only when `query.objectType` is `bfbeShopWishlist` and `hasLoop` is set and `bfbeShopWishlistActions` is not `off`. Add to cart while the row stays on the list.
- `bfbeShopWishlistRemoveText` (text) **Remove word**: placeholder Remove; only when `query.objectType` is `bfbeShopWishlist` and `hasLoop` is set and `bfbeShopWishlistActions` is not `off`
- `bfbeShopWishlistBoughtText` (text) **Mark as bought word**: placeholder Mark as bought; only when `query.objectType` is `bfbeShopWishlist` and `hasLoop` is set
- `bfbeShopWishlistMoveLook` (select) **Move to list: open list**: options: `native` As the browser draws it (default), `custom` Styled with the controls below; only when `query.objectType` is `bfbeShopWishlist` and `hasLoop` is set and `bfbeShopWishlistActions` is not `off`. Phones keep their own list either way.
- `bfbeShopWishlistType` (select) **Post type**: options: `product` Products (default), `post` Posts, `page` Pages, `bfbe_shop_review` Shop Reviews, `bfbe_review` Review, `bfbe_demo` Demos, `bfbe_feature` Feature visuals, `bfbe_fixture` Fixtures, `bfbe_sweep` Sweeps, `bfbe_scratch` Scratch, `bricks_template` My Templates; only when `query.objectType` is `bfbeShopWishlist` and `hasLoop` is set
Styling, in the schema file: `bfbeShopWishlistMoveTypography`, `bfbeShopWishlistMoveBackground`, `bfbeShopWishlistMoveBorder`, `bfbeShopWishlistMovePadding`, `bfbeShopWishlistMoveChevron`, `bfbeShopWishlistMovePanelBg`, `bfbeShopWishlistMovePanelBorder`, `bfbeShopWishlistMovePanelShadow`, `bfbeShopWishlistMovePanelPadding`, `bfbeShopWishlistMoveOptTypography`, `bfbeShopWishlistMoveOptPadding`, `bfbeShopWishlistMoveOptHover`, `bfbeShopWishlistMoveHoverText`, `bfbeShopWishlistMoveOptOnBg`, `bfbeShopWishlistMoveOptOnColor`, `bfbeShopWishlistMoveTick`.

#### BFB Products being compared (`bfbeShopQbfbeShopCompare`)
Pro.
The whole group shows only when `query.objectType` is `bfbeShopCompare`.
- `bfbeShopCompareActions` (select) **Remove on each row**: options: `on` On (default), `off` Off; only when `query.objectType` is `bfbeShopCompare` and `hasLoop` is set
- `bfbeShopCompareRemoveText` (text) **Remove word**: placeholder Remove; only when `query.objectType` is `bfbeShopCompare` and `hasLoop` is set and `bfbeShopCompareActions` is not `off`

#### BFB Quote list (`bfbeShopQbfbeShopQuote`)
Pro.
The whole group shows only when `query.objectType` is `bfbeShopQuote`.
- `bfbeShopQuoteActions` (select) **Quantity and Remove on each row**: options: `on` On (default), `off` Off; only when `query.objectType` is `bfbeShopQuote` and `hasLoop` is set
- `bfbeShopQuoteUpdateText` (text) **Update word**: placeholder Update; only when `query.objectType` is `bfbeShopQuote` and `hasLoop` is set and `bfbeShopQuoteActions` is not `off`
- `bfbeShopQuoteRemoveText` (text) **Remove word**: placeholder Remove; only when `query.objectType` is `bfbeShopQuote` and `hasLoop` is set and `bfbeShopQuoteActions` is not `off`

#### BFB Shop products (`bfbeShopQbfbeShopProducts`)
Pro.
The whole group shows only when `query.objectType` is `bfbeShopProducts`.
- `bfbeShopSet` (select) **Set**: options: `best_sellers` Best sellers (default), `trending` Trending, `top_rated` Top rated, `new` New arrivals, `on_sale` On sale, `price_drops` Price drops, `back_in_stock` Back in stock, `bought` Bought before, `recent` Recently viewed, `hotspots` Pinned on an image; only when `query.objectType` is `bfbeShopProducts` and `hasLoop` is set
- `bfbeShopCount` (number) **Products per page**: placeholder 8; only when `query.objectType` is `bfbeShopProducts` and `hasLoop` is set
- `bfbeShopDays` (number) **Within the last days**: placeholder 30; only when `query.objectType` is `bfbeShopProducts` and `hasLoop` is set and `bfbeShopSet` is `trending` or `new` or `price_drops` or `back_in_stock`. New arrivals: 0 means the newest, however old.
- `bfbeShopMinReviews` (number) **Minimum reviews**: placeholder 1; only when `query.objectType` is `bfbeShopProducts` and `hasLoop` is set and `bfbeShopSet` is `top_rated`
- `bfbeShopHotspots` (text) **Element id**: placeholder abc123; only when `query.objectType` is `bfbeShopProducts` and `hasLoop` is set and `bfbeShopSet` is `hotspots`. Empty: the nearest BFB Image Hotspots.
- `bfbeShopRecentWhile` (select) **While there is nothing yet**: options: `` Nothing (default), `best_sellers` Best sellers, `trending` Trending, `top_rated` Top rated, `new` New arrivals, `on_sale` On sale, `price_drops` Price drops, `back_in_stock` Back in stock; only when `query.objectType` is `bfbeShopProducts` and `hasLoop` is set and `bfbeShopSet` is `recent`
- `bfbeShopSkipCurrent` (checkbox) **Leave out the product on this page**: only when `query.objectType` is `bfbeShopProducts` and `hasLoop` is set

#### BFB Shop variations (`bfbeShopQbfbeShopVariations`)
Pro.
The whole group shows only when `query.objectType` is `bfbeShopVariations`.
- `bfbeShopVariationsProduct` (text) **Product**: placeholder This product; dynamic data accepted; only when `query.objectType` is `bfbeShopVariations` and `hasLoop` is set. An id or SKU; empty means this product.
- `bfbeShopVariationsInStock` (checkbox) **In stock only**: only when `query.objectType` is `bfbeShopVariations` and `hasLoop` is set

#### BFB Shop images (`bfbeShopQbfbeShopImages`)
Pro.
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

_Not written yet._

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
