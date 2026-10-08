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
- `kinetic` (select) **Effect**: options: `wave` Wave (default), `tilt` Tilt, `skew` Skew, `rise` Rise; only when `mode` is `kinetic`. Pick Fade up, the default, Fade down, Blur in, Scale in, Slide from the left, Slide from the right or Curtain.
Styling, in the schema file: `strength`.

### Count up (`bfbeCount`)
The whole group shows only when `mode` is `count`.
- `from` (number) **From**: only when `mode` is `count`. The number the count starts at, 0 by default.
- `to` (text) **To**: placeholder 1200; dynamic data accepted; only when `mode` is `count`. The number to count to, 1200 by default. It accepts dynamic data and reads the number inside the field, so a field holding "1,200 visitors" counts to 1200.
- `decimals` (number) **Decimals**: only when `mode` is `count`. How many decimal places the count shows, 0 by default and up to 4.
- `separators` (checkbox) **Thousands separators**: only when `mode` is `count`. Tick it to group the digits. The separators follow the page's language. Off by default.
- `prefix` (text) **Before the number**: dynamic data accepted; only when `mode` is `count`. Text shown before the number, such as a currency sign. It takes dynamic data.
- `suffix` (text) **After the number**: dynamic data accepted; only when `mode` is `count`. Text shown after the number, such as a plus sign or a unit. It takes dynamic data.
- `countDuration` (number) **Duration (ms)**: only when `mode` is `count`. How long each part takes to come in, 600 by default. With Highlight on scroll played on view, it is how long the highlight takes to draw.

### Marked words (`bfbeMarked`)
The whole group shows only when `mode` is not `count`.
Styling only, every key in the schema file: `markedColor`, `markedTypography`.

## What it guarantees for accessibility (do not undo)
- A visually hidden copy of the whole text is in the page.
- The split words or letters are aria-hidden, so a screen reader reads the phrase once.
- Under reduced motion every part shows at once with no animation, scroll-driven modes show their finished state, and the count-up shows its final number without counting.
- The text keeps the HTML tag you choose, so a heading stays a heading in the page's outline.
<!-- bfbe:generated:end -->

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
