---
name: bfbe-shop-product-gallery
description: "Use for the shop's settings on Bricks' Product gallery (`product-gallery`): a first image that loads at once, the thumbnails' ratio, space and rings, the product's video as a slide and its 3D view as a slide (BFB Shop product gallery, `shop-product-gallery`). Read before writing these settings."
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

The feature adds no wrapper to Bricks' Product gallery. The BFB Gallery group changes the main image's attributes and writes CSS; the video and 3D groups add one slide each, and its thumbnail, through WooCommerce's own slide filter.

```html
<div class="brxe-product-gallery thumbnail-slider" data-pos="bottom">          <!-- thumbnail-slider: Bricks' Thumbnail slider on -->
  <div class="woocommerce-product-gallery images">
    <div class="woocommerce-product-gallery__wrapper">
      <div class="woocommerce-product-gallery__image"><a><img loading="eager" fetchpriority="high" decoding="async" …></a></div>
      <div class="woocommerce-product-gallery__image bfbe-gvideo" data-bfbe-gvideo="self|youtube|vimeo" data-thumb="…">
        <img class="bfbe-gvideo__lb" data-large_image="…" hidden>   <!-- lightbox stand-in, no src -->
        <div class="bfbe-vp …">… BFB Video Player's own markup …</div>
      </div>
      <div class="woocommerce-product-gallery__image bfbe-g3d" data-bfbe-g3d data-thumb="…">
        <img class="bfbe-g3d__lb" data-large_image="…" hidden>
        <div class="bfbe-3d" data-bfbe-3d="{…}">… BFB 3D View's own markup …</div>
      </div>
    </div>
  </div>
  <div class="brx-product-gallery-thumbnail-slider">
    <div class="woocommerce-product-gallery__image bfbe-gvideo__thumb" data-bfbe-gvideo-thumb><img alt="Video: {product}"><span class="bfbe-gvideo__mark"><svg/></span></div>
    <div class="woocommerce-product-gallery__image bfbe-g3d__thumb" data-bfbe-g3d-thumb><img alt="{product}, 3D view"><span class="bfbe-g3d__mark"><svg/></span></div>
  </div>
</div>
```

- **First image** `bfbeShopFirstImage`, unset or `eager`: the main image alone gets `loading="eager"`, `fetchpriority="high"` and `decoding="async"`; the thumbnails keep what WordPress decides.
- With Bricks' **Thumbnail slider** off, the thumbnails are WooCommerce's `ol.flex-control-thumbs`, built by its script. The scripts then add `bfbe-gvideo__nav` or `bfbe-g3d__nav` to the slide's `li`, and the mark is that item's `::after`.
- `bfbeShopGalleryBorder` writes to `.woocommerce-product-gallery__image img`. The `bfbeShopThumb*` controls write to `.flex-control-thumbs img` and to `.brx-product-gallery-thumbnail-slider .woocommerce-product-gallery__image img` alike. `bfbeShopThumbActiveShadow` writes on `img.flex-active` and `.flex-active-slide img`. `bfbeShopThumbSpace` is a margin on the picture's side of the strip, by `data-pos`.
- The 3D slide's Spin, View in 3D and View in your room buttons sit over the picture's bottom left corner (`.bfbe-g3d .bfbe-3d__bar`, 12px in). `bfbeShop3dBackground` writes to `.bfbe-g3d .bfbe-3d__stage`.
- The marks are 34% of the thumbnail, at most 44px (**3D mark size** and **Play mark size** set width and cap). `bfbeShopVideoPlayed` sets `--bfbe-vp-accent` on `.bfbe-gvideo`, which the player's seek and volume bars read.
- States: the active slide is WooCommerce's `.flex-active-slide`. Leaving the video slide pauses a file and removes a provider's `iframe.bfbe-vp__frame`, so the poster and play button are back on return.

## Wiring to other elements

- **The product carries the media.** The video comes from the product's **BFB Video** panel (meta `_bfbe_video`: a media file or a YouTube or Vimeo address, poster, place, captions); a variation shows its parent's. The 3D slide comes from the product's **3D view** tab (`_bfbe_360_frames`, `_bfbe_ar_glb`, `_bfbe_ar_usdz`). The gallery's groups only show, hide and place them.
- **BFB Video Player** (`bfbe-video-player`) plays the slide; it is built through the player's own class with the essential bar and privacy on. **BFB 3D View** (`bfbe-product-3d`, skill `bfbe-product-3d`) draws the 3D slide the same way.
- **The same media elsewhere.** `{bfbe_product_video}` (`:poster`, `:captions`) puts the video in a BFB Video Player's **Video URL**, Bricks' Video or a link anywhere on the product page; set `bfbeShopVideoShow: "hide"` if the gallery should then stay pictures only. A BFB 3D View placed beside the gallery shows the product as well; set `bfbeShop3dShow: "hide"` to keep one. Tags: skill `bfbe-shop-tags-and-conditions`.
- **The variation's pictures.** WooCommerce swaps the first slide's image for the chosen variation's, so a video or 3D slide asked for first goes second on a variable product.
- **A stack in place of the slider.** A Block looping BFB Shop images (`bfbeShopImages`, skill `bfbe-shop-loops`) with Bricks Images opening one lightbox replaces this element for a column of pictures; video and 3D slides belong to the gallery alone.
- Nothing targets the gallery by class or id. The hub is skill `bfbe-shop`.

## Verified patterns

**Six thumbnails under the picture, ringed when shown** (the demo shop's product template, Fernhouse look, `dev/demo/shop/10-templates.php`). WooCommerce's own strip (`thumbnailSlider: false`) six to a row, cropped square on a paper ground and 22px below the picture; the shown thumbnail gets a 2px ring by `bfbeShopThumbActiveShadow`, so it never shrinks as a border would. `bfbeShopVideoShow: "show"` and `bfbeShop3dBackground` give a product's video and 3D slides their place and ground. The demo's colours are site variables there; plain hex here.

```json
{
  "name": "product-gallery",
  "settings": {
    "thumbnailSlider": false, "columns": 6, "gap": "10px", "thumbnailOpacity": "0.72",
    "thumbnailBorder": { "radius": { "top": "14", "right": "14", "bottom": "14", "left": "14" } },
    "bfbeShopFirstImage": "eager", "bfbeShopVideoShow": "show",
    "bfbeShopGalleryBorder": { "radius": { "top": "20", "right": "20", "bottom": "20", "left": "20" } },
    "bfbeShopThumbSpace": "22px", "bfbeShopThumbRatio": "1 / 1", "bfbeShopThumbBackground": { "hex": "#f3f2ef" },
    "bfbeShopThumbActiveShadow": { "values": { "offsetX": 0, "offsetY": 0, "blur": 0, "spread": 2 }, "color": { "hex": "#101828" } },
    "bfbeShop3dBackground": { "hex": "#f3f2ef" }
  }
}
```

**Bricks' thumbnail slider, left to WordPress** (template `bfbe-shop-product-p3-off`, the P3 fixture). Bricks' slider shows four 90px thumbnails at the bottom; the same `bfbeShopThumb*` controls reach it. `bfbeShopFirstImage: "auto"` leaves the main image's loading to WordPress, for a template whose gallery sits below the fold.

```json
{
  "name": "product-gallery",
  "settings": { "bfbeShopFirstImage": "auto", "thumbnailSlider": true, "thumbnailPosition": "bottom", "itemWidth": 90, "maxItems": 4, "bfbeShopThumbSpace": "20px", "bfbeShopThumbRatio": "1 / 1", "bfbeShopThumbBackground": { "hex": "#eef2f6" } }
}
```

## Gotchas

- **The first image loads at once unless told otherwise.** Unset `bfbeShopFirstImage` reads as `eager`, so every gallery already on a site gets it; only `auto` leaves WordPress' count of images on the page in charge. It never preloads or resizes the picture. <!-- src: plugins/bfb-elements/includes/shop/class-product-page.php:452 ; docs/SHOP-LABELS-2.0.0.md "Product gallery element: group BFB Gallery" -->
- **Each group has its own switch.** BFB Gallery needs **Product page essentials** (`shop-product-page`) on, BFB Gallery video needs **Gallery video** (`shop-gallery-video`), and BFB 3D view appears only while BFB 3D View is on in Bricks' Element Manager. Off, the group and its keys are gone from the panel. <!-- src: plugins/bfb-elements/includes/shop/class-product-page.php:43 ; plugins/bfb-elements-pro/includes/shop/class-gallery-video.php:50 ; plugins/bfb-elements-pro/includes/shop/class-gallery-3d.php:40 -->
- **The video slide needs BFB Video Player.** The slide is the player element built through its class; with the player disabled in Bricks' Element Manager its class never loads and no video slide or thumbnail appears. <!-- src: plugins/bfb-elements-pro/includes/shop/class-gallery-video.php:149 ; plugins/bfb-elements/includes/class-registry.php:351 -->
- **No media on the product, no slide.** The video needs a playable file or a provider address in the product's BFB Video panel; the 3D slide needs at least two frames or a GLB file. Setting the gallery's groups adds nothing on a product without them. <!-- src: plugins/bfb-elements-pro/includes/shop/class-gallery-video.php:106 ; plugins/bfb-elements-pro/includes/shop/class-gallery-3d.php:116 -->
- **First means second on a variable product.** `bfbeShopVideoPlace: "first"` and `bfbeShop3dPlace: "first"` put the slide after the product image there, because WooCommerce's variation script replaces the first slide's picture. <!-- src: plugins/bfb-elements-pro/includes/shop/class-gallery-video.php:280 ; plugins/bfb-elements-pro/includes/shop/class-gallery-3d.php:162 ; docs/elements/shop-gallery-video.md -->
- **Video before 3D when both are last.** With both at Last slide, the video slide comes first, then the 3D view. `bfbeShopVideoPlace` unset (`product`) follows each product's own **Place** field. <!-- src: plugins/bfb-elements-pro/includes/shop/class-gallery-3d.php:175 ; plugins/bfb-elements-pro/includes/shop/class-gallery-video.php:275 -->
- **The 3D slide takes the element's defaults.** It is built with the product and the first frame as its still, nothing else: frames load on the first turn, it never turns on its own, the model waits for a press, and the words are Spin, View in 3D and View in your room. For other settings place a BFB 3D View beside the gallery. <!-- src: plugins/bfb-elements-pro/includes/shop/class-gallery-3d.php:127-145 -->
- **The video slide's player is fixed too.** Essential bar, privacy on (nothing from the provider before play), 16:9 for YouTube or Vimeo and the file's own shape otherwise. The gallery's look reaches it through the marks and **Progress colour** `bfbeShopVideoPlayed` alone. <!-- src: plugins/bfb-elements-pro/includes/shop/class-gallery-video.php:152-158 ; plugins/bfb-elements-pro/includes/shop/class-gallery-video.php:257 -->
- **Icon colour only reaches Bricks' slider.** `bfbeShop3dMarkColor` and `bfbeShopVideoMarkColor` colour the mark's icon in Bricks' thumbnail slider; in WooCommerce's strip the icon is a white background image, and only size and background apply. <!-- src: plugins/bfb-elements-pro/includes/shop/class-gallery-3d.php:105 ; src/elements/shop-gallery-video/shop-gallery-video.css:17 ; src/elements/product-3d/product-3d.css:31 -->
- **Border draws the main picture, not the thumbnails.** `bfbeShopGalleryBorder` rounds `.woocommerce-product-gallery__image img`, and the 3D slide copies that radius to its stage; Bricks' own **Border** `thumbnailBorder` draws the thumbnails. **Ratio** crops each thumbnail with `object-fit: cover`, whatever the photo's shape. <!-- src: plugins/bfb-elements/includes/shop/class-product-page.php:164-200 ; src/elements/product-3d/product-3d.js:119 -->
- **Space from the picture adds to Gap.** Bricks' **Gap** spaces the thumbnails and the picture at once; `bfbeShopThumbSpace` adds a margin on the picture's side only, chosen by **Thumbnail position**. <!-- src: plugins/bfb-elements/includes/shop/class-product-page.php:170-187 -->
- **The player's files load only with a gallery in the template.** They are queued early on a product page whose content template holds a Product gallery and whose product has a video; a video shown only through `{bfbe_product_video}` loads the player as that element does. <!-- src: plugins/bfb-elements-pro/includes/shop/class-gallery-video.php:472 ; docs/elements/shop-gallery-video.md "Cost" -->

## Never do

- Do not set `bfbeShopFirstImage: "auto"` on a gallery at the top of a product page.
- Do not expect `bfbeShopVideoPlace: "first"` or `bfbeShop3dPlace: "first"` to open a variable product's gallery; it opens second there.
- Do not disable BFB Video Player or BFB 3D View in Bricks' Element Manager on a shop that shows their slides.
- Do not set the gallery's video or 3D groups for a product with no video, frames or GLB file and expect a slide.
- Do not style the 3D slide's words or turning through the gallery; place a BFB 3D View and set `bfbeShop3dShow: "hide"`.
- Do not rely on `bfbeShop3dMarkColor` or `bfbeShopVideoMarkColor` with `thumbnailSlider` off; WooCommerce's strip keeps a white icon.
- Do not use Bricks' `thumbnailBorder` for the main picture's corners; use `bfbeShopGalleryBorder`.
