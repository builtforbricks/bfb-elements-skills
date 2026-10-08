---
name: bfbe-scroll-video
description: "Use when building a scroll-scrubbed film with BFB Scroll Video (`bfbe-scroll-video`): a muted video whose playhead follows the scroll, pinned while content scrolls over it or scrubbing as it passes. Read before writing its settings."
---

# BFB Scroll Video (`bfbe-scroll-video`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.3 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
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

## Rendered DOM

```html
<div id="brxe-…" class="brxe-bfbe-scroll-video bfbe-sv bfbe-sv--pinned bfbe-sv--off-768 bfbe-sv--fit is-scrub" data-bfbe-smooth="0.18" style="--bfbe-sv-shape: 1280 / 720">
  <div class="bfbe-sv__track">
    <div class="bfbe-sv__stage">
      <video class="bfbe-sv__video" src="…" poster="…" muted playsinline preload="metadata" controls></video>
      <div class="bfbe-sv__shade" aria-hidden="true"></div>
    </div>
  </div>
  <!-- each nested element, a direct child of the root -->
</div>
```

- Root classes from the PHP: `.bfbe-sv`; `.bfbe-sv--pinned` or `.bfbe-sv--inview` (`mode`); `.bfbe-sv--off-480`, `-640`, `-768` or `-992` (`offBelow`, none with `never`); `.bfbe-sv--fit` (`fit`, pinned only). With `smoothing` on, `data-bfbe-smooth` is the catch-up factor: 0.3 light, 0.18 medium, 0.08 heavy. <!-- src: plugins/bfb-elements-pro/elements/scroll-video.php:332-344 -->
- States the script sets: `.is-scrub` while the playhead follows the scroll, `.bfbe-sv--static` when it does not (below the plain width, reduced motion). It pauses the video and removes `controls` while scrubbing or with blocks inside, and raises `preload` to `auto` once the element is within a fifth of a screen. <!-- src: src/elements/scroll-video/scroll-video.js:43-52,91-97 -->
- `--bfbe-sv-shape` in the root's inline style is the video's own proportion, written when its metadata loads. The video has no `autoplay` or `loop`; the page's markup carries `controls` only with nothing nested inside. <!-- src: src/elements/scroll-video/scroll-video.js:84-89, plugins/bfb-elements-pro/elements/scroll-video.php:366 -->
- The track is `position: absolute; inset: 0; z-index: -1` in a root with `isolation: isolate`, so nested elements paint over the film and never move it. Pinned, the stage is `position: sticky`, as tall as Video height (`100svh` unset). <!-- src: src/elements/scroll-video/scroll-video.css:5-7,13 -->
- Pinned, the root's `min-block-size` is Scroll length times `100svh`, with `padding-block: 50vh` and `row-gap: 50vh`. Bricks prints the root's own Layout values on `#brxe-<id>`, which outranks them. <!-- src: src/elements/scroll-video/scroll-video.css:12; the fixture page's printed CSS, #brxe-ec1122 -->
- Scrubs as it passes: the stage is rounded with the pack's radius (12px unset). With nested elements the root becomes the video's box, its children centred both ways. <!-- src: src/elements/scroll-video/scroll-video.css:22-26 -->
- Control to part: `distance`, `videoHeight` and `videoAt` write `--bfbe-sv-distance`, `--bfbe-sv-h` and `--bfbe-sv-at` (0, 0.5, 1) on the root; `stageBorder` and `background` write to `.bfbe-sv__stage`; `shadow` to `.bfbe-sv__video`; `overlayColor` and `overlayGradient` to `.bfbe-sv__shade`. The video inherits the stage's corners. <!-- src: plugins/bfb-elements-pro/elements/scroll-video.php:99-243, src/elements/scroll-video/scroll-video.css:14 -->
- Builder only: `.bfbe-sv--canvas` with Keep it compact; `.bfbe-empty` and a notice while no video resolves. <!-- src: plugins/bfb-elements-pro/elements/scroll-video.php:319-326,346-348 -->

## Wiring to other elements

Stands alone; nothing targets it and it targets nothing.

- Nested elements are the root's own children, as in a Bricks block. Place them with Bricks' Layout controls on the Scroll Video: **Display** (`_display: "flex"`), **Align cross axis** (`_alignItems`, across), **Align main axis** (`_justifyContent`, down the scroll), **Row gap** (`_rowGap`) and **Padding** (`_padding`), each per breakpoint. Each child keeps its own **Align self** (`_alignSelf`). <!-- src: docs/elements/scroll-video.md "Round 421", plugins/bfb-elements/includes/abstract-element.php:798-843 -->
- The script starts every `.bfbe-sv` on load and again on Bricks' `bricks/ajax/pagination/completed`, `bricks/ajax/load_page/completed`, `bricks/ajax/query_result/displayed` and `bricks/ajax/popup/loaded` events. One inserted by any other script starts when you call `window.bfbeScrollVideo()`, which is safe to call again. <!-- src: src/elements/scroll-video/scroll-video.js:10,110-121 -->

## Verified patterns

`7497` and `22` in `poster` are attachment ids from the development site's media library; write the target site's own. The video addresses are `https://example.com/...` in place of that site's files; write the target site's own.

**A pinned film, nothing inside.** From the demo page `demo-bfb-scroll-video` (the Northwind pour). It scrubs across three screen heights with the smoothing at Medium; `offBelow`, `smoothStrength` and `fit` are left out as their defaults. The 18px corners come from `stageBorder`, and `background` paints the stage around the film's own shape.

```json
{
  "name": "bfbe-scroll-video",
  "settings": {
    "url": "https://example.com/wp-content/uploads/northwind-pour.mp4",
    "poster": { "id": 7497, "size": "large" },
    "mode": "pinned",
    "distance": 3,
    "smoothing": true,
    "stageBorder": { "radius": { "top": "18px", "right": "18px", "bottom": "18px", "left": "18px" } },
    "background": { "hex": "#101828" }
  }
}
```

**Cards scrolling over a pinned, darkened film.** From the fixture page `fixture-scroll-video` (`.sv-layered`), its probe classes and card corners left out. `_display: "flex"` with `_alignItems: "flex-end"` puts the cards at the right, and `overlayColor` darkens the film under them. Three cards outgrow the two-screen `distance`, so the element is as long as they are.

```json
{
  "name": "bfbe-scroll-video",
  "settings": {
    "url": "https://example.com/wp-content/uploads/scrub.mp4",
    "poster": { "id": 22 },
    "fit": true,
    "distance": 2,
    "overlayColor": { "rgb": "rgba(0, 0, 0, 0.3)" },
    "_display": "flex",
    "_alignItems": "flex-end"
  },
  "children": [
    { "name": "block", "settings": { "_widthMax": "360px", "_background": { "color": { "hex": "#ffffff" } }, "_padding": { "top": "28", "right": "28", "bottom": "28", "left": "28" } }, "children": [
      { "name": "heading", "settings": { "text": "Card 1", "tag": "h3" } },
      { "name": "text-basic", "settings": { "text": "Any content, scrolling over the pinned film." } }
    ] },
    { "name": "block", "settings": { "_widthMax": "360px", "_background": { "color": { "hex": "#ffffff" } }, "_padding": { "top": "28", "right": "28", "bottom": "28", "left": "28" } }, "children": [
      { "name": "heading", "settings": { "text": "Card 2", "tag": "h3" } },
      { "name": "text-basic", "settings": { "text": "Any content, scrolling over the pinned film." } }
    ] },
    { "name": "block", "settings": { "_widthMax": "360px", "_background": { "color": { "hex": "#ffffff" } }, "_padding": { "top": "28", "right": "28", "bottom": "28", "left": "28" } }, "children": [
      { "name": "heading", "settings": { "text": "Card 3", "tag": "h3" } },
      { "name": "text-basic", "settings": { "text": "Any content, scrolling over the pinned film." } }
    ] }
  ]
}
```

**A heading over a film that scrubs as it passes.** From the fixture page `fixture-scroll-video` (`.sv-inview-layered`), its probe class left out. `mode: "inview"` with `videoHeight: "400px"` makes a 400px box that scrubs as it crosses the screen, the heading in its middle. The white `_typography` colour is kept so the words read over the film.

```json
{
  "name": "bfbe-scroll-video",
  "settings": {
    "url": "https://example.com/wp-content/uploads/scrub.mp4",
    "mode": "inview",
    "videoHeight": "400px"
  },
  "children": [
    { "name": "heading", "settings": { "text": "Over the film", "tag": "h2", "_typography": { "color": { "hex": "#ffffff" } } } }
  ]
}
```

## Gotchas

- **Encode for seeking, and keep it short.** A seek decodes from the last keyframe, so put one every fifth frame: `ffmpeg -i in.mp4 -an -c:v libx264 -pix_fmt yuv420p -crf 23 -g 5 -keyint_min 5 -sc_threshold 0 -movflags +faststart out.mp4`. A plain encode froze for up to two seconds, and scrubbing downloads the whole file, about one and a half times a normal encode. <!-- src: docs/elements/scroll-video.md:5-11,27-40, src/elements/scroll-video/scroll-video.js:47-49,91-97 -->
- **No video, nothing on the page, nested blocks included.** When neither **Video file** (`file`) nor **Or a video URL** (`url`) resolves, a dynamic tag that comes back empty included, the page prints no markup at all. The builder keeps the blocks under a notice, so the canvas looks fine. <!-- src: plugins/bfb-elements-pro/elements/scroll-video.php:311-330 -->
- **At 768px and narrower it stops scrubbing, even unset.** **Plain video below** (`offBelow`) defaults to 768, and reduced motion stops it at any width. With nothing inside it turns into an ordinary video with controls; with blocks inside the film holds still, pinned, showing the **Poster** (`poster`) or its first frame. <!-- src: docs/elements/scroll-video.md "Round 420", src/elements/scroll-video/scroll-video.css:33-40, src/elements/scroll-video/scroll-video.js:39-52 -->
- **Set Display with the layout controls.** The root is a flex column in the stylesheet, so `_alignItems` alone moves the blocks on the page. The panel shows Align cross axis, Align main axis, Direction and the gaps only with `_display: "flex"`, so without it a designer cannot see the value. <!-- src: plugins/bfb-elements/includes/abstract-element.php:70-71,798-843, docs/elements/scroll-video.md "Round 421" -->
- **Unset, nested blocks sit half a screen apart.** Pinned, the root adds half a screen before the first block, after the last and between them; `_rowGap` and `_padding` replace that. **Scroll length** (`distance`) is the least length: taller content makes the element longer and the film plays across all of it. <!-- src: src/elements/scroll-video/scroll-video.css:9-12, docs/elements/scroll-video.md "Round 420" -->
- **Video height makes a band; three keys are pinned only.** Pinned, **Video height** (`videoHeight`) turns the full-screen stage into a band that **Video sits** (`videoAt`) puts top, centre or bottom, per breakpoint (`videoHeight:mobile_portrait`). `videoAt`, `fit` and `distance` are hidden under `mode: "inview"` and do nothing there. <!-- src: plugins/bfb-elements-pro/elements/scroll-video.php:110,158,189-226, src/elements/scroll-video/scroll-video.css:13,22-26, docs/elements/scroll-video.md "Round 421" -->
- **An in-view box with blocks takes the film's shape late.** It is 16 / 9 until the script reads the video's metadata, and without the script; set `videoHeight` for a box that never changes. <!-- src: src/elements/scroll-video/scroll-video.css:25, src/elements/scroll-video/scroll-video.js:84-89 -->
- **Without Fill the screen, a pinned film keeps its own shape.** It sits centred in a screen-tall stage that **Background** (`background`) paints; `fit: true` covers and crops. Corners come from **Stage border** (`stageBorder`), and **Shadow** (`shadow`) lands on the video, not the stage. <!-- src: src/elements/scroll-video/scroll-video.css:13-15, plugins/bfb-elements-pro/elements/scroll-video.php:161-183, docs/elements/scroll-video.md:46 -->
- **Overflow on an ancestor breaks it.** Under a section, container or block with `overflow: hidden`, the sticky stage scrolls away while the playhead keeps moving (`overflow: clip` keeps it pinned). Inside a box that scrolls on its own (`overflow: auto` or `scroll`) the film does not follow that scroll: the script listens to the window's alone. <!-- src: src/elements/scroll-video/scroll-video.css:13, src/elements/scroll-video/scroll-video.js:102; checked headless on fixture-scroll-video 2026-10-08, the stage's top at -936 with the parent hidden, at 0 with clip -->
- **The canvas pins and scrubs as the page does.** A three-screen element takes three screens of the canvas. **Keep it compact** (`builderCompact`) shows a 360px plain video with the blocks after it, in the builder only. <!-- src: plugins/bfb-elements-pro/elements/scroll-video.php:345-348, src/elements/scroll-video/scroll-video.css:42-45 -->
- **Four keys are retired.** `contentSide`, `contentWidth`, `contentGap` and `contentPadding`, from before round 421, are moved in memory on an older page: into `_alignItems` (with `_display: "flex"`), `_rowGap` and `_padding`, the width dropped. Write the new keys. <!-- src: plugins/bfb-elements-pro/elements/scroll-video.php:264-298 -->

## Never do

- Do not use a video without a keyframe every few frames; re-encode it with `-g 5`.
- Do not leave `file` and `url` both empty, or rely on a dynamic tag in `url` that can come back empty.
- Do not nest blocks without a `poster`.
- Do not set `_alignItems` or `_justifyContent` without `_display: "flex"`.
- Do not set `videoAt`, `fit` or `distance` with `mode: "inview"`.
- Do not place a pinned Scroll Video inside an ancestor with `overflow: hidden`, or inside a box that scrolls on its own.
- Do not write `contentSide`, `contentWidth`, `contentGap` or `contentPadding`; they are retired.
