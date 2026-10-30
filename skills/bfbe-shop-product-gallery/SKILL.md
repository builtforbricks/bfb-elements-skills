---
name: bfbe-shop-product-gallery
description: "Use for the shop's settings on Bricks' Product gallery: the gallery's layout and first image, the 3D view, and video in the gallery (BFB Shop product gallery, `shop-product-gallery`). Read before writing these settings."
---

# BFB Shop product gallery (`shop-product-gallery`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 2.0.0 or later, and BFB Elements Pro 2.0.0 or later for the groups marked Pro, WooCommerce active, the feature switches on (WordPress menu BFB Elements, Elements): `shop-product-page`, `shop-gallery-video`. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/shop-product-gallery.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/shop-product-gallery/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

## Where it lives
A feature, not an element: its groups are added to Bricks' own elements, on the Content tab after Bricks' own groups. By element:
- Product gallery (`product-gallery`): BFB Gallery (`bfbeShopGallery`), BFB 3D view (`bfbeShop3d`), BFB Gallery video (`bfbeShopGalleryVideo`).

## Settings that decide the build

### Product gallery (`product-gallery`)

#### BFB Gallery (`bfbeShopGallery`)
Free, switch `shop-product-page`.
- `bfbeShopFirstImage` (select) **First image**: options: `eager` Loads at once (default), `auto` As WordPress decides
Styling, in the schema file: `bfbeShopGalleryBorder`, `bfbeShopThumbSpace`, `bfbeShopThumbRatio`, `bfbeShopThumbBackground`, `bfbeShopThumbShadow`, `bfbeShopThumbActiveShadow`.

#### BFB 3D view (`bfbeShop3d`)
Pro.
- `bfbeShop3dShow` (select) **3D view**: options: `show` Shown (default), `hide` Hidden. A slide for a product with 360 degree frames or a GLB.
- `bfbeShop3dPlace` (select) **Position**: options: `first` First slide, `last` Last slide (default); only when `bfbeShop3dShow` is not `hide`
Styling, in the schema file: `bfbeShop3dBackground`, `bfbeShop3dMarkSize`, `bfbeShop3dMarkBackground`, `bfbeShop3dMarkColor`.

#### BFB Gallery video (`bfbeShopGalleryVideo`)
Pro, switch `shop-gallery-video`.
- `bfbeShopVideoShow` (select) **Video**: options: `show` Shown (default), `hide` Hidden
- `bfbeShopVideoPlace` (select) **Position**: options: `product` As the product says (default), `first` First slide, `last` Last slide; only when `bfbeShopVideoShow` is not `hide`
Styling, in the schema file: `bfbeShopVideoMarkSize`, `bfbeShopVideoMarkBackground`, `bfbeShopVideoMarkColor`, `bfbeShopVideoPlayed`.
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
