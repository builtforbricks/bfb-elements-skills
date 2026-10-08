---
name: bfbe-scroll-video
description: "Use when placing, wiring or styling BFB Scroll Video (`bfbe-scroll-video`): a muted video whose playhead follows the scroll position, so scrolling plays it forward and back. Read before writing its settings."
---

# BFB Scroll Video (`bfbe-scroll-video`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-scroll-video.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/scroll-video/

## What it is
A muted video whose playhead follows the scroll position, so scrolling plays it forward and back. Pinned while scrolling holds it on screen while visitors scroll through a section a set number of screen heights tall, and Scrubs as it passes moves it as it crosses the viewport. With Pinned while scrolling, blocks you drop inside scroll past over the film, which stays pinned behind them.

**Not for:** Not for a film with sound or one that visitors start and stop themselves: the video is muted and its playhead belongs to the scroll position. Footage that was not encoded with frequent keyframes will stutter while it scrubs.

**Costs a page:** CSS 0.89 KB, JS 1.20 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** yes · **In a query loop:** no · **Dynamic data:** yes · **Keyboard:** no · **Reduced motion:** yes

## Structure
Nestable: any Bricks element goes inside (blocks, headings, text, images, a form).

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Video (`bfbeVideo`)
- `file` (file) **Video file**. The file to scrub. Encode it with a keyframe every five frames, or the playhead will freeze and jump as it seeks.
- `url` (text) **Or a video URL**: placeholder https://example.com/sequence.mp4; dynamic data accepted. An address to use when no file is chosen. It accepts dynamic data. A chosen file wins over the typed address.
- `poster` (image) **Poster**. The image shown before the video loads, and in the plain video that appears when scrubbing is off.

### Scrolling (`bfbeScroll`)
- `mode` (select) **Behaviour**: options: `pinned` Pinned while scrolling (default), `inview` Scrubs as it passes. Choose Pinned while scrolling, the default, or Scrubs as it passes. Pinned keeps the video on screen while the page scrolls, and Scrubs moves the playhead as the video passes across the screen.
- `smoothing` (checkbox) **Smooth the scrub**. Tick it to ease the playhead toward the scroll position instead of jumping to it. It is off by default.
- `smoothStrength` (select) **Smoothing strength**: options: `light` Light, `medium` Medium (default), `heavy` Heavy; only when `smoothing` is set. Light, Medium, the default, or Heavy. Heavy trails the scroll the most.
- `offBelow` (select) **Plain video below**: options: `never` Never, `480` 480px, `640` 640px, `768` 768px (default), `992` 992px. 768px by default, or Never. Under that width the film becomes a plain video, with controls when nothing is nested inside it.
Styling, in the schema file: `distance`.

### Look (`bfbeLook`)
- `videoAt` (select) **Video sits**: options: `top` Top, `center` Centre (default), `bottom` Bottom; writes CSS; only when `mode` is not `inview`. With Pinned while scrolling and a Video height shorter than the screen, where the video sits: Top, Centre or Bottom. Centre is the default.
- `fit` (checkbox) **Fill the screen**: only when `mode` is not `inview`. Tick it to make the pinned video cover the screen, cropped to fit, instead of keeping its own shape.
Styling, in the schema file: `videoHeight`, `stageBorder`, `shadow`, `background`, `overlayColor`, `overlayGradient`.

### In the builder (`bfbeBuilder`)
- `builderCompact` (checkbox) **Keep it compact**. Tick it to show the film small and still in the canvas. Left off, the film scrubs as you scroll the canvas.

## What it guarantees for accessibility (do not undo)
- The video is muted, and scrolling by any means moves the playhead, the keyboard included, because the script follows the page's scroll position.
- Under reduced motion, below Plain video below, or without the script, the playhead no longer follows the scroll.
- With nothing nested inside, it is then an ordinary video with the browser's own controls.
- With blocks inside, the film is a background with no controls in its markup, and it stays still wherever scrubbing is off.
<!-- bfbe:generated:end -->

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
