---
name: bfbe-image-focal-point
description: "Use when placing, wiring or styling BFB Image focal point (`image-focal-point`): a feature of the free plugin, not an element of its own: a Focal point field in an image's details in the media library, where you drag a dot onto the subject or type two numbers, with previews of a wide, a square and a tall crop. Read before writing its settings."
---

# BFB Image focal point (`image-focal-point`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 1.1.0 or later. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/image-focal-point.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/image-focal-point/

## What it is
A feature of the free plugin, not an element of its own: a Focal point field in an image's details in the media library, where you drag a dot onto the subject or type two numbers, with previews of a wide, a square and a tall crop. Bricks then keeps that point in frame wherever it crops the image: the Image element, a featured image in a query loop, and an element's own background image, dynamic ones included. An element's own position for its pictures, such as an Image's Object position or BFB Devices' Media position, wins, and so does an element's own Background position, and the point adds no file to the page.

**Not for:** Not for cropping or resizing the image file: WordPress's sizes stay as they are, and the point decides which part shows where Bricks crops the image on the page. A background that switches to another image at a breakpoint is left as it is, and so is an image that another plugin's own code prints without WordPress. Slider slides and the Carousel's background mode are not covered.

**Nestable:** no · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** no

## Where it lives
A feature, not an element: its controls are added to images in the media library: Bricks' Image element, featured images in query loops, background images.

## Settings that decide the build

## What it guarantees for accessibility (do not undo)
- The dot is a slider named Focal point that takes keyboard focus, and its value is read as the two percentages.
- With the dot focused, the arrow keys move it one step, Shift with an arrow moves it ten, and Home puts it back in the centre.
- Across and Down are labelled number fields, so the point can be typed instead of dragged.
- The three crop previews are aria-hidden, since the numbers say the same thing.
- On the page the point moves the picture inside its frame; the markup and the alt text stay as they are.
<!-- bfbe:generated:end -->

## Rendered DOM

The feature adds no element, wrapper, class, attribute, stylesheet or script to the page. It writes one CSS property into a `style` attribute Bricks or WordPress is already printing, after any style already there.

```html
<img width="1024" height="576" src="..." class="brxe-image css-filter size-large" alt="..." id="brxe-4359fb" loading="lazy" style="object-position:83% 50%" />

<figure id="brxe-a1b2c3" class="brxe-image tag caption">
  <a class="tag" href="#"><img width="1024" height="576" src="..." class="css-filter size-large" alt="..." style="object-position:83% 50%" /></a>
  <figcaption class="bricks-image-caption">...</figcaption>
</figure>

<div id="brxe-d4e5f6" class="brxe-block" style="background-position:83% 50%">...</div>
```

- **On an image**: `object-position` on the `<img>` WordPress prints for an attachment (`wp_get_attachment_image()`). A Bricks `image` with no link, caption or HTML tag prints that `<img>` as its root; with a link or caption the `<img>` sits inside and still carries the style.
- **On a background**: `background-position` on the element's root, where Bricks prints the root's attributes. Nothing is written on a child, a pseudo-element or in Bricks' generated CSS.
- **The value** is the point in percent from the left and top edges, with at most one decimal and no trailing zero: `83% 50%`, `12.5% 80%`.
- **An image with no point** gets nothing. Centre in the media library deletes the point, so the centre writes nothing either.
- **In the media library** the field is `.bfbe-focal` (marked `data-bfbe-focal`): the image in `.bfbe-focal__stage` with the dot `.bfbe-focal__dot` (`role="slider"`, `aria-label="Focal point"`, `aria-valuemin="0"`, `aria-valuemax="100"`, `aria-valuenow="83"`, `aria-valuetext="83% across, 50% down"`, and `data-bfbe-words`, the translated words its script fills in), the two number inputs `attachments[<id>][bfbe_focal_x]` and `[bfbe_focal_y]` (0 to 100, step 0.1), the Centre button `[data-bfbe-focal-centre]`, and three `aria-hidden` previews. Its script and stylesheet (handle `bfbe-focal-point`) load wherever WordPress's media window can open, the builder included, and on an image's own edit screen. Never on the page.

## Wiring to other elements

- **There is no element setting.** The point belongs to the image, in its attachment meta `_bfbe_focal_point`, stored as `"x y"` in percent (`"83 50"`). Every element that shows that image cropped picks it up; nothing is written on the element.
- **How an agent sets it.** BFB Elements registers no ability, no REST route and no element control for the point, and the meta key starts with an underscore and is not registered, so WordPress's REST API does not write it either. Ask the user to set it in the media library (open the image, drag the dot or type Across and Down, then the media window saves; on the image's edit screen, press Update). Where the agent can run code on the site (WP-CLI, or Bricks 2.4's `bricks/execute-php` ability where the site has switched it on), write the meta itself: `wp post meta update 14145 _bfbe_focal_point "83 50"`, or `update_post_meta( 14145, '_bfbe_focal_point', '83 50' )`, with the target site's own attachment id.
- **Bricks' Image (`image`).** Set **Object fit** to Cover (`_objectFit: "cover"`) and give the frame a shape (`_height`, `_aspectRatio`), and leave **Object position** (`_objectPosition`) out.
- **Any element's background.** A section, container, block or div with `_background.image` and `size: "cover"` takes the point when the background has no `position`, at any breakpoint or on any of its global classes.
- **Query loops.** `{featured_image}` as an Image's `image.useDynamicData` or as a background's `_background.image.useDynamicData` takes each post's own image, and with it that image's own point. Posts whose images have no point stay centred.
- **Other elements that print an attachment image through WordPress** carry the point too, because the style is added to every attachment `<img>` WordPress prints: Bricks' Image Gallery and Posts, and BFB Elements' Before / After, Price List, Blockquote's photo and Devices among them. It shows where their CSS crops the image with `cover`. Since BFB Elements 1.1.2, one that sets its own position for its pictures keeps it (see the Gotchas).
- **Not reached.** Images inside post content or a Rich Text element (WordPress filters that HTML, it does not print it through `wp_get_attachment_image()`), the background images of a Slider's slides or of a Carousel set to background images (not the element's root), images given by URL with no media id, and any image another plugin prints in its own markup.
- **Switched off**, under BFB Elements, Elements, Features (Image focal point), the field leaves the media library and nothing is written on the page. The points stay saved on the images and work again when it is back on. Deleting the plugin deletes every point.

## Verified patterns

The images carry the demo site's media id (14145, the photograph whose point is `"83 50"`, the eye at its right edge) and `https://example.com/...` addresses in place of its own. Use the target site's own media id, `filename`, `url` and `full`, and set the point on that image as above: the trees carry no trace of it.

**Three crops that keep the point.** From the Image focal point demo (`demo-bfb-image-focal-point`), the row "With its focal point": the same three Images with no position of their own, wide, square and tall. Each renders `style="object-position:83% 50%"` on its `<img>`. The demo writes `_objectPosition: ""`; leaving the key out is the same. Trimmed: the corner radius, the labels under each Image and the demo's colours.

```json
{
  "name": "block",
  "settings": { "_direction": "row", "_columnGap": "24px", "_alignItems": "flex-start", "_flexWrap": "nowrap" },
  "children": [
    { "name": "image", "settings": { "image": { "id": 14145, "filename": "bfbe-demo-kestrel-cover-fitting.jpg", "size": "large", "url": "https://example.com/wp-content/uploads/bfbe-demo-kestrel-cover-fitting-1024x576.jpg", "full": "https://example.com/wp-content/uploads/bfbe-demo-kestrel-cover-fitting.jpg" }, "_objectFit": "cover", "_aspectRatio": "16/9", "_height": "180px", "_width": "auto" } },
    { "name": "image", "settings": { "image": { "id": 14145, "filename": "bfbe-demo-kestrel-cover-fitting.jpg", "size": "large", "url": "https://example.com/wp-content/uploads/bfbe-demo-kestrel-cover-fitting-1024x576.jpg", "full": "https://example.com/wp-content/uploads/bfbe-demo-kestrel-cover-fitting.jpg" }, "_objectFit": "cover", "_aspectRatio": "1/1", "_height": "180px", "_width": "auto" } },
    { "name": "image", "settings": { "image": { "id": 14145, "filename": "bfbe-demo-kestrel-cover-fitting.jpg", "size": "large", "url": "https://example.com/wp-content/uploads/bfbe-demo-kestrel-cover-fitting-1024x576.jpg", "full": "https://example.com/wp-content/uploads/bfbe-demo-kestrel-cover-fitting.jpg" }, "_objectFit": "cover", "_aspectRatio": "3/4", "_height": "180px", "_width": "auto" } }
  ]
}
```

**The same Image with its own Object position: the point is ignored.** From the same demo, the row "Centred", tall 3:4. `_objectPosition` set to anything, here Bricks' centre, wins over the point: nothing is written on the `<img>` and the eye falls out of the tall crop. Set it this way when an Image must ignore the point.

```json
{
  "name": "image",
  "settings": { "image": { "id": 14145, "filename": "bfbe-demo-kestrel-cover-fitting.jpg", "size": "large", "url": "https://example.com/wp-content/uploads/bfbe-demo-kestrel-cover-fitting-1024x576.jpg", "full": "https://example.com/wp-content/uploads/bfbe-demo-kestrel-cover-fitting.jpg" }, "_objectFit": "cover", "_aspectRatio": "3/4", "_height": "180px", "_width": "auto", "_objectPosition": "center center" }
}
```

**A tall block with the photograph as its background.** From the feature page "Background images too" (`dev/demo/feature-pages/bfb-image-focal-point.php`), the "Frames" panel. The background has an image and `size: "cover"` and no `position`, so the root renders `style="background-position:83% 50%"`. Trimmed: the corner radius, `_overflow` and the label's colours.

```json
{
  "name": "block",
  "settings": {
    "_background": { "image": { "id": 14145, "filename": "bfbe-demo-kestrel-cover-fitting.jpg", "size": "full", "url": "https://example.com/wp-content/uploads/bfbe-demo-kestrel-cover-fitting.jpg", "full": "https://example.com/wp-content/uploads/bfbe-demo-kestrel-cover-fitting.jpg" }, "size": "cover" },
    "_width": "220px",
    "_height": "480px",
    "_justifyContent": "flex-end",
    "_alignItems": "flex-start",
    "_padding": { "top": "16", "right": "16", "bottom": "16", "left": "16" }
  },
  "children": [
    {
      "name": "block",
      "settings": { "_background": { "color": { "hex": "#ffffff" } }, "_padding": { "top": "10", "right": "14", "bottom": "10", "left": "14" }, "_rowGap": "2px", "_width": "auto" },
      "children": [
        { "name": "text-basic", "settings": { "text": "Frames", "tag": "p" } },
        { "name": "text-basic", "settings": { "text": "Fitted in the shop.", "tag": "p" } }
      ]
    }
  ]
}
```

**Post cards in a query loop, each keeping its own image's point.** From the focal point probe (`dev/focal-point-probe.mjs`), the block `fp-loop`: a Block repeated over posts, its background and an Image inside both `{featured_image}`. The probe read `20% 30%` on both for each post. Changed: the probe's fixed `post__in` list is a `posts_per_page` here, and the query names its `objectType`.

```json
{
  "name": "block",
  "settings": {
    "hasLoop": true,
    "query": { "objectType": "post", "post_type": ["post"], "posts_per_page": "3" },
    "_background": { "image": { "useDynamicData": "{featured_image}", "size": "full" }, "size": "cover" },
    "_height": "200px",
    "_width": "100%"
  },
  "children": [
    { "name": "image", "settings": { "image": { "useDynamicData": "{featured_image}", "size": "large" }, "_objectFit": "cover", "_height": "120px", "_width": "100%" } }
  ]
}
```

## Gotchas

- **An uncropped image shows nothing.** `object-position` moves a picture inside its box, so a Bricks `image` left at the default fit, or with no height or aspect ratio, is never cropped and the point has no visible effect. <!-- src: plugins/bfb-elements/includes/class-focal-point.php:196-197 --> <!-- src: docs/elements/focal-point.md "Where it applies" -->
- **Contain moves the picture too.** With Object fit Contain, Scale down or None, or a background `size` other than `cover`, the point still applies and pushes the picture towards its side of the frame: a point at `83 50` sits a letterboxed image against the right edge. <!-- src: plugins/bfb-elements/includes/class-focal-point.php:201-215, 227-239 -->
- **Any own position wins, at any breakpoint.** A value in any of the element's settings that writes `object-position` (an Image's `_objectPosition`, BFB Devices' `mediaPosition`, read from the element's own controls; before BFB Elements 1.1.2, only the Image's), or a `position` inside `_background` on an element, set on the element or on one of its `_cssGlobalClasses`, at the base or at any breakpoint (`_objectPosition:mobile_portrait`), turns the point off for that element at every width. The images it prints while it renders follow it, the innermost element first. <!-- src: plugins/bfb-elements/includes/class-focal-point.php:228, 248, 272, 330 --> <!-- src: dev/focal-point-probe.mjs (fp-own, fp-class, fp-bgown) ; dev/fixes-1.1.2-probe.mjs (Devices left top kept 0% 0%, Devices unset took 83% 50%) -->
- **Habitual centre values cancel it.** `_objectPosition: "center center"` or a background `position: "center center"`, written out of habit, count as the element's own choice. The demo's "Centred" row is built exactly that way to show the eye falling out of frame. <!-- src: plugins/bfb-elements/includes/class-focal-point.php:260-278 --> <!-- src: dev/demo/sections/kestrel.php:499 -->
- **A position set for :hover does not count, and loses.** `_objectPosition:hover` and a `position` in `_background:hover` are skipped when the point looks for the element's own choice, and the point's inline style outranks Bricks' `:hover` rule, so that hover position never shows. <!-- src: plugins/bfb-elements/includes/class-focal-point.php:230, 268 -->
- **Positions written anywhere else lose.** The check reads Bricks settings on the element and its global classes. An `object-position` or `background-position` in custom CSS, a plain class or a theme style is beaten by the inline style unless it carries `!important`. <!-- src: plugins/bfb-elements/includes/class-focal-point.php:272, 330 -->
- **A background that changes image is left alone.** When `_background` and its breakpoint keys name more than one image, there is no single point and nothing is written, even at the widths that show the image with a point. The same image at every breakpoint still takes it. <!-- src: plugins/bfb-elements/includes/class-focal-point.php:221-239 --> <!-- src: dev/focal-point-probe.mjs (fp-bgbp) -->
- **Before / After pairs can drift apart.** Both images are cropped with `cover` and each takes its own point, so a before image with a point and an after image without one (or with another) no longer line up under the divider. Give both the same point, or neither (rendered 2026-10-13). <!-- src: plugins/bfb-elements/elements/before-after.php:478-497 --> <!-- src: src/elements/before-after/before-after.css:58-65 -->
- **The meta format is strict.** `get()` reads two numbers with at most one decimal, separated by one space. `"83% 50%"`, `"83,50"` or `"83.25 50"` are ignored as no point; values above 100 are read as 100. The media field deletes the meta at the centre, but `"50 50"` written by code is kept and written to the page as `50% 50%`. <!-- src: plugins/bfb-elements/includes/class-focal-point.php:58-65, 139-146 -->
- **It never touches the file.** WordPress's image sizes stay as they were generated; the point decides which part of each one shows where it is cropped on the page. Changing the point needs no regeneration and no page save. <!-- src: plugins/bfb-elements/includes/class-focal-point.php:14-16, 201-215 --> <!-- src: docs/RELEASE-BRIEF-1.1.0.md "Not claimed" -->
- **The point travels with the image, not the page.** A template or a page copied to another site brings its Images and backgrounds without the points, which live in that site's media library. The demo is a page, not a library template, for this reason. <!-- src: dev/demo/sections/kestrel.php:486-487 -->
- **The media window saves on change.** A drag saves when the dot is released, and each arrow key press saves at once, through the media window's own save. On the image's edit screen nothing is saved until Update is pressed. Saving needs a user who can edit that attachment. <!-- src: plugins/bfb-elements/assets/admin/focal-point.js:37-47, 75-86, 88-102 --> <!-- src: plugins/bfb-elements/includes/class-focal-point.php:135 --> <!-- src: dev/demo/feature-pages/bfb-image-focal-point.php:8-9 -->

## Never do

- Do not look for a focal point control on an element or in a schema; there is none. Set the point on the image.
- Do not set `_objectPosition` on a Bricks `image`, or `position` inside `_background`, at any breakpoint or on a global class, when the image's point should apply.
- Do not write `"center center"` positions by habit on cropped images or backgrounds.
- Do not write the meta as anything but `"x y"`: two numbers from 0 to 100, at most one decimal, one space.
- Do not use a different background image at a breakpoint and expect the point to apply.
- Do not set a point on one image of a Before / After pair and not the other.
- Do not override the point with custom CSS `!important`; give the element its own Object position or Background position instead.
- Do not tell the user the point crops, resizes or regenerates the image files.
