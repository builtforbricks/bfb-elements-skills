---
name: bfbe-text-rotator
description: "Use when building a rotating-word heading, a typewriter or scramble headline, or letters that react on hover with BFB Text Rotator (`bfbe-text-rotator`): text before, a rotating word and text after, read as one sentence. Read before writing its settings."
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
- `hover` (select) **Effect**: options: `none` None (default), `lift` Letters lift, `wave` Wave, `tumble` Tumble, `shine` Shine sweep, `weight` Weight follows the pointer. Weight needs a variable font.
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

## Rendered DOM

The root is the **HTML tag** (`tag`, `h2` by default) with class `bfbe-tr`, one mode class (`bfbe-tr--fx-<effect>`, or
`bfbe-tr--scramble`) and one hover class (`bfbe-tr--hover-<hover>`, `bfbe-tr--hover-none` included). It carries
`data-bfbe-interval` and an inline `--bfbe-tr-interval`, plus `data-bfbe-pause="1"` with **Pause on hover** and
`data-bfbe-weight="300 900"` with the weight hover.

```html
<h2 class="bfbe-tr bfbe-tr--fx-up bfbe-tr--hover-none" data-bfbe-interval="2500" style="--bfbe-tr-interval:2500ms">
  <span class="bfbe-tr__before">Built for</span>
  <span class="bfbe-tr__rotator">
    <span class="bfbe-tr__word is-active" data-bfbe-word="designers">designers</span>
    <span class="bfbe-tr__word" aria-hidden="true" data-bfbe-word="agencies">agencies</span>
  </span>
  <span class="bfbe-tr__after">today</span>
</h2>
```

- `.bfbe-tr__rotator` is an inline grid and every `.bfbe-tr__word` sits in its one cell. The script moves `is-active`,
  `is-leaving` and `aria-hidden` between words; each effect is drawn by the stylesheet from those two classes.
- Letter by letter, Typewriter and every hover effect split a word into `<span class="bfbe-sr">` (the readable copy) and
  an aria-hidden `.bfbe-tr__letters` holding `.bfbe-tr__letters-word` boxes of `.bfbe-tr__letters-part` spans, each with
  `--bfbe-i`. A hover effect splits Text before and Text after the same way.
- Typewriter adds `<span class="bfbe-tr__caret" aria-hidden="true">` inside each word, Loading bar adds
  `<span class="bfbe-tr__bar" aria-hidden="true">`. Neither is drawn in scramble mode.
- An empty Words row leaves `<span hidden></span>` in the rotator so per-word colours keep their row positions.
- Where controls write: each row's **Colour** to `.bfbe-tr__word:nth-child(n)`; **Typography** (`wordTypography`) to
  `.bfbe-tr__word`; **Align words** (`wordAlign`) to `justify-items` on `.bfbe-tr__rotator`; **Caret thickness**
  (`caretWidth`) to `.bfbe-tr__caret`. Duration, Easing, Letter delay, Strength, Shine colour, bar and caret colours are
  custom properties on the root (`--bfbe-tr-duration`, `--bfbe-tr-ease`, `--bfbe-tr-stagger`, `--bfbe-tr-strength`,
  `--bfbe-tr-shine`, `--bfbe-tr-bar`, `--bfbe-tr-bar-h`, `--bfbe-tr-caret`).
- With no words and no text around them, the page gets no markup at all; the canvas shows a notice.

## Wiring to other elements

Stands alone; nothing targets it and it targets nothing. To style several rotators alike, give them a class in
`_cssClasses` rather than styling `_cssId`, since component instances share ids. With the pro plugin the **Hover effect**
group holds two controls called **Effect**: `hover`, under The rotating words, is this element's own; `bfbeHoverEffect`,
under The whole element, is the pack's Hover Effects feature (skill `bfbe-hover-effects`) and acts on the element's box.

## Verified patterns

Hero heading where whole phrases rotate, from the demo page `demo-bfb-text-rotator`. Slide down (`effect: "down"`), and
each row's `color` tints its phrase against the plain Text before.

```json
{
  "name": "bfbe-text-rotator",
  "settings": {
    "tag": "h1",
    "before": "Roasted for",
    "words": [
      { "word": "the morning after", "color": { "hex": "#a88fff" } },
      { "word": "the long shift", "color": { "hex": "#a88fff" } },
      { "word": "the second cup", "color": { "hex": "#a88fff" } },
      { "word": "you, mostly", "color": { "hex": "#a88fff" } }
    ],
    "effect": "down"
  }
}
```

Typewriter, from the fixture page `fixture-text-rotator`. Each letter is deleted and typed at `stagger` (60 ms), so
`interval` goes up to 3000 to leave the typed word readable; `caretColor` exists for this effect alone.

```json
{
  "name": "bfbe-text-rotator",
  "settings": {
    "before": "We type",
    "words": [ { "word": "slowly" }, { "word": "carefully" }, { "word": "for you" } ],
    "effect": "type",
    "stagger": 60,
    "interval": 3000,
    "caretColor": { "hex": "#e0a020" }
  }
}
```

Scramble, from the fixture page `fixture-text-rotator`. `mode: "scramble"` churns the showing word for `duration`
(800 ms) and settles it into the next; `effect` is hidden in this mode, so it is left out. `pauseOnHover` holds the word
under the pointer.

```json
{
  "name": "bfbe-text-rotator",
  "settings": {
    "before": "Decode the",
    "words": [ { "word": "signal" }, { "word": "message" }, { "word": "pattern" } ],
    "mode": "scramble",
    "duration": 800,
    "pauseOnHover": true
  }
}
```

## Gotchas

- **The slot is as wide as the longest word.** Words share one grid cell, so a short word leaves a gap before Text after;
  `wordAlign` places it within that width. Typewriter differs: untyped letters take no room, so Text after moves with
  the typing. <!-- src: src/elements/text-rotator/text-rotator.css:22-28, :88-92; measured on fixture-text-rotator 2026-10-08: Slide up slot 166px on every word, Typewriter slot 94px with the waiting words at 0px -->
- **One word does not rotate.** The script starts the timer with two or more words; a single row is a static heading.
  <!-- src: src/elements/text-rotator/text-rotator.js:75 -->
- **A dynamic tag fills one row, never several.** A tag returning a list shows the whole list as one word, markup it
  returns is escaped to text, and a tag that resolves empty leaves a blank turn, because empty rows are dropped before tags resolve. <!-- src: plugins/bfb-elements/elements/text-rotator.php:349-356 -->
- **Letter effects need time for their letters.** With Letter by letter and Typewriter, a swap takes (letters out plus
  letters in) times **Letter delay** (`stagger`), plus **Duration** (`duration`) for Letter by letter. Raise `interval`
  for long words, or the next swap starts mid-word. <!-- src: src/elements/text-rotator/text-rotator.css:82, :92; src/elements/text-rotator/text-rotator.js:76 -->
- **Scramble drops turns when Duration reaches Time per word.** A tick that arrives while a scramble is still settling
  is skipped, so keep `duration` well under `interval`. <!-- src: src/elements/text-rotator/text-rotator.js:51, :54 -->
- **Scramble hides the effect's controls.** With `mode: "scramble"`, Effect, Letter delay, both Loading bar controls and
  both Caret controls are hidden, and no bar or caret is rendered. <!-- src: plugins/bfb-elements/elements/text-rotator.php:145, :177, :285-322, :398-408 -->
- **Hover effects never reach touch screens.** Lift, Wave, Tumble and Shine sweep run inside
  `@media (hover: hover) and (prefers-reduced-motion: no-preference)`. Lift, Wave, Tumble and Weight act on Text before
  and after too; Shine sweep paints the rotating word alone. <!-- src: src/elements/text-rotator/text-rotator.css:118-143; plugins/bfb-elements/elements/text-rotator.php:381-390 -->
- **Weight follows the pointer needs a variable font.** The script writes `font-variation-settings: "wght"` and
  `font-weight` per letter within **Weight range** (`weightRange`); a static font steps between the weights the site
  loads. A missing or non-numeric half falls back to 300 (lightest) or 900 (heaviest). <!-- src: plugins/bfb-elements/elements/text-rotator.php:212, :374-379; src/elements/text-rotator/text-rotator.js:98-108 -->
- **Strength stops at 3.** A typed **Strength** (`hoverStrength`) above 3 acts as 3 for Lift, Wave, Tumble and Shine
  sweep, which read `clamp(0.2, strength, 3)`. <!-- src: docs/elements/text-rotator.md "Strength is clamped where it is used"; src/elements/text-rotator/text-rotator.css:15 -->
- **A click holds the rotation, whatever Pause on hover says.** Every click or tap on the heading toggles a hold (the
  WCAG 2.2.2 stop), so a click meant for a link or an interaction on the element also pauses or resumes it. <!-- src: src/elements/text-rotator/text-rotator.js:94-95 -->
- **It rotates on screen alone.** Rotation stops while the heading is outside the viewport, while the tab is hidden and
  under reduced motion, so a check of an off-screen rotator reads the opening word. <!-- src: src/elements/text-rotator/text-rotator.js:75, :81-85, :115; measured on fixture-text-rotator 2026-10-08: rotators below the fold kept their opening word -->
- **The word's Typography beats the element's.** `wordTypography` writes to `.bfbe-tr__word`, inside the root, so the
  element's own typography styles Text before and after and loses on the word wherever both set a property. <!-- src: docs/elements/text-rotator.md "The rotating word's own typography"; plugins/bfb-elements/elements/text-rotator.php:266 -->

## Never do

- Do not set `effect`, `stagger`, `barColor`, `barThickness`, `caretColor` or `caretWidth` with `mode: "scramble"`.
- Do not set `shineColor` without `hover: "shine"`, nor `weightRange` without `hover: "weight"`.
- Do not give a scramble a `duration` at or above its `interval`.
- Do not feed a list or markup into one Words row through a dynamic tag; add one row per word.
- Do not carry meaning in a hover effect; touch screens and reduced-motion visitors never see it.
- Do not choose `hover: "weight"` on a site without a variable font.
- Do not remove `aria-hidden` from the words that are not showing, and do not add a live region to the heading.
