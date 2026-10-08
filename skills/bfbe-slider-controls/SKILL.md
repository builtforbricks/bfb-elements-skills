---
name: bfbe-slider-controls
description: "Use when adding custom arrows, a slide counter like 3 / 7, a progress bar or thumbnail navigation to Bricks' Slider (Nestable) with BFB Slider Controls (`bfbe-slider-controls`), placed anywhere on the page and bound to the nearest slider or one named by ID. Read before wiring or styling it."
---

# BFB Slider Controls (`bfbe-slider-controls`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-slider-controls.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/slider-controls/

## What it is
One control for Bricks' Slider (Nestable) element, placed anywhere on the page: arrows, a fraction like 3 / 7, a progress bar or thumbnails. Each element is exactly one of those, so you lay a row of them out with Bricks' own containers. It binds to a slider by element ID, or to the nearest slider when the ID is empty.

**Not for:** Not a slider of its own: it drives Bricks' Slider (Nestable) element, not the Slider or the Carousel, and hides itself if it cannot find one. It cannot drive an Advanced Snap Slider, which carries its own buttons and dots.

**Costs a page:** CSS 0.71 KB, JS 1.44 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** no · **In a query loop:** no · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Slider (`bfbeTarget`)
- `target` (text) **Slider element ID**: placeholder The nearest slider. The ID of the Bricks Slider (Nestable) to control: it drives that element, not the Slider or the Carousel. Empty, the default, takes the nearest slider, found by walking out from this element. With no slider found, it hides itself on the page.
- `part` (select) **Control**: options: `arrows` Both arrows (default), `prev` Previous arrow, `next` Next arrow, `fraction` Fraction (3 / 7), `progress` Progress bar, `thumbs` Thumbnails. Choose Both arrows, the default, Previous arrow, Next arrow, Fraction (3 / 7), Progress bar or Thumbnails. Each element is one control, and the groups below follow your choice.

### Arrows (`bfbeArrows`)
The whole group shows only when `part` is not `fraction` or `progress` or `thumbs`.
- `prevLabel` (text) **Previous label**: placeholder Previous slide; dynamic data accepted; only when `part` is not `next` or `fraction` or `progress` or `thumbs`. The name screen readers read for the previous button, Previous slide by default. It takes dynamic data.
- `nextLabel` (text) **Next label**: placeholder Next slide; dynamic data accepted; only when `part` is not `prev` or `fraction` or `progress` or `thumbs`. The same for the next button, Next slide by default. It takes dynamic data too.
- `prevIcon` (icon) **Previous icon**: only when `part` is not `next` or `fraction` or `progress` or `thumbs`. Pick an icon of your own in place of the drawn chevron.
- `nextIcon` (icon) **Next icon**: only when `part` is not `prev` or `fraction` or `progress` or `thumbs`. The same for the next button. An arrow with no icon of its own draws a simple chevron.
Styling, in the schema file: `gap`, `arrowSize`, `arrowColor`, `arrowBackground`, `arrowBackgroundHover`, `arrowColorHover`, `arrowBorder`.

### Progress bar (`bfbeBar`)
The whole group shows only when `part` is `progress`.
Styling only, every key in the schema file: `barHeight`, `barColor`, `barTrack`, `barBorder`.

### Fraction (`bfbeFraction`)
The whole group shows only when `part` is `fraction`.
Styling only, every key in the schema file: `fractionTypography`.

### Thumbnails (`bfbeThumbs`)
The whole group shows only when `part` is `thumbs`.
Styling only, every key in the schema file: `thumbsAlign`, `thumbSize`, `thumbBorder`, `thumbGap`, `thumbDim`, `thumbActive`.

### Motion (`bfbeMotion`)
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS. The curve those changes follow, Snappy unless set.
Styling, in the schema file: `duration`, `easingCustom`.

## What it guarantees for accessibility (do not undo)
- Every arrow and thumbnail is a real button that names the slider it controls through aria-controls, and the arrow names are editable.
- At the start and end of a slider that neither loops nor rewinds, the matching arrow gets aria-disabled and ignores clicks.
- The progress bar is a progressbar with aria-valuenow and a Slide progress label, and the fraction is hidden from assistive technology.
- Each thumbnail is named Go to slide with its number, and the current one carries aria-current.
- The bar's fill and the thumbnails' fades run on the shared motion duration, which reduced motion sets to zero.
<!-- bfbe:generated:end -->

## Rendered DOM

One root per element, `div.bfbe-sc` with `bfbe-sc--<part>` from **Control** `part`. The fixture's parts, bound and moved to slide two:

```html
<div id="brxe-5dab23" class="brxe-bfbe-slider-controls bfbe-sc bfbe-sc--arrows" data-bfbe-target="demo-slider">
  <button type="button" class="bfbe-sc__btn bfbe-sc__btn--prev" data-bfbe-go="prev" aria-controls="demo-slider"
          aria-label="Previous slide" aria-disabled="false"><svg class="bfbe-sc__icon bfbe-sc__icon--drawn" aria-hidden="true">...</svg></button>
  <button type="button" class="bfbe-sc__btn bfbe-sc__btn--next" data-bfbe-go="next" aria-controls="demo-slider" ...>...</button>
</div>
<div class="bfbe-sc bfbe-sc--fraction"><span class="bfbe-sc__fraction" aria-hidden="true"><span class="bfbe-sc__now">2</span> / <span class="bfbe-sc__total">3</span></span></div>
<div class="bfbe-sc bfbe-sc--progress"><div class="bfbe-sc__progress" role="progressbar" aria-valuemin="0" aria-valuemax="100"
     aria-valuenow="50" aria-label="Slide progress"><span class="bfbe-sc__fill" style="inline-size: 50%"></span></div></div>
<div class="bfbe-sc bfbe-sc--thumbs" data-bfbe-slide="Go to slide %d"><div class="bfbe-sc__thumbs">
  <button type="button" class="bfbe-sc__thumb" aria-controls="demo-slider" aria-label="Go to slide 2" aria-current="true"><img src="..." alt="" loading="lazy"></button>
</div></div>
```

- `data-bfbe-target` is written when **Slider element ID** `target` is set, a leading `#` stripped. With it empty, the script writes `aria-controls` once it has found a slider.
- The script sets: `aria-disabled` on each arrow, `aria-valuenow` and the fill's inline `inline-size` on the bar, the text of `.bfbe-sc__now` and `.bfbe-sc__total`, `aria-current="true"` on the current thumbnail, and `is-unbound` (`display: none`) on a root that found no slider.
- The thumbnail buttons are made by the script, one per slide that is not a Splide clone; until it runs, `.bfbe-sc__thumbs` is empty.
- A chosen **Previous icon** `prevIcon` or **Next icon** `nextIcon` replaces the drawn chevron and keeps its own fill; the drawn one alone carries `bfbe-sc__icon--drawn`.
- The root is a wrapping flex row. `.bfbe-sc--progress` and `.bfbe-sc--thumbs` stretch across their container; `.bfbe-sc__progress` is `flex: 1 1 80px`.
- Where controls write: `gap` to the root of the pair alone (`&.bfbe-sc--arrows`); `arrowSize` to `--bfbe-sc-btn`; `arrowColor`, `arrowBackground`, `arrowBorder` to `.bfbe-sc__btn`, the two hover controls to its `:hover` and `:focus-visible`; `barHeight`, `barColor` to `--bfbe-sc-bar`, `--bfbe-sc-bar-color`; `barTrack`, `barBorder` to `.bfbe-sc__progress`; `fractionTypography` to `.bfbe-sc__fraction`; `thumbsAlign`, `thumbGap` to `.bfbe-sc__thumbs`; `thumbBorder` to `.bfbe-sc__thumb`; `thumbSize`, `thumbDim`, `thumbActive` to `--bfbe-sc-thumb`, `--bfbe-sc-thumb-dim`, `--bfbe-sc-thumb-on`; `duration`, `easing` to `--bfbe-duration`, `--bfbe-ease`.

## Wiring to other elements

- **What it drives.** Bricks' **Slider (Nestable)** (`slider-nested`): the script finds its `.splide` root and drives the Splide instance Bricks keeps in `window.bricksData.splideInstances` under the slider's `data-script-id`.
- **What it cannot drive.** Bricks' Slider and Carousel, and BFB Advanced Snap Slider (`bfbe-snap-slider`), which has no Splide. The snap slider draws its own buttons, counter, dots and bar: switch on its `arrows`, `counter`, `dots` or `progress` (skill `bfbe-snap-slider`).
- **The nearest slider, by default.** With `target` empty, the control walks out from itself one ancestor at a time and binds to the first `.splide` that ancestor holds. Put the slider and its controls in one block; two such blocks on a page each find their own.
- **A named slider.** `target` takes an HTML id, never a class or a selector: the slider's `id`, which is `brxe-` and its element id unless it has a CSS ID. The id of a block holding a slider also works: the first slider inside it is taken. A named ID wins over a nearer slider.
- **Why nearest first.** It has no class targeting. Component instances share ids, and a section inserted twice carries its ids twice; `getElementById` returns the first, so every copy would drive the first slider. The nearest search gives each copy its own. To style several controls alike, use a class in `_cssClasses`, not `_cssId`.
- **One slider, many controls.** Each element binds on its own, and a press on one pair moves every fraction, bar and thumbnail strip bound to that slider. A row of them is a Bricks `block` with `_direction: "row"`; arrows apart are `part: "prev"` and `part: "next"` in a block with `_justifyContent: "space-between"`.
- **What it shows.** `part`: `arrows` (the default), `prev`, `next`, `fraction`, `progress`, `thumbs`. There is no dots part: for dots, switch on the slider's own **Pagination** (`pagination`), or use thumbnails.
- **Re-running.** `window.bfbeSliderControls()` binds every `.bfbe-sc` again; the script calls it after `bricks/ajax/pagination/completed`, `bricks/ajax/load_page/completed`, `bricks/ajax/query_result/displayed` and `bricks/ajax/popup/loaded`.

## Verified patterns

**A counter, the pair and a bar beside the slider, no ID.** From the demo page `demo-bfb-slider-controls` (Rye & Stone): the controls sit in the words column, the slider in the next, and they find it through the grid they share. `_flexGrow` lets the bar fill the row. The demo's section is dark: its white arrow colours and translucent backgrounds are left out, and its photo slides are trimmed to words.

```json
{
  "name": "block",
  "settings": {"_display": "grid", "_gridTemplateColumns": "minmax(0, 0.8fr) minmax(0, 1.2fr)", "_gridTemplateColumns:mobile_landscape": "1fr", "_columnGap": "32px", "_rowGap": "32px"},
  "children": [
    {"name": "block", "settings": {"_justifyContent": "space-between", "_rowGap": "32px"}, "children": [
      {"name": "heading", "settings": {"text": "Three rooms, at three stages", "tag": "h2"}},
      {"name": "block", "settings": {"_direction": "row", "_alignItems": "center", "_columnGap": "8px"}, "children": [
        {"name": "bfbe-slider-controls", "settings": {"part": "fraction", "fractionTypography": {"color": {"hex": "#98a2b3"}, "font-size": "14px", "font-weight": "600"}}},
        {"name": "bfbe-slider-controls", "settings": {"part": "arrows", "arrowSize": "52px", "arrowBorder": {"radius": {"top": 999, "right": 999, "bottom": 999, "left": 999}}}},
        {"name": "bfbe-slider-controls", "settings": {"part": "progress", "barColor": {"hex": "#6e44ff"}, "barHeight": "3px", "_flexGrow": "1"}}
      ]}
    ]},
    {"name": "slider-nested", "settings": {"height": "460px"}, "children": [
      {"name": "block", "settings": {}, "children": [{"name": "heading", "settings": {"text": "Back to the lime", "tag": "h3"}}, {"name": "text-basic", "settings": {"text": "Every later layer came off.", "tag": "p"}}]},
      {"name": "block", "settings": {}, "children": [{"name": "heading", "settings": {"text": "Second fix", "tag": "h3"}}, {"name": "text-basic", "settings": {"text": "Studwork up, rooflight in.", "tag": "p"}}]},
      {"name": "block", "settings": {}, "children": [{"name": "heading", "settings": {"text": "The stair, finished", "tag": "h3"}}, {"name": "text-basic", "settings": {"text": "One continuous soffit.", "tag": "p"}}]}
    ]}
  ]
}
```

**Thumbnails under a slider.** From the fixture page `fixture-slider-controls`, where the strip names the slider by ID; here it shares the slider's block instead. Each thumbnail copies its slide's image, and slide three has none, so its thumbnail reads 3. The image ids 22 and 23 are the demo site's media: use the target site's own attachment ids and URLs. The development site's addresses are replaced with `https://example.com/`.

```json
{
  "name": "block",
  "settings": {"_rowGap": "16px"},
  "children": [
    {"name": "slider-nested", "settings": {}, "children": [
      {"name": "block", "settings": {}, "children": [{"name": "heading", "settings": {"text": "Slide one", "tag": "h3"}}, {"name": "image", "settings": {"image": {"id": 22, "filename": "bfbe-before.png", "size": "medium", "url": "https://example.com/wp-content/uploads/2026/09/bfbe-before-300x188.png", "full": "https://example.com/wp-content/uploads/2026/09/bfbe-before.png"}}}]},
      {"name": "block", "settings": {}, "children": [{"name": "heading", "settings": {"text": "Slide two", "tag": "h3"}}, {"name": "image", "settings": {"image": {"id": 23, "filename": "bfbe-after.png", "size": "medium", "url": "https://example.com/wp-content/uploads/2026/09/bfbe-after-300x188.png", "full": "https://example.com/wp-content/uploads/2026/09/bfbe-after.png"}}}]},
      {"name": "block", "settings": {}, "children": [{"name": "heading", "settings": {"text": "Slide three", "tag": "h3"}}]}
    ]},
    {"name": "bfbe-slider-controls", "settings": {"part": "thumbs", "thumbsAlign": "center"}}
  ]
}
```

**A styled pair aimed at a slider elsewhere.** From the fixture page `fixture-slider-controls`: 52px buttons, 16px apart, white on blue. `demo-slider` is the fixture slider's CSS ID; on a site, put the slider's HTML id, `brxe-` and its element id. `arrowBackground` is a Background control, so its colour sits inside `{"color": ...}`.

```json
{
  "name": "bfbe-slider-controls",
  "settings": {"target": "demo-slider", "part": "arrows", "arrowSize": "52px", "gap": "16px", "arrowBackground": {"color": {"hex": "#1d4ed8"}}, "arrowColor": {"hex": "#ffffff"}}
}
```

## Gotchas

- **Nearest can be far.** The walk goes up to `<body>`, so a control with no `target` binds to a nestable slider wherever one is on the page, even in another section, rather than hiding. <!-- src: src/elements/slider-controls/slider-controls.js:14-20 -->
- **Two sliders in one block: the first wins.** An ancestor answers with its first `.splide` in page order, so controls sharing a block with two sliders all drive the first. <!-- src: src/elements/slider-controls/slider-controls.js:15-17 -->
- **A named ID never falls back.** With `target` set, the control looks there alone; a wrong ID leaves it unbound beside a slider it could have found. <!-- src: src/elements/slider-controls/slider-controls.js:24-28; dev/fixtures/pro-pack.php:307; measured on fixture-slider-controls-nearest 2026-10-08: the third set named near-one and drove it, not its neighbour -->
- **No slider: visible for five seconds, then gone.** The script retries 50 times at 100 ms, then adds `is-unbound`, which hides the root. The builder canvas never hides it. <!-- src: src/elements/slider-controls/slider-controls.js:8, :52; src/elements/slider-controls/slider-controls.css:53; docs/elements/slider-controls.md "⚑ The retries run for five seconds"; measured on fixture-slider-controls-alone 2026-10-08: display flex at 1.5 s, none at 6.5 s -->
- **Beside a snap slider it finds the wrong slider.** It looks for `.splide`, which Bricks' Slider (Nestable) alone draws, so next to a `bfbe-snap-slider` it binds to a nestable slider elsewhere on the page or hides. <!-- src: src/elements/slider-controls/slider-controls.js:16, :27; bricks 2.3.10 includes/elements: splide appears in slider-nested.php alone -->
- **The slider's own arrows and dots turn on with any value.** Bricks reads `arrows` and `pagination` with `isset()`, so `"arrows": false` shows them. Leave both keys out of the slider's settings. <!-- src: bricks 2.3.10 includes/elements/slider-nested.php:1239, :1286, :1377 (same in 2.4-beta3); dev/fixtures/pro-pack.php:280 -->
- **The default slider loops, so the arrows never dim.** Bricks' `type` defaults to `loop`, and `rewind` counts for the other types alone. An arrow gets `aria-disabled="true"` at an end with `type: "slide"` or `"fade"` and no `rewind`. <!-- src: bricks 2.3.10 includes/elements/slider-nested.php:1220, :1299; src/elements/slider-controls/slider-controls.js:69, :91; measured on fixture-slider-controls 2026-10-08: type loop, both arrows "false" at slide one, previous went to 3 / 3 -->
- **Several slides a page: the fraction stops short.** On a slider that does not loop, the last position is slides minus `perPage`: the bar reaches 100% there, and 7 slides at 3 a page end at 5 / 7. <!-- src: src/elements/slider-controls/slider-controls.js:79-82; measured 2026-10-08 on a 7-slide Splide, type slide, perPage 3, bound by the script: 5 / 7, aria-valuenow 100, next aria-disabled -->
- **Thumbnails need an `<img>` in each slide.** The script copies each slide's first image (its `data-src` when lazy-loaded); a slide whose picture is a background, or that has none, shows its number. <!-- src: src/elements/slider-controls/slider-controls.js:110-127; measured on fixture-slider-controls 2026-10-08: thumbnails img, img, "3" -->
- **In a row, the bar needs Flex grow.** The bar stretches across a column, but in a row block it stays 80px wide until it has `_flexGrow: "1"`. <!-- src: src/elements/slider-controls/slider-controls.css:17, :43; docs/elements/slider-controls.md "Round 402"; measured on fixture-slider-controls 2026-10-08: 949px with flex-grow 1, 80px without -->
- **The arrow backgrounds need a colour object.** `arrowBackground` and `arrowBackgroundHover` are Background controls: a bare `{"hex": "..."}` is stored and writes no CSS. `arrowColor`, `barColor`, `barTrack` and `thumbActive` are Color controls and take `{"hex": "..."}`. <!-- src: plugins/bfb-elements-pro/elements/slider-controls.php:175-194; measured 2026-10-08 with Assets::generate_inline_css_from_element: wrapped wrote background-color on .bfbe-sc__btn, bare wrote nothing -->
- **Motion is not the slide speed.** **Duration** `duration` and **Easing** `easing` time the bar's fill, the thumbnails' fades and the arrows' hover; the slides travel at the slider's own `speed`. <!-- src: src/elements/slider-controls/slider-controls.css:32, :44, :47; plugins/bfb-elements/includes/abstract-element.php:1025, :1060; bricks 2.3.10 includes/elements/slider-nested.php:1279 -->

## Never do

- Do not set `target` when the controls can share a block with their slider; leave it empty.
- Do not set `target` inside a component or a section that may appear twice on a page; every copy would drive the first slider.
- Do not leave two sliders in a block whose controls name no slider; give each slider and its controls a block of their own.
- Do not aim it at Bricks' Slider, Carousel or a `bfbe-snap-slider`; switch on the snap slider's own `arrows`, `counter`, `dots` or `progress`.
- Do not set the slider's `arrows` or `pagination` to `false`; leave the keys out.
- Do not write `arrowBackground` or `arrowBackgroundHover` as a bare `{"hex": ...}`; wrap it in `{"color": ...}`.
- Do not leave a progress bar in a row block without `_flexGrow: "1"`.
- Do not add `disabled` to an arrow or overwrite its `aria-controls`; the script sets `aria-disabled` and `aria-controls` itself.
