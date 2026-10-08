---
name: bfbe-cursor
description: "Use when adding a custom mouse cursor with BFB Interactive Cursor (`bfbe-cursor`): a ring that follows the pointer, grows over links and buttons, says a word such as View over tagged cards, and drives spotlight, reveal, image trail and floating gallery effects on tagged blocks. Read before writing its settings or tagging its targets."
---

# BFB Interactive Cursor (`bfbe-cursor`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-cursor.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/cursor/

## What it is
A ring that follows the mouse pointer, grows over links and buttons, and can show a word inside itself over anything you tag. The browser's own pointer stays unless you hide it, and steps aside only while the ring shows a word. The ring switches itself off for touch, reduced motion and forced colors. Block effects add a spotlight, a reveal, an image trail or a floating gallery image to any block you tag.

**Not for:** Not for guiding keyboard or touch visitors: the ring follows a mouse alone and is hidden from assistive technology, so it carries nothing a visitor must know. One Interactive Cursor runs per page, so place a single one, usually in the header template.

**Costs a page:** CSS 2.05 KB, JS 2.83 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** no · **In a query loop:** no · **Dynamic data:** yes · **Keyboard:** no · **Reduced motion:** yes

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Cursor (`bfbeCursor`)
- `mode` (select) **Native cursor**: options: `ring` Keep it, add the ring (default), `replace` Hide it, `none` Keep it, effects only. What happens to the browser's own pointer. Keep it, add the ring is the default. Hide it swaps the pointer for the ring and a dot. Keep it, effects only draws no ring.
- `lag` (number) **Follow delay**. How far the ring lags behind the pointer, from 0 for instant to 1 for lazy. The default is 0.15. Raise it for a looser trail.
- `offBelow` (select) **Off below**: options: `never` Never, `480` 480px, `640` 640px, `768` 768px, `992` 992px (default). The window width at or under which the ring and the Block effects are off, 992px by default. Choose Never to keep them on at every width where a mouse is used.
- `shape` (select) **Shape**: options: `ring` Ring (default), `cross` Crosshair. Choose Ring, the default, or Crosshair. A Crosshair turns into the ring over anything it grows over, and while it shows a word.

### Hover effect (`bfbeHover`)
- `hoverSelector` (text) **Grows over**: placeholder a, button, [role="button"]. The CSS selector for what the ring grows over, a, button, [role="button"] by default. Add your own classes when cards or custom buttons should count too.
- `labels` (repeater) **Labels**. Add rows that pair a CSS selector (Over) with a word (Say). The word shows inside the ring over matching elements. Say accepts dynamic data. Giving any element data-bfbe-cursor="View" does the same.
- `magnet` (checkbox) **Magnetic**. Tick it to pull the elements the ring grows over toward the pointer. Use it for call-to-action buttons and leave it off for body links.
- `magnetPull` (number) **Pull (px)**: only when `magnet` is set. How far a magnetic element can move toward the pointer, 12px unless set.
- `sticky` (checkbox) **Ring hugs the element**. Tick it so the ring takes the shape of the element it is over. Use it for a highlight box, not a growing circle.
- `stickyPad` (number) **Hug distance (px)**: only when `sticky` is set. The room between the element and the ring that hugs it, 6px unless set.
Styling, in the schema file: `hoverScale`.

### Look (`bfbeLook`)
- `blend` (select) **Blend**: options: `normal` Normal (default), `difference` Invert what is under it. Choose Normal, the default, or Invert what is under it. Inverting blends the ring by difference, so it stays visible on light and dark areas.
- `noFillBorder` (checkbox) **No border once filled**. Tick it to drop the ring's border while it is filled, over an element or behind a word. It is off by default.
Styling, in the schema file: `size`, `color`, `ringBorder`, `dotSize`, `fill`, `labelBackground`, `labelTypography`.

### Motion (`bfbeMotion`)
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS. The curve those changes follow, Snappy unless set.
- `stretch` (checkbox) **Stretches with speed**. Tick it to stretch the ring along its direction of travel as the pointer speeds up. It is off by default.
- `stretchAmount` (number) **Stretch**: only when `stretch` is set. How much the ring stretches, 0.35 unless set, from 0 to 1.
- `pulse` (checkbox) **Pulses on click**. Tick it to send a pulse out of the ring each time the pointer is pressed. It is off by default.
Styling, in the schema file: `duration`, `easingCustom`, `pulseColor`.

### Block effects (`bfbeFx`)
- `trailImages` (image-gallery) **Images**. Under Image trail, the pictures that appear along the pointer's path over a block whose data-bfbe-fx is trail. With none chosen, the trail uses the pictures inside the block.
- `trailEvery` (number) **Spacing (px)**. How far the pointer travels between two trail pictures, 80 by default.
- `followImages` (image-gallery) **Images**. Under Image trail, the pictures that appear along the pointer's path over a block whose data-bfbe-fx is trail. With none chosen, the trail uses the pictures inside the block.
Styling, in the schema file: `fxSize`, `fxColor`, `fxFade`, `fxEdge`, `trailSize`, `trailLife`, `followSize`, `followBorder`.

### In the builder (`bfbeBuilder`)
- `builderView` (select) **Show it**: options: `open` Still, so you can style it (default), `live` Working, as on the site. Still, the default, shows the ring and the dot where the element sits, so you can style them. Working lets the ring follow the pointer over the canvas.

## What it guarantees for accessibility (do not undo)
- The ring, dot and label are aria-hidden and ignore pointer events, so they add nothing to the reading order and never block a click.
- It follows a mouse alone: touch, pen and keyboard input never move it. The browser's own pointer hides only under Hide it, or while the ring shows a word.
- For coarse pointers, reduced motion or forced colors, the script never tracks the pointer, and the stylesheet hides the ring and the Block effects.
- Where Hide it is chosen, the browser's own pointer is hidden just when motion is not reduced and forced colors are off.
- The browser's own pointer returns over text fields, text areas and selects, even where Hide it is chosen.
<!-- bfbe:generated:end -->

## Rendered DOM

One `div` overlay with Bricks' `brxe-bfbe-cursor` class and `id="brxe-<id>"`: `position: fixed`, `inset: 0`, `z-index: 99999`, `pointer-events: none`, `contain: strict`, `aria-hidden="true"`. It is `display: none` until the first mouse move adds `is-ready`.

```html
<div id="brxe-c46fdf" class="brxe-bfbe-cursor bfbe-cursor bfbe-cursor--no-fill-border bfbe-cursor--off-992 is-ready is-label"
     aria-hidden="true" data-bfbe-hover="a, button, [role=&quot;button&quot;]" data-bfbe-lag="0.15" data-bfbe-magnet="12"
     data-bfbe-labels="[{&quot;s&quot;:&quot;.hl-look&quot;,&quot;t&quot;:&quot;Look&quot;}]" data-bfbe-off="992">
  <div class="bfbe-cursor__ring"></div><div class="bfbe-cursor__pulse"></div>
  <div class="bfbe-cursor__dot"></div><div class="bfbe-cursor__label">Look</div>
  <span class="bfbe-cursor__ring-style" aria-hidden="true"></span><span class="bfbe-cursor__follow-style" aria-hidden="true"></span>
</div>
```

- **Root classes**: `bfbe-cursor--replace` or `--none` from `mode` (`ring` writes none); `--cross` from `shape`; `--difference` from `blend`; `--no-fill-border`; `--off-480|640|768|992` from `offBelow` (`never` writes none); in the builder only, `--canvas`, plus `--live` under `builderView: "live"`.
- **Data attributes the script reads**: `data-bfbe-hover` (the Grows over selector), `-lag`, `-labels` (JSON rows `{s, t}`) and `-off`; `-magnet`, `-sticky`, `-stretch` and `-pulse` only when their switch is on; `-trail` when `trailEvery` is set; `-trail-images` and `-gallery-images` (JSON lists of URLs) when the Images controls hold pictures.
- **Script states on the root**: `is-hover` (over a Grows over match), `is-label` (a word showing), `is-stuck` (hugging), `is-down` and `is-pulse` (pressed), `is-out` (pointer off the page or over the admin bar). Positions are inline variables: `--bfbe-cur-x/-y` for the pointer, `--bfbe-cur-rx/-ry` for the lagging ring.
- **Elsewhere on the page**: `html.bfbe-cursor-none` hides the native pointer. A pulled or hugged element gets `bfbe-cursor-target` and, with Magnetic, an inline `transform`. A tagged block under the pointer gets `is-fx`, `--bfbe-fx-on` and `--bfbe-fx-x/-y`, and receives `img.bfbe-fx__trail` pictures or one `img.bfbe-fx__follow` (`is-on` while it shows).
- **Where controls write**: `size`, `color`, `fill`, `hoverScale`, `labelBackground`, `duration` and `easing` are variables on the root. So are `fxSize`, `fxColor`, `fxFade`, `fxEdge`, `trailSize`, `trailLife` and `followSize`, which the script copies to `<html>` when it sets up. `labelTypography` goes to `.bfbe-cursor__label`, `dotSize` only on `.bfbe-cursor--replace`, `pulseColor` only on `[data-bfbe-pulse]`.
- **The two Borders** (`ringBorder`, `followBorder`) land on the hidden proxy spans; the script reads them into the ring's variables and the gallery image's.
- **The label's text** is the system `Canvas` colour (white on a light scheme) on a disc filled with **Label background** (`labelBackground`), which falls back to **Colour** (`color`).

## Wiring to other elements

One overlay per page that targets other elements by CSS selector and by attribute; nothing targets it. Only the first `.bfbe-cursor` in the document runs, and a second stays hidden.

- **What grows the ring**: **Grows over** (`hoverSelector`) is a CSS selector matched with `closest()` from the element under the pointer, so anything inside a match counts. **Magnetic** (`magnet`) and **Ring hugs the element** (`sticky`) act on the same matches.
- **Words by selector**: each **Labels** (`labels`) row pairs **Over** (`selector`) with **Say** (`text`), as `[{"selector": ".hl-look", "text": "Look"}]`. A row missing either is dropped.
- **Words by attribute**: put `data-bfbe-cursor` on the target through `_attributes`, `[{"name": "data-bfbe-cursor", "value": "Drag"}]`. Its value takes dynamic data per element, so each card of a query loop can carry its own word; **Say** resolves once, where the cursor renders.
- **Select by class**: give each target a class in `_cssClasses` and select it (`".hl-look"`). Never an id or `_cssId`: component instances share ids, and Bricks drops an element's id inside a query loop.
- **Block effects**: tag a block through `_attributes` with `data-bfbe-fx` set to `spotlight`, `reveal`, `trail` or `gallery`. Their look comes from this element's **Block effects** controls, shared by every tagged block on the page.
- **`reveal`** needs a direct child carrying `data-bfbe-fx-layer` (the fixture gives it `1`). The layer is laid over its parent with the parent's padding and flex settings, and shows through a circle at the pointer, **Spot size** (`fxSize`) in radius.
- **`trail`** spawns the pictures of **Images** (`trailImages`), one per **Spacing (px)** (`trailEvery`, 80 unless set) of pointer travel; with that control empty, it uses the `img` elements inside the block.
- **`gallery`** treats the block's direct children as its items. Each shows the `followImages` picture of the same rank, or the URL in its own `data-bfbe-fx-image`, which wins and is where a loop's dynamic tag goes.
- The tags do nothing on a page without the cursor, since its stylesheet and script load only where the element is.

## Verified patterns

**A labelled ring over photo cards.** From the demo page `/demo-bfb-cursor/`: a lookbook whose three photo cards carry the class `hl-look`. The native pointer stays, the ring fills violet and says "Look" over each card, and links and buttons pull 12px towards the pointer; `noFillBorder` drops the outline once filled.

```json
{
  "name": "bfbe-cursor",
  "settings": {
    "labels": [ { "selector": ".hl-look", "text": "Look" } ],
    "magnet": true,
    "magnetPull": 12,
    "labelBackground": { "hex": "#6e44ff" },
    "labelTypography": { "color": { "hex": "#ffffff" } },
    "noFillBorder": true
  }
}
```

**Every pointer effect, with pictures for the Block effects.** From the fixture page `fixture-cursor`. Links and buttons pull 14px and the ring hugs them 8px out. It stretches with speed, pulses on a click, and `ringBorder`'s corners make it a dashed rounded square. The card it labels carries `cursor-card` in `_cssClasses`; `builderView: "live"` lets it follow the pointer in the canvas. The media ids are the demo site's and the URLs are placeholders at `https://example.com/`: use the target site's own attachments.

```json
{
  "name": "bfbe-cursor",
  "settings": {
    "labels": [ { "selector": ".cursor-card", "text": "View" } ],
    "duration": 700,
    "easing": "cubic-bezier(0.34, 1.56, 0.64, 1)",
    "magnet": true,
    "magnetPull": 14,
    "sticky": true,
    "stickyPad": 8,
    "stretch": true,
    "stretchAmount": 0.4,
    "pulse": true,
    "fxSize": "260px",
    "trailLife": 1000,
    "builderView": "live",
    "trailImages": { "size": "large", "images": [
      { "id": 968, "filename": "bfbe-outfit.jpg", "size": "large", "url": "https://example.com/wp-content/uploads/bfbe-outfit-896x1024.jpg", "full": "https://example.com/wp-content/uploads/bfbe-outfit.jpg" },
      { "id": 969, "filename": "bfbe-living-room.jpg", "size": "large", "url": "https://example.com/wp-content/uploads/bfbe-living-room-1024x704.jpg", "full": "https://example.com/wp-content/uploads/bfbe-living-room.jpg" }
    ] },
    "followImages": { "size": "large", "images": [
      { "id": 969, "filename": "bfbe-living-room.jpg", "size": "large", "url": "https://example.com/wp-content/uploads/bfbe-living-room-1024x704.jpg", "full": "https://example.com/wp-content/uploads/bfbe-living-room.jpg" },
      { "id": 968, "filename": "bfbe-outfit.jpg", "size": "large", "url": "https://example.com/wp-content/uploads/bfbe-outfit-896x1024.jpg", "full": "https://example.com/wp-content/uploads/bfbe-outfit.jpg" }
    ] },
    "followSize": "240px",
    "followBorder": { "width": { "top": "2", "right": "2", "bottom": "2", "left": "2" }, "style": "solid", "color": { "hex": "#f5efe6" }, "radius": { "top": "12", "right": "12", "bottom": "12", "left": "12" } },
    "ringBorder": { "width": { "top": "3", "right": "3", "bottom": "3", "left": "3" }, "style": "dashed", "color": { "hex": "#e11d48" }, "radius": { "top": "10", "right": "10", "bottom": "10", "left": "10" } }
  }
}
```

**A reveal block for the cursor to drive.** From `fixture-cursor`. A dark block tagged `reveal` whose yellow layer child, tagged `data-bfbe-fx-layer`, shows a second headline through a circle at the pointer. It needs a cursor on the same page; the circle's radius is that cursor's `fxSize`.

```json
{
  "name": "block",
  "settings": {
    "_attributes": [ { "name": "data-bfbe-fx", "value": "reveal" } ],
    "_background": { "color": { "hex": "#0f172a" } },
    "_typography": { "color": { "hex": "#f8fafc" } },
    "_padding": { "top": "72", "right": "48", "bottom": "72", "left": "48" }
  },
  "children": [
    { "name": "heading", "settings": { "text": "We build websites that people remember.", "tag": "h2" } },
    { "name": "block",
      "settings": { "_attributes": [ { "name": "data-bfbe-fx-layer", "value": "1" } ], "_background": { "color": { "hex": "#fde047" } }, "_typography": { "color": { "hex": "#0f172a" } } },
      "children": [ { "name": "heading", "settings": { "text": "We build brands that people talk about.", "tag": "h2" } } ] }
  ]
}
```

## Gotchas

- **A header that moves takes the ring with it.** An ancestor with a `transform`, `translate`, `filter` or `backdrop-filter` becomes the fixed overlay's box, and `contain: strict` clips the ring to it. Bricks' sticky header sliding up, Advanced Header Scroll hiding the header, and **Blur behind** on an element around it all do this while active. <!-- src: src/elements/cursor/cursor.css:12-16; Bricks assets/css/frontend.min.css `#brx-header.brx-sticky.slide-up` (transform: translateY(-101%)); src/elements/header-scroll/header-scroll.css:54, 161; measured 2026-10-08 in headless Chrome with the shipped cursor.css and cursor.js: under each of the three the overlay shrank to the 80px header box -->
- **The root is the whole window.** Bricks' Style tab writes on the fixed overlay itself, so `_background` paints over the page at `z-index: 99999`, and a `_width`, `_height`, `_border` or `_position` shrinks or shifts the box the ring is clipped to. Style the ring with the Look controls. <!-- src: src/elements/cursor/cursor.css:2-19 -->
- **Off at 992px and under, by default.** `offBelow` is `992` unless set: at that window width or narrower, 992 itself included, the ring and the Block effects are off. Set `"never"` or a smaller width to keep them in narrow mouse windows. <!-- src: plugins/bfb-elements-pro/elements/cursor.php:535, 584-587; src/elements/cursor/cursor.css:105; src/elements/cursor/cursor.js:99 -->
- **The canvas is not the page.** With **Show it** (`builderView`) on Still, the default, the ring and dot sit still in a strip, and a reveal layer shows through a fixed middle circle. Working follows the pointer, but `offBelow` counts the canvas width, so a canvas under 992px shows nothing. <!-- src: src/elements/cursor/cursor.css:121, 150-152; src/elements/cursor/cursor.js:72; docs/elements/cursor.md "Round 409" -->
- **The ring takes the text colour around it.** **Colour** defaults to `currentColor`, the text colour of the element the cursor sits in, so a cursor in a header with white text draws a white ring over a white page. <!-- src: src/elements/cursor/cursor.css:4-6 -->
- **Grows over replaces the defaults.** A `hoverSelector` of `".card"` alone stops links and buttons growing the ring; write `"a, button, [role=\"button\"], .card"` to add to them. A selector that does not parse grows over nothing, with no error. <!-- src: plugins/bfb-elements-pro/elements/cursor.php:562; src/elements/cursor/cursor.js:234 -->
- **A label wins.** `data-bfbe-cursor` on the element or an ancestor beats every Labels row, and among rows the first match wins. A labelled element never grows the ring, is never pulled by Magnetic and is never hugged. <!-- src: src/elements/cursor/cursor.js:207-215, 235-238 -->
- **Keep it, effects only shows nothing of the pointer.** `mode: "none"` hides the ring, the dot and the label, so Labels, `sticky` and `pulse` show nothing, and the native pointer stays even over a label. Magnetic and the Block effects still act. <!-- src: src/elements/cursor/cursor.css:93; src/elements/cursor/cursor.js:104, 238 -->
- **A Border style without a colour draws grey.** In `ringBorder`, a width and a style with no colour draw Bricks' own `var(--bricks-border-color)`, not **Colour**. A width alone keeps the ring in **Colour**. <!-- src: docs/elements/cursor.md "Round 408"; plugins/bfb-elements-pro/elements/cursor.php:156-157 -->
- **Magnetic owns the target's transform.** The script writes an inline `transform` on each element it pulls and clears it when the pointer leaves, overriding that element's **Transform** (`_transform`) and the Tilt hover effect meanwhile. <!-- src: src/elements/cursor/cursor.js:115, 222, 240; src/elements/hover/hover.css:45 -->
- **An empty number is not its placeholder.** An empty string in `magnetPull`, `stickyPad` or `stretchAmount` renders as a 1px pull, a 0px hug and no stretch at all. Leave the key out for 12, 6 and 0.35. <!-- src: plugins/bfb-elements-pro/elements/cursor.php:569, 572, 575; rendered 2026-10-08: data-bfbe-magnet="1" data-bfbe-sticky="0" data-bfbe-stretch="0" -->
- **A tagged block changes.** `data-bfbe-fx` makes a block `position: relative`, `trail` adds `overflow: hidden`, and a reveal layer ignores the pointer, so a link or button inside it cannot be clicked. <!-- src: src/elements/cursor/cursor.css:113, 117, 123 -->

## Never do

- Do not place the cursor inside a header that hides on scroll, or inside an element with a transform, filter, backdrop-filter or Blur behind; put it at the top level of a template or page that stays put.
- Do not set Bricks' Style tab background, size, border or position on the cursor.
- Do not write a `hoverSelector` without `a, button, [role="button"]` when links and buttons should still grow the ring.
- Do not target by id or `_cssId` in `hoverSelector` or a Labels row's `selector`; use a class from `_cssClasses`.
- Do not set a `style` in `ringBorder` without its `color`.
- Do not write `""` into `magnetPull`, `stickyPad` or `stretchAmount`.
- Do not put links, buttons or fields inside a reveal layer (`data-bfbe-fx-layer`).
- Do not carry anything a visitor must know in a label word or a Block effect: touch, keyboard and reduced-motion visitors never see them.
