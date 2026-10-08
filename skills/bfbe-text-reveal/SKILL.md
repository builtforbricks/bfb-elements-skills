---
name: bfbe-text-reveal
description: "Use when placing, wiring or styling BFB Advanced Text Reveal (`bfbe-text-reveal`): text split into words, letters or lines and driven by one of five modes: reveal, light up, highlight, move or count up. Read before writing its settings."
---

# BFB Advanced Text Reveal (`bfbe-text-reveal`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-text-reveal.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/text-reveal/

## What it is
Text split into words, letters or lines and driven by one of five modes: reveal, light up, highlight, move or count up. Scroll-driven modes use CSS scroll-driven animations where the browser has them, and a small script supplies the progress where it does not. The split parts are hidden from assistive technology, and one plain copy of the whole text is read instead.

**Not for:** Not for formatted copy: the Text control is plain text and mark is the one tag that survives, so links, bold and line breaks are lost. Splitting by Letters wraps every character in its own span, so long passages read better split by Words or Lines.

**Costs a page:** CSS 1.29 KB, JS 1.73 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** no · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** no · **Reduced motion:** yes

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Bricks' query loop (`hasLoop`, `query`); Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Text (`bfbeText`)
- `tag` (select) **HTML tag**: options: `h1` h1, `h2` h2 (default), `h3` h3, `h4` h4, `h5` h5, `h6` h6, `p` p, `div` div. Pick h1 to h6, p or div. It is h2 by default, so the animated text keeps the heading level your page needs.
- `text` (textarea) **Text**: dynamic data accepted. The words to animate. They accept dynamic data. Wrap words in mark tags to mark them for a highlight or their own look, and keep the rest plain, because other tags are removed.
- `split` (select) **Split by**: options: `words` Words (default), `letters` Letters, `lines` Lines; only when `mode` is not `count`. Choose Words, the default, Letters or Lines. Lines groups the words by measuring where the browser breaks each line.

### Mode (`bfbeMode`)
- `mode` (select) **Mode**: options: `view` Reveal on view (default), `scroll` Light up with scroll, `highlight` Highlight on scroll, `kinetic` Move with scroll, `count` Count up. Choose Reveal on view, the default, Light up with scroll, Highlight on scroll, Move with scroll or Count up. The other groups show the controls for the mode you choose.

### Reveal (`bfbeReveal`)
The whole group shows only when `mode` is `` or `view` or `highlight`.
- `effect` (select) **Effect**: options: `up` Fade up (default), `down` Fade down, `blur` Blur in, `scale` Scale in, `left` Slide from the left, `right` Slide from the right, `curtain` Curtain; only when `mode` is `` or `view`. Pick Fade up, the default, Fade down, Blur in, Scale in, Slide from the left, Slide from the right or Curtain.
- `trigger` (select) **Play**: options: `view` When it comes into view (default), `load` On page load; only when `mode` is `` or `view`. When it comes into view, the default, or On page load.
- `once` (checkbox) **Play once**: only when `mode` is `` or `view`. Tick it to play the entrance a single time. Left off, the entrance replays each time the text scrolls back into view.
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS; only when `mode` is `` or `view` or `highlight`. The curve that movement follows, Snappy unless set.
Styling, in the schema file: `stagger`, `duration`, `easingCustom`.

### Scroll range (`bfbeScroll`)
The whole group shows only when `mode` is `scroll` or `highlight` or `kinetic`.
- `begin` (number) **Start at (% of viewport)**: only when `mode` is `scroll` or `highlight` or `kinetic`. How far down the screen the element's top is when the effect starts, 85 by default.
- `end` (number) **End at (% of viewport)**: only when `mode` is `scroll` or `highlight` or `kinetic`. How far down the screen the element's top is when the effect finishes, 35 by default.
Styling, in the schema file: `dim`.

### Highlight (`bfbeHighlight`)
The whole group shows only when `mode` is `highlight`.
- `highlight` (select) **Style**: options: `marker` Marker (default), `sweep` Colour sweep, `underline` Underline, `outline` Outline; only when `mode` is `highlight`. Pick Marker, the default, Colour sweep, Underline or Outline. It is drawn across the marked words.
- `highlightWords` (select) **Which words**: options: `marked` The marked ones (default), `all` All of them; only when `mode` is `highlight`. Choose The marked ones, the default, or All of them.
- `highlightDrive` (select) **Driven by**: options: `scrub` Scroll position (default), `play` Coming into view, once; only when `mode` is `highlight`. Scroll position, the default, draws the highlight as the reader scrolls. Coming into view, once plays it a single time when the text appears.
Styling, in the schema file: `highlightColor`, `highlightThickness`, `outlineWidth`.

### Kinetic (`bfbeKinetic`)
The whole group shows only when `mode` is `kinetic`.
- `kinetic` (select) **Effect**: options: `wave` Wave (default), `tilt` Tilt, `skew` Skew, `rise` Rise; only when `mode` is `kinetic`. How the text moves as the reader scrolls. Pick Wave, the default, Tilt, Skew or Rise.
Styling, in the schema file: `strength`.

### Count up (`bfbeCount`)
The whole group shows only when `mode` is `count`.
- `from` (number) **From**: only when `mode` is `count`. The number the count starts at, 0 by default.
- `to` (text) **To**: placeholder 1200; dynamic data accepted; only when `mode` is `count`. The number to count to, 1200 by default. It accepts dynamic data and reads the number inside the field, so a field holding "1,200 visitors" counts to 1200.
- `decimals` (number) **Decimals**: only when `mode` is `count`. How many decimal places the count shows, 0 by default and up to 4.
- `separators` (checkbox) **Thousands separators**: only when `mode` is `count`. Tick it to group the digits. The separators follow the page's language. Off by default.
- `prefix` (text) **Before the number**: dynamic data accepted; only when `mode` is `count`. Text shown before the number, such as a currency sign. It takes dynamic data.
- `suffix` (text) **After the number**: dynamic data accepted; only when `mode` is `count`. Text shown after the number, such as a plus sign or a unit. It takes dynamic data.
- `countDuration` (number) **Duration (ms)**: only when `mode` is `count`. How long the count takes, 2000 by default, from 100 to 10000. The finished number is already in the page, so it reads correctly without the script.

### Marked words (`bfbeMarked`)
The whole group shows only when `mode` is not `count`.
Styling only, every key in the schema file: `markedColor`, `markedTypography`.

## What it guarantees for accessibility (do not undo)
- A visually hidden copy of the whole text is in the page.
- The split words or letters are aria-hidden, so a screen reader reads the phrase once.
- Under reduced motion every part shows at once with no animation, scroll-driven modes show their finished state, and the count-up shows its final number without counting.
- The text keeps the HTML tag you choose, so a heading stays a heading in the page's outline.
<!-- bfbe:generated:end -->

## Rendered DOM

The root is the **HTML tag** (`tag`, `h2` by default, the same tag in the canvas) with Bricks' `id="brxe-<id>"`, class
`bfbe-rv` and `data-bfbe-mode` (`view`, `scroll`, `highlight`, `kinetic` or `count`). A text mode writes every variant
attribute, empty where it does not apply, so match on values: `data-bfbe-by`, `data-bfbe-fx` (reveal **Effect**),
`data-bfbe-hl` (highlight **Style**), `data-bfbe-drive` (`scrub` or `play`), `data-bfbe-k` (kinetic **Effect**),
`data-bfbe-play` (`view` or `load`), `data-bfbe-repeat` (`1` while **Play once** is off) and `data-bfbe-range`.

```html
<p id="brxe-abc123" class="bfbe-rv" data-bfbe-mode="highlight" data-bfbe-by="words" data-bfbe-fx data-bfbe-hl="marker"
   data-bfbe-drive="scrub" data-bfbe-k data-bfbe-play data-bfbe-repeat
   style="--bfbe-rv-begin:15vh;--bfbe-rv-end:65vh" data-bfbe-range="85 35">
  <span class="bfbe-sr">Clients who never read the brief.</span>
  <span class="bfbe-rv__parts" aria-hidden="true" style="--bfbe-n:6;--bfbe-m:4">
    <span class="bfbe-rv__part" style="--bfbe-i:0">Clients</span>
    <span class="bfbe-rv__part" style="--bfbe-i:1">who</span>
    <span class="bfbe-rv__part is-marked" style="--bfbe-i:2;--bfbe-j:0">never</span>
    <!-- read, the and brief. follow, each is-marked with its own j index -->
  </span>
</p>
```

- Each `.bfbe-rv__part` is an inline-block span with its index `--bfbe-i`; words inside `<mark>` add `is-marked` and
  `--bfbe-j`. Punctuation touching a word joins its part, so the full stop after `</mark>` above is marked too.
- **Split by** (`split`) Letters puts a word's letters in a `.bfbe-rv__word` that never wraps, each space a
  `.bfbe-rv__part--space`; a Curtain wraps every part in `.bfbe-rv__mask`. Lines: the script regroups the parts into
  `.bfbe-rv__line > .bfbe-rv__line-in` after fonts load and each resize, and sets `--bfbe-n` to the line count.
- `.is-in` on the root starts a reveal or a played highlight: added when 15% of the root is in view (at once for On
  page load), removed when it leaves unless it plays once. The canvas adds `.is-settled` to hold a played reveal.
- The scroll modes read `--bfbe-p` (0 to 1) on the root, from a CSS `view()` timeline where the browser has one, or an
  inline style the script writes on scroll. `--bfbe-rv-begin` and `--bfbe-rv-end` are 100 minus Start and End, in `vh`.
- Count up draws `.bfbe-rv__prefix`, `.bfbe-rv__number` (tabular figures) and `.bfbe-rv__suffix`, with
  `data-bfbe-count='{"from":0,"to":12480,"decimals":0,"sep":true,"ms":2500}'` on the root and none of the variant
  attributes. The server prints the final number; the script sets it back to From and counts on arrival.
- On the root as custom properties: **Part delay** `--bfbe-rv-stagger`, **Duration** `--bfbe-rv-duration`, **Easing**
  `--bfbe-ease`, **Dim opacity** `--bfbe-rv-dim`, highlight **Colour** `--bfbe-rv-hl`, **Thickness** `--bfbe-rv-hl-h`,
  **Line width** `--bfbe-rv-hl-w`, **Strength** `--bfbe-rv-strength`. **Marked words** Colour and Typography
  (`markedColor`, `markedTypography`) write to `.is-marked`; Bricks' typography on the root styles every part.

## Wiring to other elements

Stands alone; nothing targets it and it targets nothing. Two pack tokens on `:root` reach it: `--bfbe-accent` is the
highlight colour while **Colour** (`highlightColor`) is unset, and `--bfbe-ease` is the count-up's curve. To style
several alike, give them a class in `_cssClasses` rather than styling `_cssId`, since component instances share ids.
Roots that arrive by AJAX pagination, a loaded page, a query result or a popup start on Bricks' own events; for markup
your own script adds, call `window.bfbeTextReveal()`, which starts each root it has not seen and leaves the rest alone.

## Verified patterns

Hero headline, from the demo page `demo-bfb-text-reveal`. The words fade up one after another as the page loads
(`trigger: "load"`), 45 ms apart (`stagger`). **Play once** is off, so it replays when the reader scrolls back up to it.

```json
{
  "name": "bfbe-text-reveal",
  "settings": {
    "text": "Every job, every van, every invoice, in one place.",
    "tag": "h1",
    "split": "words",
    "trigger": "load",
    "stagger": 45
  }
}
```

Marker drawn across the marked words as the reader scrolls, from the fixture page `fixture-text-reveal`. `<mark>`
picks the words, `mode: "highlight"` draws the default Marker over them in turn, `highlightColor` sets its colour.

```json
{
  "name": "bfbe-text-reveal",
  "settings": {
    "tag": "p",
    "text": "We build for the designers who notice the half pixel, the agencies that ship on Friday, and the clients who <mark>never read the brief</mark>. Every element earns its bytes, and every motion earns its place.",
    "mode": "highlight",
    "highlightColor": { "hex": "#e0a020" }
  }
}
```

Statistic that counts up on arrival, from the fixture page `fixture-text-reveal`. `separators` groups the digits (off
unless set), `prefix` and `suffix` wrap the number, `countDuration` is the whole count in ms, `div` keeps it out of
the outline.

```json
{
  "name": "bfbe-text-reveal",
  "settings": {
    "tag": "div",
    "mode": "count",
    "to": "12480",
    "separators": true,
    "prefix": "+",
    "suffix": " sites",
    "countDuration": 2500
  }
}
```

## Gotchas

- **A bare `<mark>` is the one tag read.** `<mark class="x">` is stripped like any other tag and its words stay
  unmarked, and a stripped tag leaves no space, so `bold<br>next` becomes the one word "boldnext". <!-- src: plugins/bfb-elements-pro/elements/text-reveal.php:436, :444, :448, :459-465; rendered 2026-10-08: <mark class="x"> gave --bfbe-m:0, "<strong>bold</strong><br>two" gave the part "boldtwo" -->
- **Some settings draw nothing.** An empty **Text** (`text`), or a dynamic tag that resolves empty, prints no markup on
  the page; Highlight on scroll with **Which words** on The marked ones and no `<mark>` draws no highlight. <!-- src: plugins/bfb-elements-pro/elements/text-reveal.php:533-537, :566-569; plugins/bfb-elements/includes/abstract-element.php:538-541 -->
- **An unset highlight Colour is the text's own colour.** `--bfbe-rv-hl` falls back to `--bfbe-accent`, which is
  `currentColor`: a Marker becomes a solid bar over the lower half of the words, and a Colour sweep paints nothing. <!-- src: src/elements/text-reveal/text-reveal.css:17; plugins/bfb-elements/includes/class-assets.php:78; measured 2026-10-08 in headless Chrome: marker gradient rgb(17,17,17) on text rgb(17,17,17), sweep words transparent at every progress -->
- **A Colour sweep hides marked words until it reaches them.** Marked parts are `color: transparent` with the colour
  clipped to the glyphs, so with All of them the whole text is blank before the reader scrolls. <!-- src: src/elements/text-reveal/text-reveal.css:108-115; measured 2026-10-08 on fixture-text-reveal: sweep at progress 0 computed color transparent, gradient #0d9488 50% / transparent 50% at position 100% -->
- **Marked words Colour cancels a Colour sweep.** Bricks writes `markedColor` as `#brxe-<id> .is-marked { color }`,
  which outranks the sweep's transparent text, so the words read in that colour and the sweep never shows. <!-- src: src/elements/text-reveal/text-reveal.css:108-115; measured 2026-10-08: Bricks' generated CSS "#brxe-trE01a .is-marked {color: #cc0000}", words solid #cc0000 at progress 0, 0.5 and 1 -->
- **Split by Lines breaks Light up with scroll and Rise.** The script sets `--bfbe-n` to the line count while each part
  keeps its word index, so at the end of the range the first (lines + 1) words light up and the rest stay at
  **Dim opacity** (`dim`), or at 0.15 for Rise. <!-- src: src/elements/text-reveal/text-reveal.js:48; src/elements/text-reveal/text-reveal.css:70-72, :124; measured 2026-10-08 in headless Chrome: 35 words in 5 lines at --bfbe-p 1, words 0 to 5 at opacity 1, words 6 to 34 at 0.2 (scroll) and 0.15 (rise) -->
- **A scrubbed highlight ignores the timing controls.** With **Driven by** (`highlightDrive`) on Scroll position, the
  default, **Part delay** (`stagger`), **Duration** (`duration`) and **Easing** (`easing`) are offered and do nothing;
  they time Coming into view, once. <!-- src: src/elements/text-reveal/text-reveal.css:50-51, :117; plugins/bfb-elements-pro/elements/text-reveal.php:170, :174 -->
- **On page load needs Play once below the fold.** Without `once`, the first viewport check hides text that starts off
  screen and it plays on arrival instead; the canvas ignores `once` altogether, so judge it on the page. <!-- src: src/elements/text-reveal/text-reveal.js:80, :135-139; measured 2026-10-08 in headless Chrome: trigger load below the fold had no is-in at load without once, is-in with once -->
- **Start at must be larger than End at.** **Start at** (`begin`, 85) and **End at** (`end`, 35) place the element's
  top as a percentage down the viewport, and it travels from the larger to the smaller; reversed, Chrome jumps from
  start to finish in one step and the script's fallback runs backwards. <!-- src: plugins/bfb-elements-pro/elements/text-reveal.php:557-561; src/elements/text-reveal/text-reveal.js:104; measured 2026-10-08 in headless Chrome: begin 30, end 80 read --bfbe-p 0 with the top at 95% to 40%, 1 at 20% and 5% -->
- **To keeps the first number it finds.** Commas and spaces are dropped as separators and a dot is the decimal point,
  so "1.200" counts to 1.2 and shows 1; an empty **To** (`to`) counts to 1200 and one with no digits to 0. <!-- src: plugins/bfb-elements-pro/elements/text-reveal.php:513; rendered 2026-10-08: "1.200" gave to 1.2, "" gave 1200, "abc" gave 0 -->
- **Count up's Duration is the whole count.** Its **Duration (ms)** (`countDuration`) is 2000 when unset, and the curve
  is the pack's `--bfbe-ease` on `:root`; the Reveal group's Duration and Easing are hidden here and do not apply. <!-- src: plugins/bfb-elements-pro/elements/text-reveal.php:395-406, :521; src/elements/text-reveal/text-reveal.js:61-62 -->
- **A check below the fold reads the starting state.** Reveal parts sit at opacity 0 until 15% of the root is in view,
  and a count-up shows From until it arrives, so scroll to the element before asserting what it shows. <!-- src: src/elements/text-reveal/text-reveal.css:48-49; src/elements/text-reveal/text-reveal.js:70, :81; measured 2026-10-08 on fixture-text-reveal: the 12,480 count read "0" before it was scrolled to -->

## Never do

- Do not put attributes on `<mark>`, or any other tag, in `text`; write bare `<mark>` pairs around plain words.
- Do not leave `highlightColor` unset on `mode: "highlight"`.
- Do not set `markedColor` on `highlight: "sweep"`.
- Do not combine `split: "lines"` with `mode: "scroll"` or `kinetic: "rise"`.
- Do not set `begin` at or below `end`.
- Do not feed `to` a number written with a dot between thousands, or a dynamic tag that can resolve empty.
- Do not set `trigger: "load"` on text that starts below the fold without `once: true`.
- Do not remove the `.bfbe-sr` copy or the `aria-hidden` on `.bfbe-rv__parts`.
