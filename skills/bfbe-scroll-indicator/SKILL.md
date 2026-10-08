---
name: bfbe-scroll-indicator
description: "Use when building a reading progress bar, a progress ring, a back-to-top button that fills as the page scrolls, or a bar of dots linking to the page's sections, with BFB Scroll Indicator (`bfbe-scroll-indicator`). Read before writing its settings."
---

# BFB Scroll Indicator (`bfbe-scroll-indicator`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-scroll-indicator.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/scroll-indicator/

## What it is
Shows how far a visitor has scrolled, as a bar or a ring, fixed to the top or bottom or placed in the flow. A bar can also mark sections: each dot is a link to its section, named after the section's heading, and the current one is flagged. The progress value is exposed as a progressbar role that updates with the scroll.

**Not for:** It reports progress of the page's own scroll, so a scrolling panel inside the page does not drive it. A reading bar for one article therefore counts the header, footer and everything else on the page too.

**Costs a page:** CSS 1.60 KB, JS 1.73 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** no · **In a query loop:** no · **Dynamic data:** no · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Indicator (`bfbeShape`)
- `shape` (select) **Shape**: options: `bar` Bar (default), `ring` Ring. Bar is the default. Ring draws a circular indicator with an optional percentage or a scroll-to-top icon in the middle.
- `position` (select) **Position**: options: `top` Fixed to the top (default), `bottom` Fixed to the bottom, `inline` Where it is placed. Fixed to the top is the default. Choose Fixed to the bottom, or Where it is placed to sit in the page flow.
- `percent` (checkbox) **Show the percentage**: only when `shape` is `ring` and `centerIcon` is not set. For the Ring, tick it to print how far the page has scrolled in the middle of the ring.
- `centerIcon` (checkbox) **Show an icon instead**: only when `shape` is `ring`. For the Ring, tick it to swap the percentage for a button with a caret that scrolls the page to the top.
- `appearAfter` (number) **Show after scrolling (px)**: only when `shape` is `ring` and `position` is not `inline`. For a fixed Ring, how far the page scrolls before the ring appears, 0 by default.
- `offBelow` (select) **Hide below**: options: `never` Never (default), `480` 480px, `640` 640px, `768` 768px, `992` 992px. Never by default. Choose 480, 640, 768 or 992px to drop the indicator on narrow screens.

### Sections (`bfbeSections`)
The whole group shows only when `shape` is not `ring`.
- `sections` (checkbox) **Mark the sections**: only when `shape` is not `ring`. For the Bar, adds a dot for each section found by Which elements. Each dot links to its section.
- `sectionSelector` (text) **Which elements**: placeholder main > .brxe-section; only when `shape` is not `ring` and `sections` is set. A CSS selector for the sections, main > .brxe-section by default. Sections without an id are given one.
- `labels` (checkbox) **Show labels**: only when `shape` is not `ring` and `sections` is set. Shows each dot's name as text. It comes from the section's heading, or from a data-bfbe-label attribute, which takes priority.
- `labelPlace` (select) **Labels**: options: `auto` Below, or above a bottom bar (default), `below` Below, `above` Above, `hover` On hover, over each dot; only when `shape` is not `ring` and `sections` is set and `labels` is set. Below, or above a bottom bar, is the default. The other choices are Below, Above and On hover, over each dot.
Styling, in the schema file: `labelPadding`, `labelShadow`.

### Dots (`bfbeDots`)
The whole group shows only when `shape` is not `ring` and `sections` is set.
Styling only, every key in the schema file: `markerSize`, `markerColor`, `markerCurrent`, `markerDone`, `markerHover`, `markerGrow`, `markerBorder`, `markerShadow`.

### Look (`bfbeLook`)
- `ringTrack` (select) **Line**: options: `solid` Solid (default), `dashed` Dashed, `dotted` Dotted; only when `shape` is `ring`
- `ringCaps` (select) **Fill ends**: options: `round` Round (default), `butt` Flat; writes CSS; only when `shape` is `ring`
- `align` (justify-content) **Alignment**: only when `shape` is not `ring` and `width` is set
- `icon` (icon) **Icon**: only when `shape` is `ring` and `centerIcon` is set. With Show an icon instead, pick your own icon in place of the caret.
Styling, in the schema file: `offset`, `percentBackground`, `percentPadding`, `percentBorder`, `percentTypography`, `thickness`, `color`, `track`, `ringSize`, `barBorder`, `fillBorder`, `width`, `iconSize`, `iconColor`, `labelBackground`, `labelBorder`, `labelGap`, `labelTypography`.

### Motion (`bfbeMotion`)
Styling only, every key in the schema file: `smoothing`.

## What it guarantees for accessibility (do not undo)
- The bar or ring has role progressbar with the name Page progress, and aria-valuenow updates from 0 to 100 as the page scrolls.
- Section dots are links in an ordered list named Sections, each named by its heading, and the current one carries aria-current location.
- The ring's icon is a real button named Scroll to top, and the percentage text is hidden from assistive technology.
- With reduced motion requested, Scroll to top jumps straight up and Smoothing is set to zero.
<!-- bfbe:generated:end -->

## Rendered DOM

A `div.bfbe-si` root (with Bricks' `brxe-bfbe-scroll-indicator` and `id="brxe-<id>"`). The script builds the section list after load.

```html
<div id="brxe-503d0d" class="brxe-bfbe-scroll-indicator bfbe-si bfbe-si--bar bfbe-si--top bfbe-si--labels-hover"
     data-bfbe-sections=".rl-part" data-bfbe-nav-label="Sections" data-bfbe-labels="1" style="--bfbe-si-p: 0.4200">
  <div class="bfbe-si__track" role="progressbar" aria-valuemin="0" aria-valuemax="100" aria-valuenow="42" aria-label="Page progress">
    <div class="bfbe-si__fill"></div>
  </div>
  <ol class="bfbe-si__sections" aria-label="Sections">
    <li class="bfbe-si__marker bfbe-si__marker--done bfbe-si__marker--current" style="--bfbe-si-at: 31.20%; --bfbe-si-atn: 0.3120">
      <a class="bfbe-si__dot" href="#brxe-e214bf" aria-label="Part one" aria-current="location">
        <span class="bfbe-si__dot-fill"></span><span class="bfbe-si__label">Part one</span>
      </a>
    </li>
  </ol>
</div>

<div class="brxe-bfbe-scroll-indicator bfbe-si bfbe-si--ring bfbe-si--bottom is-visible" data-bfbe-appear="300">
  <svg class="bfbe-si__svg" viewBox="0 0 100 100" role="progressbar" aria-label="Page progress" ...>
    <circle class="bfbe-si__track" .../><circle class="bfbe-si__fill" pathLength="1" .../>
  </svg>
  <button type="button" class="bfbe-si__icon" aria-label="Scroll to top"><i aria-hidden="true" class="ti-angle-up"></i></button>
</div>
```

- With `percent` and no `centerIcon`, a `span.bfbe-si__percent` (`aria-hidden="true"`, text `42%`) takes the button's place.
- **The progressbar role** sits on `.bfbe-si__track` or the `svg`, never the root: a progressbar's subtree is presentational, which would hide the section links.
- **Root classes**: `bfbe-si--bar` or `--ring`; `--top`, `--bottom` or `--inline`; `--off-480|640|768|992` from `offBelow`; `--track-dashed|dotted` from `ringTrack`; `--align-start|end` from `align` (centre writes none); `--labels-below|above|hover` from `labelPlace` (auto writes none); `--canvas` in the builder.
- **Script state**: `--bfbe-si-p` (0 to 1) inline on the root drives both fills, and `aria-valuenow` and the percent text follow it. A ring with `data-bfbe-appear` gains `is-visible` once the page has scrolled that far.
- **Markers**: `bfbe-si__marker--done` once the fill reaches a dot, `--current` on the last one reached, whose link carries `aria-current="location"`.
- **Fills**: the bar's `.bfbe-si__fill` grows by `inline-size`, not a transform; the ring's is a `stroke-dashoffset` on a `pathLength="1"` circle.
- **Placement**: fixed is `position: fixed` at `z-index: 9990`, a ring 16px (`--bfbe-gap`) in from the inline-end corner; inline is `position: relative` at `z-index: 50`.
- **Custom properties on the root**: `thickness`, `color`, `track`, `ringSize`, `width`, `offset`, `ringCaps`, `smoothing`, `markerSize`, `markerColor`, `markerDone`, `markerHover`, `markerGrow`, `labelBackground`, `labelGap`.
- **Parts**: `barBorder` and `fillBorder` to the bar's `.bfbe-si__track` and `.bfbe-si__fill`; `percent*` to `.bfbe-si__percent`; `iconSize`, `iconColor` to `.bfbe-si__icon`; `labelBorder`, `labelTypography`, `labelPadding`, `labelShadow` to `.bfbe-si__label`; `markerBorder`, `markerShadow` to `.bfbe-si__dot-fill`; `markerCurrent` to the current dot's `.bfbe-si__dot-fill` background. Bricks' Style tab lands on the root.

## Wiring to other elements

The indicator points at sections; nothing points at it.

- **Sections by selector**: **Which elements** (`sectionSelector`) is a CSS selector run over the whole document, with `sections: true` on a bar. Give each section a class in `_cssClasses` and select that class (`".rl-part"`); never an id or `_cssId`, since component instances share ids.
- **A dot's name**: put `data-bfbe-label` on the section through `_attributes`, `[{"name": "data-bfbe-label", "value": "Part one"}]`. It wins over the section's heading.
- **Headings as stops**: a selector that matches headings (`"main h2"`) makes each heading a stop, named by its own text.
- **Anchors**: each dot links to `#<the section's id>`. Bricks gives every element `brxe-<id>` on the page; a matched node with no id gets `bfbe-section-1`, `-2` and so on, numbered across every indicator on the page, so do not link to those from elsewhere.
- **Sticky header**: a dot sits where the page lands when it is followed, after the root's `scroll-padding-top` and the section's `scroll-margin-top`. To keep a top bar clear of a sticky header, set **Offset** (`offset`) to the header's height.
- **Scroll to top**: the ring's button scrolls the window to the top and touches nothing else.
- Several indicators can share a page; each builds its own dots from its own selector.

## Verified patterns

**Reading bar with section dots.** From the demo page `/demo-bfb-scroll-indicator/`. A bar fixed to the top marks three parts of an article: `sectionSelector: ".rl-part"` finds them and `labelPlace: "hover"` turns each name into a tooltip on hover and focus. Unreached dots wear the track's colour and passed dots the fill's (`markerColor` = `track`, `markerDone` and `markerCurrent` = `color`), so the bar reads as one line; `labelShadow` at zero drops the shadow hover labels carry by default.

```json
{
  "name": "bfbe-scroll-indicator",
  "settings": {
    "position": "top",
    "sections": true,
    "labels": true,
    "sectionSelector": ".rl-part",
    "labelPlace": "hover",
    "thickness": "4px",
    "color": { "hex": "#6e44ff" },
    "track": { "raw": "#f7f8fa" },
    "markerColor": { "raw": "#f7f8fa" },
    "markerDone": { "raw": "#6e44ff" },
    "markerCurrent": { "raw": "#6e44ff" },
    "labelBackground": { "raw": "#6e44ff" },
    "labelTypography": { "color": { "raw": "hsl(0, 0%, 100%)" }, "font-size": "14" },
    "labelPadding": { "top": 12, "right": 12, "bottom": 12, "left": 12 },
    "labelBorder": { "radius": { "top": "4", "right": "4", "bottom": "4", "left": "4" } },
    "labelShadow": { "values": { "offsetX": "0", "offsetY": "0", "blur": "0", "spread": "0" } },
    "labelGap": "12"
  }
}
```

Each part it marks, on the same page, is a `block` carrying the class and the dot's name:

```json
{
  "name": "block",
  "settings": {
    "_cssClasses": "rl-part",
    "_attributes": [{ "name": "data-bfbe-label", "value": "Part one" }]
  },
  "children": [{ "name": "heading", "settings": { "tag": "h3", "text": "What the whiteboard is actually doing" } }]
}
```

**Back-to-top ring that appears after scrolling.** From the fixture page `fixture-scroll-indicator-ring`. A ring fixed to the bottom corner whose centre is a Scroll to top button (`centerIcon`, here with an icon of its own in `icon`); `appearAfter: 300` keeps it hidden, and out of the tab order, until the page has scrolled 300px.

```json
{
  "name": "bfbe-scroll-indicator",
  "settings": {
    "shape": "ring",
    "position": "bottom",
    "centerIcon": true,
    "appearAfter": 300,
    "icon": { "library": "ionicons", "icon": "ion-md-arrow-round-up" }
  }
}
```

**Ring with the percentage, in the flow.** From `fixture-scroll-indicator-ring` (and `fixture-universals`). A ring that sits where it is placed, in a sidebar for example, printing how far the page has scrolled; `ringSize` sets its box.

```json
{
  "name": "bfbe-scroll-indicator",
  "settings": { "shape": "ring", "position": "inline", "percent": true, "ringSize": "72px" }
}
```

## Gotchas

- **The default selector misses nested sections.** Without `sectionSelector` the script looks for `main > .brxe-section`, Sections placed straight on the page, and finds none inside a block, a container or any other wrapper. <!-- src: plugins/bfb-elements/elements/scroll-indicator.php:620 -->
- **No match draws nothing, and says nothing.** A selector that matches nothing, or does not parse, leaves the bar without a `.bfbe-si__sections` list and raises no error. <!-- src: src/elements/scroll-indicator/scroll-indicator.js:43-46, 97 -->
- **A dot's name comes from the section, in this order**: its `data-bfbe-label`; the section itself if it is a heading; its first `h1` to `h4` (an `h5` or `h6` is not read); else "Sections 1", "Sections 2". <!-- src: src/elements/scroll-indicator/scroll-indicator.js:105-108 -->
- **The current dot looks like every other passed dot** until **Current section colour** (`markerCurrent`) is set. Current means the last dot the fill has reached. <!-- src: plugins/bfb-elements/elements/scroll-indicator.php:489-499 -->
- **Passed colour defaults to `Canvas`**, the browser's own page colour, not the site's background. On a dark or tinted page a passed dot shows as a pale notch in the fill; set `markerDone`. <!-- src: src/elements/scroll-indicator/scroll-indicator.css:16-18 -->
- **Labels rest at 70% opacity** and go to full on hover, on focus and for the current section. No control changes the 70%. <!-- src: src/elements/scroll-indicator/scroll-indicator.css:125, 134 -->
- **A fixed bar's labels hang over the page**, below a top bar and above a bottom one. A bar placed inline keeps room for them as margin; hover labels take no room in either. <!-- src: src/elements/scroll-indicator/scroll-indicator.css:90-92; src/elements/scroll-indicator/scroll-indicator.js:82-88 -->
- **The builder canvas never fixes the indicator.** It sits where it is placed in the structure, and a ring with Show after scrolling is always shown there; check both on the page. <!-- src: src/elements/scroll-indicator/scroll-indicator.css:68-73, 141-145 -->
- **Logged in, a top bar sits below WordPress's admin bar**: 32px down, 46px under 783px, back at the edge under 601px. A visitor sees it at the edge. <!-- src: src/elements/scroll-indicator/scroll-indicator.css:77-86 -->
- **A transformed ancestor unfixes it.** `position: fixed` resolves against an ancestor with a `transform`, `filter` or `backdrop-filter`, so the bar or ring moves with that ancestor instead of staying on the window. <!-- src: src/elements/scroll-indicator/scroll-indicator.css:76 -->
- **On a ring, Thickness scales with Size.** The line is drawn in the ring's 100-unit box at twice `thickness`, so the default 4px is about 4.5px on the 56px ring and 9px on a 112px one. <!-- src: src/elements/scroll-indicator/scroll-indicator.css:54-58; measured on fixture-scroll-indicator-ring, stroke-width 8 in a 56px svg -->
- **A ring's outline is Bricks' own Border** (`_border`), drawn as a circle because the root is round; a radius set there squares it. <!-- src: src/elements/scroll-indicator/scroll-indicator.css:46-48; docs/elements/scroll-indicator.md "Border around the ring is gone from the panel" -->

## Never do

- Do not select sections by id or `_cssId`; set a class in `_cssClasses` and put it in `sectionSelector`.
- Do not keep the default `sectionSelector` when the sections are not direct children of `main`.
- Do not place a fixed bar or ring inside an element with a `transform`, `filter` or `backdrop-filter`.
- Do not judge the fixed position or `appearAfter` from the builder canvas, or a top bar's position from a logged-in page.
- Do not add `role`, `aria-*` or `tabindex` to the root through `_attributes`; the progressbar role belongs on the track or `svg`.
- Do not set a radius on a ring's `_border`.
- Do not leave `markerCurrent` empty when the current section has to stand out.
