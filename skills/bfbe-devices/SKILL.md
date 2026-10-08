---
name: bfbe-devices
description: "Use when placing, wiring or styling BFB Devices (`bfbe-devices`): a phone, tablet, laptop or browser window mockup drawn in CSS around live nested elements, a screenshot or a looping app clip. Read before writing its settings."
---

# BFB Devices (`bfbe-devices`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-devices.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/devices/

## What it is
A phone, tablet, laptop or browser window drawn in CSS around live nested elements, an image or a video. The frames are generic shapes with no image files, and the bezel and corner radius scale with the width. Media can fill the screen with cropping or fit inside it, and an autoplaying clip with Player controls off pauses on a click.

**Not for:** The frames are generic shapes, not a specific manufacturer's device, and each screen keeps fixed proportions, so media of another shape is cropped or fitted. A mockup that must match one exact model fits a framed image of that model better.

**Costs a page:** CSS 1.38 KB, JS 0.63 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** yes · **In a query loop:** no · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** no

## Structure
Nestable: any Bricks element goes inside (blocks, headings, text, images, a form).
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-devices",
    "settings": {},
    "children": [
        {
            "name": "heading",
            "settings": {
                "text": "Live content",
                "tag": "h4"
            }
        },
        {
            "name": "text-basic",
            "settings": {
                "text": "Anything you nest here shows on the screen."
            }
        }
    ]
}
```

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Device (`bfbeDevice`)
- `device` (select) **Device**: options: `phone` Phone (default), `tablet` Tablet, `laptop` Laptop, `browser` Browser window. Choose Phone, the default, Tablet, Laptop or Browser window. All four are generic shapes drawn in CSS, without image files.
- `orientation` (select) **Orientation**: options: `portrait` Portrait (default), `landscape` Landscape; only when `device` is not `laptop` or `browser`. Choose Portrait or Landscape for the Phone and Tablet. The Laptop and Browser window keep their own wide proportions.
- `address` (text) **Address bar text**: placeholder example.com; dynamic data accepted; only when `device` is `browser`. The address shown in the Browser window frame, example.com unless set. It takes dynamic data.
Styling, in the schema file: `width`, `chromeBackground`, `addressTypography`.

### Screen (`bfbeScreen`)
- `content` (select) **On the screen**: options: `nested` Nested elements (default), `image` An image, `video` A video. Choose Nested elements, the default, for live content. An image and A video put media on the screen instead.
- `image` (image) **Image**: only when `content` is `image`. With An image, the picture on the screen. In the canvas, a note gives the screen's proportions, and how much a crop cuts when it is a tenth or more.
- `videoFile` (video) **Video file**: only when `content` is `video`. With A video, a file from the media library. It wins over the address below.
- `video` (text) **Or a video URL**: placeholder https://example.com/demo.mp4; dynamic data accepted; only when `content` is `video`. The video's address when no file is chosen. It takes dynamic data.
- `videoAutoplay` (checkbox) **Autoplay**: only when `content` is `video`. Plays the video muted and looping from page load. With Player controls off, a click or tap on the screen plays and pauses it.
- `videoControls` (checkbox) **Player controls**: only when `content` is `video`. Tick it to show the browser's video controls on a clip that autoplays. A clip without Autoplay always shows them.
- `mediaFit` (select) **Media fit**: options: `cover` Fill the screen, cropping (default), `contain` Fit inside the screen; writes CSS; only when `content` is not `` or `nested`. Fill the screen, cropping is the default. Fit inside the screen shows the whole picture or video.
- `mediaPosition` (select) **Media position**: options: `left top` Top left, `center top` Top, `right top` Top right, `left center` Left, `center center` Middle (default), `right center` Right, `left bottom` Bottom left, `center bottom` Bottom, `right bottom` Bottom right; writes CSS; only when `content` is not `` or `nested`. Which part stays in view when the media is cropped, or where fitted media sits. There are nine places, Middle by default.
- `scrollable` (checkbox) **Scrollable screen**: only when `content` is not `image` or `video`. For nested elements, and off by default. Tick it to let the screen scroll. It then takes keyboard focus, so a keyboard can scroll it.
Styling, in the schema file: `screenBackground`, `screenPadding`.

### Frame (`bfbeFrame`)
- `camera` (checkbox) **Camera cutout**: only when `device` is not `laptop` or `browser`. Off by default. Tick it to give a Phone or Tablet a camera cutout at the top of the screen.
- `buttons` (checkbox) **Side buttons**: only when `device` is `` or `phone`. Off by default. Tick it to give a Phone a volume pair on one edge and a power button on the other, colored by Side button colour.
Styling, in the schema file: `frameColor`, `bezel`, `radius`, `frameBorder`, `buttonColor`, `shadow`, `chromePadding`, `chromeDots`, `addressPadding`, `addressBorder`, `baseColor`.

## What it guarantees for accessibility (do not undo)
- The side buttons, laptop base and browser window bar, with its address text, are hidden from assistive technology.
- Nested elements stay live content in the page, and a Scrollable screen is given tabindex 0 so a keyboard can reach and scroll it.
- With Autoplay on and Player controls off, a keyboard button named Pause the video or Play the video toggles the clip.
- That button stays out of sight until it has focus or the clip is paused.
- With Autoplay on and Player controls off, reduced motion turns autoplay off and pauses the clip, removes the pause button and restores the browser's controls.
- With Player controls on, the clip is a standard video element, so the browser's controls can pause it, and under reduced motion it does not play by itself.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<div class="brxe-bfbe-devices bfbe-dev bfbe-dev--phone bfbe-dev--c-nested bfbe-dev--portrait bfbe-dev--camera bfbe-dev--scroll">
  <div class="bfbe-dev__frame">
    <div class="bfbe-dev__chrome" aria-hidden="true">                       <!-- browser -->
      <span class="bfbe-dev__dots"><i></i><i></i><i></i></span><span class="bfbe-dev__address">example.com</span>
    </div>
    <span class="bfbe-dev__btn bfbe-dev__btn--vol-a" aria-hidden="true"></span> <!-- phone with buttons: vol-a, vol-b, power -->
    <div class="bfbe-dev__screen">
      <div class="bfbe-dev__content" tabindex="0">...nested elements...</div>
      <!-- or <img class="bfbe-dev__media"> or <video class="bfbe-dev__media"> + <button class="bfbe-dev__pause"> -->
    </div>
    <div class="bfbe-dev__base" aria-hidden="true"></div>                   <!-- laptop -->
  </div>
</div>
```

- Root classes: `bfbe-dev--{device}` and `bfbe-dev--c-{content}` always; `bfbe-dev--portrait` or `--landscape` and `bfbe-dev--camera` on a phone or tablet; `bfbe-dev--scroll` for a scrollable nested screen; `bfbe-dev--tap` when a resolved clip autoplays with Player controls off.
- `.bfbe-dev` is a flex row with `justify-content: center` and `align-self: stretch`, so the frame sits centred in the width it gets. `_cssClasses` and Bricks' universals land here, and so do the custom properties: **Width** `width` writes `--bfbe-dev-w`, **Frame colour** `frameColor` `--bfbe-dev-frame`, **Bezel** `bezel` `--bfbe-dev-bezel`, **Corner radius** `radius` `--bfbe-dev-radius`, **Side button colour** `buttonColor` `--bfbe-dev-button`.
- `.bfbe-dev__frame` is the body, `min(width, 100%)` wide. **Frame border** `frameBorder` and **Shadow** `shadow` write to it.
- `.bfbe-dev__screen` holds the device's aspect ratio with `overflow: hidden`. **Screen background** `screenBackground` writes here; **Screen padding** `screenPadding` writes here in nested mode. Unset, it paints the system colours `Canvas` and `CanvasText`.
- `.bfbe-dev__content` wraps the children, padded by `--bfbe-gap` (16px) plus the cutout's height under a camera. With **Scrollable screen** on, it is the scroller and carries `tabindex="0"`.
- `.bfbe-dev__media` is the `<img>` (`loading="lazy"`) or the `<video>` (`playsinline preload="metadata"`, plus `autoplay muted loop` with Autoplay, plus `controls` unless the screen is the switch). **Media fit** `mediaFit` and **Media position** `mediaPosition` write its `object-fit` and `object-position`.
- Browser window parts: `chromeBackground` and `chromePadding` write to `.bfbe-dev__chrome` (the whole bar); `chromeDots` to `.bfbe-dev__dots i`; `addressTypography`, `addressPadding` and `addressBorder` to `.bfbe-dev__address`. Laptop: `baseColor` writes to `.bfbe-dev__base`.
- The camera cutout is `.bfbe-dev__screen::before`, not an element.
- States: the script sets `is-paused` on the root while the clip is paused and swaps the button's text between its `data-bfbe-pause` and `data-bfbe-play` values. Under reduced motion it removes `bfbe-dev--tap` and the button and turns `controls` on.
- `p.bfbe-notice`, above the frame, is drawn in the canvas and never on the page.

## Wiring to other elements

Stands alone; nothing targets it and it targets nothing. The play switch is internal: no other element starts or pauses the clip.

- **Nested content.** In nested mode Bricks renders the children as it would anywhere, inside `.bfbe-dev__content`; the screen clips whatever overflows it.
- **Targeting.** Give the device a class in `_cssClasses` and select `.that-class .bfbe-dev__screen` or `.that-class .bfbe-dev__content`. Never use `_cssId`: component instances share ids.
- **Dynamic data.** `address` and `video` take dynamic tags; a tag in `video` resolves a file field, an attachment id or a plain address. `image` takes the image control's own dynamic data.
- **AJAX content.** The script scans again after Bricks' AJAX pagination, page loads, query results and popups. For markup added any other way, call `window.bfbeDevices()`.

## Verified patterns

**A looping app clip in a phone.** From the Devices demo (`demo-bfb-devices`), with the address made generic and a stray `shadow: true` left out. Autoplay with `videoControls` unset makes the screen the play switch. The demo's clip is 720 x 1560, the phone screen's own 9 : 19.5, so nothing is cropped.

```json
{
  "name": "bfbe-devices",
  "settings": {
    "device": "phone",
    "content": "video",
    "video": "https://example.com/wp-content/uploads/app-scroll.mp4",
    "videoAutoplay": true,
    "width": "300px",
    "camera": true,
    "buttons": true,
    "frameColor": { "hex": "#6e44ff" }
  }
}
```

**Live elements on a scrolling phone screen.** From the fixture page `fixture-devices`, the text shortened. The device defaults to a portrait phone; `scrollable` lets content taller than the screen scroll by wheel, touch and keyboard, and `camera` pushes the content down to clear the cutout.

```json
{
  "name": "bfbe-devices",
  "settings": {
    "camera": true,
    "scrollable": true
  },
  "children": [
    { "name": "heading", "settings": { "text": "Hello", "tag": "h4" } },
    { "name": "text-basic", "settings": { "text": "Scrollable text inside the phone." } }
  ]
}
```

**A screenshot in a browser window, shown whole.** From the fixture page `fixture-devices-media`, the address and image made generic. Put an attachment from this site's media library in `image`; its alt text becomes the image's. `mediaFit: "contain"` keeps the whole picture; a 1600 x 1000 (16 : 10) image fills the screen without bands.

```json
{
  "name": "bfbe-devices",
  "settings": {
    "device": "browser",
    "address": "example.com/app",
    "content": "image",
    "image": { "id": 123, "size": "large", "url": "https://example.com/wp-content/uploads/app-screenshot.png" },
    "mediaFit": "contain"
  }
}
```

## Gotchas

- **Children vanish in image or video mode.** With `content: "image"` or `"video"`, nested children stay saved but are not rendered. The canvas says "Nested elements show in the nested screen mode."; the page says nothing. <!-- src: plugins/bfb-elements-pro/elements/devices.php:525; plugins/bfb-elements-pro/elements/devices.php:591 -->
- **The screen keeps the device's proportions, so nested content is clipped.** Phone 9 : 19.5, tablet 3 : 4, laptop and browser 16 : 10, with `overflow: hidden`. Content taller than the screen is cut off unless `scrollable` is on. <!-- src: src/elements/devices/devices.css:51; src/elements/devices/devices.css:52; src/elements/devices/devices.css:63 -->
- **Media of another shape is cropped from the middle by default.** A 16 : 9 shot in a portrait phone keeps 26% of its width. Set `mediaPosition` for the part that stays, or `mediaFit: "contain"` with a `screenBackground` for the bands. Sizes that fit: 1170 x 2535 (phone), 1536 x 2048 (tablet), 1600 x 1000 (laptop, browser). <!-- src: plugins/bfb-elements-pro/elements/devices.php:41; docs/elements/devices.md "Side buttons, and media that does not fit the screen" -->
- **A clean clip needs Autoplay.** Without `videoAutoplay` the browser's controls always show and `videoControls` changes nothing. Autoplay is always muted and looping; there is no setting for sound. <!-- src: plugins/bfb-elements-pro/elements/devices.php:512; plugins/bfb-elements-pro/elements/devices.php:583 -->
- **Under reduced motion no clip starts by itself.** Controls on or off, the clip waits paused for the visitor, and the screen switch gives way to the browser's controls. <!-- src: src/elements/devices/devices.js:23; src/elements/devices/devices.js:58 -->
- **The canvas does not pause the clip.** In the builder a click on the screen selects the element; the switch acts on the page. <!-- src: src/elements/devices/devices.js:47; docs/elements/devices.md "Round 453" -->
- **Width is in px, and its default depends on the device.** Unset, it is 320px for a phone, 480px tablet, 640px laptop and 720px browser, though the panel shows 320px. Bezel, corner and cutout are fractions of it, and the control warns that other units bend the frame. <!-- src: src/elements/devices/devices.css:3; src/elements/devices/devices.css:65; src/elements/devices/devices.css:102; src/elements/devices/devices.css:110; plugins/bfb-elements-pro/elements/devices.php:107 -->
- **A squeezed device keeps the proportions of its set width.** The frame narrows to its column, but bezel and corner stay worked out from `width`: a 320px phone in a 180px column reads a 22% corner, not 12.5%. Bricks' `_width` on the element squeezes it the same way. Set `width` per breakpoint (`width:mobile_portrait`) instead. <!-- src: docs/elements/devices.md "A device squeezed by a container narrower than its width"; src/elements/devices/devices.css:50 -->
- **A set Bezel or Corner radius stops scaling.** Unset, `bezel` and `radius` follow `width`; a value set from the panel stays that number at every width. <!-- src: src/elements/devices/devices.css:12; docs/elements/devices.md "A device keeps its shape at any size" -->
- **Frame colour and Bezel change nothing on a Browser window.** Its frame is the pack's surface tint with no padding. Colour the bar with `chromeBackground`, which paints the whole bar, and the outline with `frameBorder`. <!-- src: src/elements/devices/devices.css:110; src/elements/devices/devices.css:111; measured on fixture-devices 2026-10-08 (frame background and padding unchanged with --bfbe-dev-frame and --bfbe-dev-bezel set) -->
- **Screen padding adds to the content's own padding.** `screenPadding` pads the screen around `.bfbe-dev__content`, which keeps its 16px. For edge-to-edge nested content, set `padding: 0` on `.that-class .bfbe-dev__content` in custom CSS. <!-- src: src/elements/devices/devices.css:52; plugins/bfb-elements-pro/elements/devices.php:290 -->
- **An image `id` must be in this site's library.** With an `id`, the screen draws that attachment and the `url` beside it is ignored, so an id from another site draws an empty screen. A `url` alone draws with `alt=""`. <!-- src: plugins/bfb-elements-pro/elements/devices.php:575; plugins/bfb-elements-pro/elements/devices.php:578; plugins/bfb-elements/includes/abstract-element.php:1417 -->

## Never do

- Do not nest children under `content: "image"` or `content: "video"`; they need nested mode to render.
- Do not put more nested content on a screen than fits without `scrollable: true`.
- Do not set `width` in a unit other than px, and do not size the device with Bricks' `_width`.
- Do not set `bezel` or `radius` unless the device must keep that number at every width.
- Do not set `frameColor` or `bezel` on `device: "browser"`; use `chromeBackground` and `frameBorder`.
- Do not copy an image `id` from another site; upload the picture to this site's library and use its id.
- Do not carry the message in the clip alone: under reduced motion it never starts by itself.
