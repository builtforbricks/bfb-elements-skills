---
name: bfbe-before-after
description: "Use when building a before and after image comparison slider with BFB Before / After Image (`bfbe-before-after`): two photos under a draggable divider, left and right or top and bottom, for a renovation, a retouch or a redesign. Read before writing its settings."
---

# BFB Before / After Image (`bfbe-before-after`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-before-after.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/before-after/

## What it is
Two images sit under a draggable divider that runs left and right or top and bottom. The divider is a native range input, so arrow keys, touch and screen readers all work on it. The frame reserves the images' aspect ratio, taken from the media library, unless you type one.

**Not for:** The divider compares exactly two images, so a sequence of three or more stages needs one comparison per pair. Video and live content cannot go on either side, because both sides are image controls.

**Costs a page:** CSS 1.34 KB, JS 0.79 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** no · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Bricks' query loop (`hasLoop`, `query`); Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Images (`bfbeImages`)
- `before` (image) **Before**. The image to the left of the divider, or above it when Direction is Top and bottom. It accepts a dynamic data tag.
- `after` (image) **After**. The image on the other side of the divider. Choose both images, or the page shows nothing outside the builder.
- `fit` (select) **Image fit**: options: `cover` Fill the frame, cropping (default), `contain` Fit inside the frame; writes CSS. Fill the frame, cropping is the default. Choose Fit inside the frame when no part of either image may be cut off.
- `ratio` (text) **Aspect ratio**: placeholder From the images. Leave it empty to use your images' own ratio, with 16 / 9 as the fallback. Type 4 / 3 to override it.

### Slider (`bfbeSlider`)
- `orientation` (select) **Direction**: options: `horizontal` Left and right (default), `vertical` Top and bottom. Left and right is the default. Pick Top and bottom to stack the images, so the divider moves up and down.
- `start` (number) **Start position (%)**. Where the divider sits when the page loads, 50 by default. Set a value from 0 to 100 when the subject sits off center.
- `hoverMove` (checkbox) **Follow the pointer**. Off by default, so visitors drag the divider. Tick it and a mouse moves the divider without a click. Touch still drags.

### Labels (`bfbeLabels`)
- `showLabels` (checkbox) **Show labels**. Off by default. Tick it to print Before and After on the images.
- `labelBefore` (text) **Label**: placeholder Before; dynamic data accepted; only when `showLabels` is set. Under Before and under After, the word printed on that image, Before or After when left empty. It accepts dynamic data.
- `labelBeforePosition` (select) **Position**: options: `top` Top (default), `middle` Middle, `bottom` Bottom, `custom` Custom; only when `showLabels` is set. Choose Top, Middle, Bottom or Custom for each label. Custom brings up From the left or From the right, plus From the top.
- `labelAfter` (text) **Label**: placeholder After; dynamic data accepted; only when `showLabels` is set. Under Before and under After, the word printed on that image, Before or After when left empty. It accepts dynamic data.
- `labelAfterPosition` (select) **Position**: options: `top` Top, `middle` Middle, `bottom` Bottom, `custom` Custom; only when `showLabels` is set. Choose Top, Middle, Bottom or Custom for each label. Custom brings up From the left or From the right, plus From the top.
Styling, in the schema file: `labelBeforeX`, `labelBeforeY`, `labelAfterX`, `labelAfterY`, `labelTypography`, `labelBackground`, `labelPadding`, `labelBorder`, `labelOffset`.

### Divider (`bfbeDivider`)
Styling only, every key in the schema file: `dividerWidth`, `dividerColor`.

### Handle (`bfbeHandle`)
- `handleText` (text) **Text**: placeholder Drag; dynamic data accepted. A word such as Drag, shown instead of the arrows. It accepts dynamic data, and the arrow controls hide while it is filled in.
- `handleIconLeft` (icon) **Left arrow**: only when `handleText` is not set. Your own icon for the left side of the handle, in place of the drawn arrows.
- `handleIconRight` (icon) **Right arrow**: only when `handleText` is not set. Your own icon for the right side. Leave it empty and it mirrors the left arrow, or set both to use them as they are.
Styling, in the schema file: `handleSize`, `handleBackground`, `handleBorder`, `handleShadow`, `handleIconSize`, `handleIconGap`, `handleIconColor`.

## What it guarantees for accessibility (do not undo)
- The divider is a native range input named Compare plus the two label words, such as Compare Before and After.
- Tab reaches it, and the arrow keys, Home and End move it. In a vertical comparison the Up and Down arrows move the divider the way they point.
- Its value is announced as a percentage through aria-valuetext, updated as the divider moves.
- The labels, the line and the handle are hidden from assistive technology, so the range input is the one control a screen reader finds.
- A visible focus outline is drawn around the handle when the range input has keyboard focus.
- With reduced motion requested, the handle's small hover scale runs with no transition.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<div class="bfbe-ba bfbe-ba--horizontal bfbe-ba__frame" style="--bfbe-ba-pos:50%;--bfbe-ba-ratio:1600 / 1000" data-bfbe-ba-hover="1">
  <img class="bfbe-ba__img bfbe-ba__img--after" loading="eager" draggable="false">
  <div class="bfbe-ba__clip"><img class="bfbe-ba__img bfbe-ba__img--before" loading="eager" draggable="false"></div>
  <input type="range" class="bfbe-ba__range" min="0" max="100" value="50" aria-label="Compare Before and After" aria-valuetext="50%">
  <span class="bfbe-ba__label bfbe-ba__label--before bfbe-ba__label--p-top" aria-hidden="true">Before</span>
  <span class="bfbe-ba__label bfbe-ba__label--after" aria-hidden="true">After</span>
  <div class="bfbe-ba__line" aria-hidden="true"></div>
  <div class="bfbe-ba__handle" aria-hidden="true"><span class="bfbe-ba__arrows"></span></div>
</div>
```

- The root is the frame: one `div` carrying `.bfbe-ba`, `.bfbe-ba--horizontal` or `.bfbe-ba--vertical`, and `.bfbe-ba__frame`, plus Bricks' own id and classes. Bricks' Style tab Border, radius and Background land on the visible box.
- The root's inline style holds `--bfbe-ba-pos` (from `start`) and `--bfbe-ba-ratio`. As the divider moves, the script rewrites `--bfbe-ba-pos` on the root and `aria-valuetext` on the input; no state class changes.
- `data-bfbe-ba-hover="1"` is on the root when **Follow the pointer** (`hoverMove`) is ticked.
- The after image fills the frame; the before image sits in `.bfbe-ba__clip`, cut at the divider with `clip-path`.
- `.bfbe-ba__range` covers the whole frame at opacity 0 and takes every pointer event; labels, line and handle are `pointer-events: none`. A vertical comparison adds `aria-orientation="vertical"`.
- Keyboard focus on the input outlines `.bfbe-ba__handle` through a sibling selector, which is why the input comes before the handle.
- Labels exist only with `showLabels`; a stored position adds `.bfbe-ba__label--p-top`, `--p-middle`, `--p-bottom` or `--p-custom`.
- The handle holds one of three: `span.bfbe-ba__arrows` (two drawn arrowheads), `span.bfbe-ba__icons` with two `.bfbe-ba__icon` (each `--plain` or `--mirror`), or `span.bfbe-ba__text`.
- Custom properties on the root: `dividerWidth` writes `--bfbe-ba-line`, `dividerColor` writes `--bfbe-ba-line-color` (line and handle disc), `handleSize` writes `--bfbe-ba-handle`, `handleIconSize` writes `--bfbe-ba-icon` (arrows, icons and text alike), `handleIconGap` writes `--bfbe-ba-icon-gap`, `labelOffset` writes `--bfbe-ba-label-offset`.
- `handleBackground`, `handleBorder`, `handleShadow` and `handleIconColor` write to `.bfbe-ba__handle`; the label look controls to `.bfbe-ba__label`; `fit` to `object-fit` on `.bfbe-ba__img`.
- The root has `inline-size: 100%` and `aspect-ratio`, so it fills its parent's width and the height follows. Narrow it with Bricks' **Max. width** (`_widthMax`).
- On a right-to-left page the comparison mirrors: the before image keeps the start side, now the right.
- In the builder only, a side with no image is a `span.bfbe-ba__ph` placeholder panel.

## Wiring to other elements

Stands alone; nothing targets it and it targets nothing.

The script starts every `.bfbe-ba` on the page when it loads, and again after Bricks' AJAX pagination, load page, query results and popup loaded events. A comparison inserted by any other script starts when you call `window.bfbeBeforeAfter()`, which is safe to call again. <!-- src: src/elements/before-after/before-after.js:75-86 -->

## Verified patterns

`id` in `before` and `after` is an attachment id from this site's media library; write the target site's own ids.

A project comparison with its own label words, a typed 4 / 3 frame and the divider a little left of centre. From the demo page `demo-bfb-before-after`. Labels need `showLabels: true`, or both words are dropped.

```json
{
  "name": "bfbe-before-after",
  "settings": {
    "before": { "id": 1930, "size": "full" },
    "after": { "id": 1931, "size": "full" },
    "ratio": "4/3",
    "showLabels": true,
    "labelBefore": "As found",
    "labelAfter": "As finished",
    "start": 45,
    "dividerColor": { "hex": "#6e44ff" }
  }
}
```

A top and bottom comparison, the divider starting at 30%. From the fixture page `fixture-before-after`. With no positions stored, Old sits top left and New bottom left.

```json
{
  "name": "bfbe-before-after",
  "settings": {
    "before": { "id": 22, "size": "full" },
    "after": { "id": 23, "size": "full" },
    "orientation": "vertical",
    "start": 30,
    "showLabels": true,
    "labelBefore": "Old",
    "labelAfter": "New"
  }
}
```

A larger handle with one icon: the right side is the left icon mirrored. From the fixture page `fixture-before-after`. `handleIconSize` and `handleIconGap` size the icons.

```json
{
  "name": "bfbe-before-after",
  "settings": {
    "before": { "id": 22, "size": "full" },
    "after": { "id": 23, "size": "full" },
    "handleSize": "60px",
    "handleIconLeft": { "library": "themify", "icon": "ti-angle-left" },
    "handleIconSize": "14px",
    "handleIconGap": "14px"
  }
}
```

## Gotchas

- **The page draws nothing until both images resolve.** The builder shows a toned placeholder for a missing side, but the page prints no markup at all, root included. <!-- src: plugins/bfb-elements/elements/before-after.php:577-586 -->
- **The frame's shape comes from the first image with an attachment id.** When neither has one (a URL image, or a dynamic tag that returns a URL), the frame falls back to 16 / 9. Type **Aspect ratio** (`ratio`) as digits and a slash (`"4/3"`); `"16:9"` is ignored without a word. <!-- src: plugins/bfb-elements/elements/before-after.php:516-541 -->
- **Fit inside the frame leaves transparent bars.** With `fit: "contain"`, the frame's background shows around an image of other proportions, transparent unless Bricks' Background is set. Where the two images differ in shape, the before side's bars show the after image. <!-- src: src/elements/before-after/before-after.css:35-68, measured in headless Chrome -->
- **Label words need Show labels, even for the slider's name.** With `showLabels` off, `labelBefore` and `labelAfter` are dropped and the range input stays "Compare Before and After". <!-- src: plugins/bfb-elements/elements/before-after.php:159,225,594-603,649 -->
- **Custom position clears every edge.** The distances act only with **Position** `custom` and are dropped otherwise. `labelAfterX` measures from the right. A custom label with no distances sits flush in the top left corner, After included, over the Before label. <!-- src: src/elements/before-after/before-after.css:204, plugins/bfb-elements/elements/before-after.php:178-194, measured -->
- **In a vertical comparison After defaults to bottom.** Setting `labelAfterPosition: "top"` there puts it at top left, exactly on the Before label. <!-- src: src/elements/before-after/before-after.css:190-201, measured -->
- **Text replaces the arrows and does not grow the handle.** A filled **Text** (`handleText`) drops `handleIconLeft`, `handleIconRight` and `handleIconGap`. The handle stays a disc of `handleSize` (44px), so a long word spills out unless the handle grows or `handleIconSize` shrinks. <!-- src: plugins/bfb-elements/elements/before-after.php:398,407,434, src/elements/before-after/before-after.css:101-107,167-172, measured -->
- **One arrow icon serves both sides.** Set only `handleIconLeft` and the right is that icon mirrored; set both and they are used as given. A vertical comparison turns the row 90 degrees, so pick left and right arrows there too. <!-- src: plugins/bfb-elements/elements/before-after.php:681-691, src/elements/before-after/before-after.css:158-165 -->
- **Divider Colour also fills the handle.** `dividerColor` paints the line and the handle disc, while the arrows stay `#111` until **Colour** (`handleIconColor`) is set. A dark divider hides them. <!-- src: src/elements/before-after/before-after.css:113-117, measured -->
- **The root is the frame.** Bricks' own Border, radius and Background write to the visible box, which has a 12px radius by default; there is no separate frame box to style. <!-- src: docs/elements/before-after.md "The root is the frame now", docs/elements/before-after.md "Frame border and Frame background are gone" -->
- **On touch, a top and bottom comparison keeps every swipe.** A left and right one passes vertical swipes to the page; a vertical one does not, so a phone cannot scroll from a swipe that starts on it. Keep it well under a phone screen's height. <!-- src: src/elements/before-after/before-after.css:48-52, measured: root pan-y and range pan-x on a vertical comparison -->
- **Both images load eagerly at the stored size.** Each image is `loading="eager"` at its `size`, `full` when none is stored. In a query loop or a long page of comparisons, store `size: "large"`. <!-- src: plugins/bfb-elements/elements/before-after.php:482-490,555-568 -->

## Never do

- Do not leave `before` or `after` empty: the page renders nothing.
- Do not type `ratio` with a colon or a word (`"16:9"`, `"auto"`); write `"16/9"`.
- Do not set `labelBefore` or `labelAfter` without `showLabels: true`.
- Do not set `labelBeforeX`, `labelBeforeY`, `labelAfterX` or `labelAfterY` without their label's position `custom`, and do not set `custom` without both distances.
- Do not set `labelAfterPosition: "top"` in a vertical comparison.
- Do not set `handleIconLeft`, `handleIconRight` or `handleIconGap` together with `handleText`.
- Do not pair a dark `dividerColor` with the default arrows; set a light `handleIconColor`.
- Do not add `tabindex`, `role` or `aria-*` to the range input, the labels or the handle.
