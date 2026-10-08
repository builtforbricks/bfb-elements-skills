---
name: bfbe-text-rotator
description: "Use when placing, wiring or styling BFB Text Rotator (`bfbe-text-rotator`): one heading with text before, a rotating word and text after, which stays readable as a single sentence. Read before writing its settings."
---

# BFB Text Rotator (`bfbe-text-rotator`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-text-rotator.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/text-rotator/

## What it is
One heading with text before, a rotating word and text after, which stays readable as a single sentence. Nine swap effects or a letter-scramble mode change the word, and five hover effects make the letters react to the pointer. Assistive technology sees the word that is showing, and rotation stops on the opening word under reduced motion.

**Not for:** The rotating words share one slot in a sentence, so each must read correctly with the same text around it. Anything visitors must read at their own pace belongs in static text, since the words keep changing.

**Costs a page:** CSS 1.51 KB, JS 1.63 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** no · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** no · **Reduced motion:** yes

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Bricks' query loop (`hasLoop`, `query`); Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Text (`bfbeText`)
- `tag` (select) **HTML tag**: options: `h1` h1, `h2` h2 (default), `h3` h3, `h4` h4, `h5` h5, `h6` h6, `p` p, `div` div. H2 by default. Pick h1 to h6, p or div so the rotator sits at the right level in your heading outline.
- `before` (text) **Text before**: dynamic data accepted. The words ahead of the rotating word. It accepts dynamic data.
- `words` (repeater) **Words**. A list where each row has a Word, which accepts dynamic data, and an optional Colour for that word.
- `after` (text) **Text after**: dynamic data accepted. The words after the rotating word. It accepts dynamic data too.

### Rotation (`bfbeRotation`)
- `mode` (select) **Change words by**: options: `swap` An effect (default), `scramble` Scrambling the letters. An effect is the default. Scrambling the letters churns random characters and settles left to right on the next word.
- `effect` (select) **Effect**: options: `up` Slide up (default), `down` Slide down, `flip` Flip, `letters` Letter by letter, `clip` Curtain, `blur` Blur, `scale` Scale, `type` Typewriter, `bar` Loading bar; only when `mode` is not `scramble`. Pick Slide up, Slide down, Flip, Letter by letter, Curtain, Blur, Scale, Typewriter or Loading bar. Slide up is the default.
- `interval` (number) **Time per word (ms)**. How long each word stays, 2500 by default and 300 at the least.
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS. How the change speeds up and slows down, Snappy by default. Pick Custom and type your own curve in Custom curve.
- `pauseOnHover` (checkbox) **Pause on hover**. Off by default. Tick it to hold the rotation while the pointer is over the heading. Clicking the heading also pauses and resumes it, whatever this is set to.
Styling, in the schema file: `duration`, `easingCustom`, `stagger`.

### Hover effect (`bfbeHover`)
- `hover` (select) **Effect**: options: `none` None (default), `lift` Letters lift, `wave` Wave, `tumble` Tumble, `shine` Shine sweep, `weight` Weight follows the pointer. Pick Slide up, Slide down, Flip, Letter by letter, Curtain, Blur, Scale, Typewriter or Loading bar. Slide up is the default.
- `weightRange` (text) **Weight range**: placeholder 300 900; only when `hover` is `weight`. The lightest and heaviest weight, separated by a space, 300 900 by default. It appears with the Weight effect.
Styling, in the schema file: `hoverStrength`, `shineColor`.

### Rotating word (`bfbeWord`)
Styling only, every key in the schema file: `wordTypography`, `wordAlign`, `barColor`, `barThickness`, `caretColor`, `caretWidth`.

## What it guarantees for accessibility (do not undo)
- Words that are not showing are aria-hidden, so assistive technology reads the sentence with the word currently on display.
- No live region is used, so nothing is announced as the words change.
- When letters are split for an effect or a hover, a full copy of the text sits ahead of the split letters, which are aria-hidden.
- Rotation pauses while the heading is off screen, while the browser tab is hidden, and under the pointer when Pause on hover is ticked.
- With reduced motion requested, the rotation never starts and the heading holds its opening word; the hover effects stay off.
<!-- bfbe:generated:end -->

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
