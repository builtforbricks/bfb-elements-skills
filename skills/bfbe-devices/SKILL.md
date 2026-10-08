---
name: bfbe-devices
description: "Use when placing, wiring or styling BFB Devices (`bfbe-devices`): a phone, tablet, laptop or browser window drawn in CSS around live nested elements, an image or a video. Read before writing its settings."
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

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
