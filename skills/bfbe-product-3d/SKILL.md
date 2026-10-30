---
name: bfbe-product-3d
description: "Use when placing, wiring or styling BFB 3D View (`bfbe-product-3d`). Read before writing its settings."
---

# BFB 3D View (`bfbe-product-3d`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-product-3d.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/product-3d/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 1.05 KB, JS 2.37 KB (gzipped), plus model-viewer 4.4.0 (Apache-2.0, the 3D model, on a press), loaded only on pages that use it.

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### View (`bfbeView`)
- `product` (select) **Product**: placeholder The product of the page
- `image` (image) **Still image**. The product image unless chosen.
- `frames` (select) **Frames from**: options: `product` The product field (default), `here` Images chosen here
- `framesHere` (image-gallery) **Frames**: only when `frames` is `here`
- `load` (select) **Load the frames**: options: `turn` On the first turn (default), `view` Once it comes into view
- `auto` (checkbox) **Turn once in view**. Never under reduced motion.
- `time` (number) **One turn takes (s)**: placeholder 4
- `model` (select) **3D model**: options: `press` On a press (default), `view` Once in view, `off` Off. From the product's GLB file.

### Words (`bfbeWords`)
- `spoken` (text) **Spoken name**: placeholder {product}, 360 degree view
- `spinText` (text) **Spin button**: placeholder Spin
- `modelText` (text) **3D button**: placeholder View in 3D
- `arText` (text) **AR link**: placeholder View in your room

### Look (`bfbeLook`)
- `fit` (select) **Fit**: options: `contain` Contain (default), `cover` Cover; writes CSS
Styling, in the schema file: `ratio`, `stageBackground`, `stageBorder`, `stageShadow`, `stagePadding`, `barAlign`, `barGap`, `buttonGap`, `buttonTypography`, `buttonBackground`, `buttonBorder`, `buttonShadow`, `buttonPadding`, `buttonHoverBackground`, `buttonHoverColor`, `spinPressedBackground`, `spinPressedColor`, `spinPressedBorder`.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<div class="brxe-bfbe-product-3d bfbe-3d is-loading is-model" data-bfbe-3d='{"frames":[…],"load":"turn","auto":false,"time":4,"hint":"…","model":"…glb","when":"press","named":"{product}, 3D model","lib":"…/vendor/model-viewer.min.js"}' data-bfbe-3d-frame="12">
  <div class="bfbe-3d__stage" role="img" aria-label="{product}, 360 degree view" tabindex="0" aria-describedby="{hint id}">
    <img class="bfbe-3d__img" alt="" loading="eager" draggable="false" …>
    <model-viewer class="bfbe-3d__viewer" alt="{product}, 3D model" camera-controls …></model-viewer>  <!-- added on View in 3D -->
  </div>
  <p class="bfbe-sr" id="{hint id}">Drag it, or press the left and right arrow keys, to turn it.</p>
  <div class="bfbe-3d__bar">
    <button type="button" class="bfbe-3d__spin" aria-pressed="false">Spin</button>
    <button type="button" class="bfbe-3d__model" aria-pressed="false">View in 3D</button>
    <a class="bfbe-3d__ar bfbe-3d__ar--quicklook" rel="ar" href="….usdz"><img alt="" width="1" height="1"><span>View in your room</span></a>
    <a class="bfbe-3d__ar bfbe-3d__ar--scene" href="intent://arvr.google.com/scene-viewer/…">View in your room</a>
  </div>
</div>
```

- The server prints the still, the hint and the bar with every button `hidden`; the script unhides Spin when there are frames, View in 3D when there is a model, and each AR link only on a device that opens it. The bar is printed only when there are frames, a USDZ or a GLB.
- With fewer than two frames the stage is named for the product alone and gets no `tabindex`, hint or Spin.
- States: `is-loading` on the root while frames or the model load (a 3px line along the stage's foot), `is-model` while the model shows (the still is hidden, the stage loses `role`, `aria-label`, `tabindex` and `aria-describedby` to the model), `data-bfbe-3d-frame` the frame shown, `aria-pressed="true"` on Spin while it turns and on View in 3D while the model shows.
- Where controls write: `ratio`, `stageBorder`, `stageShadow`, `stagePadding` and `stageBackground` to `.bfbe-3d__stage`; `fit` to `.bfbe-3d__img`; `barGap` sets `--bfbe-3d-gap` (the root's column gap); `barAlign` and `buttonGap` to `.bfbe-3d__bar`; every `button*` control to Spin, View in 3D and the AR links together; `spinPressed*` to `[aria-pressed="true"]` on Spin and View in 3D.
- `window.bfbeProduct3d()` initialises every `.bfbe-3d[data-bfbe-3d]` not yet done.

## Wiring to other elements

- **The product.** `product` empty reads the product of the page, or of the loop item in a product query loop; set it to a product id to show one product anywhere. Frames, GLB and USDZ come from the product's **3D view** tab (`_bfbe_360_frames`, `_bfbe_ar_glb`, `_bfbe_ar_usdz`); a variation uses its parent's.
- **Bricks' Product gallery.** The same view is also a slide of the gallery, through the gallery's **BFB 3D view** group (`bfbeShop3dShow`, `bfbeShop3dPlace`), present while this element is on in Bricks' Element Manager. Skill `bfbe-shop-product-gallery`. Hide one of the two when both would show the same product.
- **BFB Motion Switch** (`bfbe-motion-switch`). Its pause puts `bfbe-motion-off` on `<html>`; **Turn once in view** `auto` does not start, and a turn under way stops, while it is there. The model's moving hand prompt is left out too.
- Nothing targets it by class or id. The hub is skill `bfbe-shop`.

## Verified patterns

The product ids are the fixture site's (`80218` the Ceramic Pitcher, with 36 frames, a GLB and a USDZ). Use a product of the target site, or leave `product` out on a product template.

**A product that turns, with its 3D model behind a press** (fixture page `fixture-shop-3d`, `.p5b-3d-pitcher`). Frames from the product field load on the first drag, arrow key or Spin; **One turn takes (s)** `time: 3` sets Spin's pace; `model` unset is On a press, so View in 3D shows because the product has a GLB.

```json
{ "name": "bfbe-product-3d", "settings": { "product": "80218", "time": 3, "_cssClasses": "p5b-3d-pitcher" } }
```

**A spin at the top of a page that turns once by itself** (fixture page `fixture-shop-3d-auto`, `.p5b-3d-auto`). `load: "view"` fetches the frames once the element is in view, `auto` turns it once round in 2 s there, and `model: "off"` keeps the 3D model off the page while Android's View in your room still opens the GLB.

```json
{ "name": "bfbe-product-3d", "settings": { "product": "80218", "auto": true, "load": "view", "time": 2, "model": "off", "_cssClasses": "p5b-3d-auto" } }
```

## Gotchas

- **Two frames or it is a picture.** With fewer than two frames the element is a still image named for the product: no focus, no hint, no Spin. With no frames and no AR file the script is not loaded at all. <!-- src: plugins/bfb-elements-pro/elements/product-3d.php:398 ; plugins/bfb-elements-pro/elements/product-3d.php:420 ; docs/elements/product-3d.md "Limits" -->
- **Nothing to show, nothing on the page.** Without a product image, a frame or **Still image** `image`, the page gets nothing and the canvas shows "Choose a product with an image, or a still image." Outside a product page or loop, set `product`. <!-- src: plugins/bfb-elements-pro/elements/product-3d.php:412-414 -->
- **Frames come in a set, in turning order.** The field reads at most 72 image ids; **Choose the frames** orders them by file name. 24 to 36 frames at even steps turn smoothly, and each is fetched at the single-product image size, so a large set costs its full weight on the first turn. `framesHere` is read only with `frames: "here"`. <!-- src: plugins/bfb-elements-pro/includes/shop/class-product-3d.php:29 ; plugins/bfb-elements-pro/includes/shop/class-product-3d.php:76-90 ; docs/elements/product-3d.md "The product fields" -->
- **View in 3D needs the product's GLB.** The button exists only when the product has a GLB file and `model` is not `off`; with `off` the GLB still opens in Scene Viewer on Android. A model that cannot be fetched, or a browser without WebGL, takes the button away and keeps the still. <!-- src: plugins/bfb-elements-pro/elements/product-3d.php:429 ; src/elements/product-3d/product-3d.js:76 ; dev/shop/p5b-probe.mjs "a GLB that cannot be fetched" -->
- **The 3D library is heavy and late.** model-viewer, 284 KB gzipped, is fetched from the plugin on the first press of View in 3D, or once in view with `model: "view"`; `view` replaces the still with the model the first time the element is on screen. <!-- src: docs/elements/product-3d.md "Cost" ; src/elements/product-3d/product-3d.js:39 ; src/elements/product-3d/product-3d.js:112 -->
- **Turn once in view is never forced.** `auto` does nothing under reduced motion or while BFB Motion Switch has paused the page, and stops a turn under way when either comes on; a press of Spin still turns it. <!-- src: src/elements/product-3d/product-3d.js:27 ; src/elements/product-3d/product-3d.js:191-193 ; src/elements/product-3d/product-3d.js:229 ; dev/shop/p5b-probe.mjs "Motion Switch" -->
- **View in your room shows only where it opens.** The Quick Look link (USDZ) shows where the browser supports `rel="ar"`, the Scene Viewer link (GLB) on Android without it; on a computer neither shows. The canvas shows every button and link, unhidden, with the script idle. <!-- src: src/elements/product-3d/product-3d.js:144 ; plugins/bfb-elements-pro/elements/product-3d.php:465-478 -->
- **One turn takes is held between 1 and 30 seconds.** `time` outside that range is clamped; empty, 4. It paces Spin and the auto turn; a drag across the stage's width turns it once round whatever `time` says. <!-- src: plugins/bfb-elements-pro/elements/product-3d.php:440 ; src/elements/product-3d/product-3d.js:222 -->
- **`{product}` is the only placeholder in Spoken name.** It is replaced with the product's name; with fewer than two frames `spoken` is ignored and the name alone is spoken. <!-- src: plugins/bfb-elements-pro/elements/product-3d.php:419-423 -->
- **Padding frames the picture, not the model.** `stagePadding` leaves room round the still inside its frame; the 3D model lies over the whole stage. **Aspect ratio** `ratio` empty keeps the image's own shape. <!-- src: src/elements/product-3d/product-3d.css:16 ; docs/elements/product-3d.md "Look" -->
- **Model files are checked at upload.** USDZ and GLB upload for administrators only, and only when the first bytes match the type; an address typed into the field is used as it is. <!-- src: plugins/bfb-elements-pro/includes/shop/class-product-3d.php:198-247 ; docs/elements/product-3d.md "The product fields" -->

## Never do

- Do not place it outside a product page or product loop without `product`.
- Do not give it a single frame and expect it to turn; give two or more, ideally 24 to 36.
- Do not set `framesHere` without `frames: "here"`.
- Do not set `model: "view"` on a page where several 3D views are in view at once; each fetches its GLB on sight.
- Do not show this element and the gallery's 3D slide for the same product on one page; set `bfbeShop3dShow: "hide"` on the gallery or remove this one.
- Do not judge the AR links or the turning from the builder canvas; check them on the page.
- Do not count on `spoken` for a product with fewer than two frames; the product's name is spoken there.
