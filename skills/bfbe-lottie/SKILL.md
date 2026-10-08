---
name: bfbe-lottie
description: "Use when placing, wiring or styling BFB Lottie (`bfbe-lottie`): plays a Lottie animation from the media library, or from a URL or dynamic data field. Read before writing its settings."
---

# BFB Lottie (`bfbe-lottie`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-lottie.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/lottie/

## What it is
Plays a Lottie animation from the media library, or from a URL or dynamic data field. Playback can start immediately, when visible, on hover or on click, or follow the scroll position. The player, lottie-light 5.13.0, is served from your own site, and reduced motion shows the opening frame as a still.

**Not for:** Lottie plays vector animations exported as JSON and draws them as SVG. Video and photographic sequences belong in Bricks' own video or image elements.

**Costs a page:** CSS 0.26 KB, JS 1.26 KB (gzipped), plus lottie-web (light, SVG renderer), loaded only on pages that use it.

**Nestable:** no · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Bricks' query loop (`hasLoop`, `query`); Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Animation (`bfbeSource`)
- `source` (select) **Animation from**: options: `file` The media library (default), `url` A URL or a field. The media library is the default, or A URL or a field. Uploading .json files needs Allow Lottie files in BFB Elements Settings, on by default. Each file is checked: a JSON file that is not a Lottie animation is refused.
- `file` (file): only when `source` is not `url`
- `url` (text) **URL**: placeholder https://; dynamic data accepted; only when `source` is `url`. The address of a Lottie JSON file. It accepts dynamic data. A file on another domain must allow cross-origin requests.

### Playback (`bfbePlayback`)
- `trigger` (select) **Play**: options: `autoplay` Immediately, `inview` When visible (default), `hover` On hover, `click` On click, `scroll` With scroll. When visible is the default and plays the animation when it comes into view. Or choose Immediately, On hover, On click or With scroll.
- `loop` (checkbox) **Loop**: only when `trigger` is not `scroll`. Off by default. Tick it to repeat the animation. With Play set to With scroll, Loop, Speed and Direction are hidden, because the scroll position drives the frame.
- `speed` (number) **Speed**: only when `trigger` is not `scroll`. A multiplier from 0.1 to 5, where 1 is the file's own speed.
- `direction` (select) **Direction**: options: `forward` Forward (default), `reverse` Reverse, `bounce` Back and forth; only when `trigger` is not `scroll`. Forward is the default, or pick Reverse or Back and forth.
- `ariaLabel` (text) **Description**: dynamic data accepted. Text for screen readers. Empty means the animation is decorative and hidden from them, unless Play is On click.

### Frame (`bfbeSize`)
Styling only, every key in the schema file: `width`, `ratio`, `align`, `stageBackground`, `stageBorder`.

## What it guarantees for accessibility (do not undo)
- With Play set to On click, the frame becomes a focusable button that answers Enter and Space and reports aria-pressed while it plays.
- Its name is the Description, or Play animation when that is empty.
- The other triggers have no keyboard action: a filled Description gives the frame the img role with that label, and an empty one hides it.
- With reduced motion requested, the animation stays on its opening frame for every trigger except On click, where a visitor can still start it.
<!-- bfbe:generated:end -->

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
