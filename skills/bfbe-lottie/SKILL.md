---
name: bfbe-lottie
description: "Use when adding a Lottie (JSON) animation with BFB Lottie (`bfbe-lottie`): an animated icon or illustration that plays on load, in view, on hover, on click or with the scroll, from the media library, a URL or a dynamic data field. Read before writing its settings."
---

# BFB Lottie (`bfbe-lottie`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 1.0.0-beta.3 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
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

## Rendered DOM

```html
<div id="brxe-a1b2c3" class="brxe-bfbe-lottie bfbe-lottie">
  <div class="bfbe-lottie__stage is-ready"
       data-bfbe-src="https://example.com/wp-content/uploads/route.json"
       data-bfbe-trigger="inview" data-bfbe-direction="forward"
       data-bfbe-speed="1" data-bfbe-loop="1"
       role="img" aria-label="A route drawing itself between four jobs">
    <svg>...</svg>
  </div>
</div>
```

- `.bfbe-lottie` is the root: a flex row the full width of its column. **Align** `align` writes its `justify-content`; `_cssClasses`, `_attributes` and Bricks' universals land here.
- `.bfbe-lottie__stage` is the frame the animation is drawn in. **Width** `width` (as `inline-size`), **Aspect ratio** `ratio`, **Background** `stageBackground` and **Border** `stageBorder` all write to it.
- The stage defaults to 100% wide, `aspect-ratio: 1 / 1`, corners from `--bfbe-radius` (12px).
- The script reads the stage's `data-bfbe-*` attributes and nothing else. `data-bfbe-src` is the resolved address; `data-bfbe-loop` is present when **Loop** is on.
- The ARIA follows **Play** `trigger`. `click` gives `tabindex="0"`, `role="button"`, `aria-pressed` and `aria-label`. Any other trigger gives `role="img"` with the **Description** `ariaLabel`, or `aria-hidden="true"` when it is empty.
- States: `is-ready` lands on the stage once the file has parsed; until then the stage shows a faint `--bfbe-surface` fill. With `click`, `aria-pressed` reads `"true"` while it plays and `"false"` after a pause or at the end.
- lottie-web inserts one `<svg>` at 100% by 100% of the stage. To verify a load on the page, look for `.bfbe-lottie__stage.is-ready svg`.
- Two scripts, enqueued on pages that hold the element: `bfbe-lottie-runtime` (lottie-light 5.13.0), then `bfbe-lottie`.

## Wiring to other elements

Stands alone; nothing targets it and it targets nothing. No setting lets another element start, pause or scrub it: for a play the visitor starts, set `trigger: "click"` and the frame itself becomes the button.

- **Dynamic data.** Set **Animation from** `source: "url"` and put a dynamic tag in **URL** `url`. A field holding a file, an attachment id or a plain address all resolve, so one template gives each post its own animation.
- **AJAX content.** The script scans again after Bricks' AJAX pagination, load more, query filter results and AJAX popups. For markup added any other way, call `window.bfbeLottie()`.
- **Targeting.** To style one instance, give it a class in `_cssClasses` and select `.that-class .bfbe-lottie__stage`. Never use `_cssId`: component instances share ids.

## Verified patterns

**An illustration that plays when scrolled into view and repeats.** From the Lottie demo page (`demo-bfb-lottie`), with `width: "100%"` trimmed as the default and the address made generic. `ariaLabel` gives the stage `role="img"`; leave it out for a decorative animation.

```json
{
  "name": "bfbe-lottie",
  "settings": {
    "source": "url",
    "url": "https://example.com/wp-content/uploads/route.json",
    "trigger": "inview",
    "loop": true,
    "ariaLabel": "A route drawing itself between four jobs"
  }
}
```

**Press to play, there and back.** From the fixture page `fixture-lottie`. The frame is a button answering Enter and Space; one press plays forward, then back, and rests on the first frame. With no `ariaLabel` its name is "Play animation"; add one that names what plays.

```json
{
  "name": "bfbe-lottie",
  "settings": {
    "source": "url",
    "url": "https://example.com/wp-content/uploads/spin.json",
    "trigger": "click",
    "direction": "bounce"
  }
}
```

**Frames that follow the scroll.** From the fixture page `fixture-lottie`. No `loop`, `speed` or `direction`: the panel hides them under this trigger and they are dropped before render. Decorative here, so the stage is `aria-hidden`.

```json
{
  "name": "bfbe-lottie",
  "settings": {
    "source": "url",
    "url": "https://example.com/wp-content/uploads/spin.json",
    "trigger": "scroll"
  }
}
```

## Gotchas

- **`url` does nothing without `source: "url"`.** The media library is the default source, and a key the panel hides is dropped before render, so a lone `url` draws nothing on the page. <!-- src: plugins/bfb-elements/elements/lottie.php:252; plugins/bfb-elements/includes/abstract-element.php:86 -->
- **The canvas shows a notice the page does not.** With no address resolved, the builder shows "Choose a Lottie file or enter a URL."; the page gets no markup at all. A looped post whose field is empty gets no element either. <!-- src: plugins/bfb-elements/elements/lottie.php:260; plugins/bfb-elements/includes/abstract-element.php:538 -->
- **`file` is an attachment.** It takes the builder's stored `{"id": 123, "url": "..."}` or a bare attachment id; with both, the stored `url` is used. <!-- src: plugins/bfb-elements/includes/abstract-element.php:1443 -->
- **Uploading .json needs the setting.** **Allow Lottie files** (BFB Elements, Settings, Media library; on by default) and the `upload_files` capability are both required. A .json without a `layers` array is refused. <!-- src: plugins/bfb-elements/includes/class-uploads.php:73; plugins/bfb-elements/includes/class-plugin.php:55; plugins/bfb-elements/includes/class-admin.php:308 -->
- **A file on another domain needs CORS.** The player fetches the JSON itself; when the host refuses, the stage never gets `is-ready` and keeps its faint placeholder fill. <!-- src: plugins/bfb-elements/elements/lottie.php:107; src/elements/lottie/lottie.css:21 -->
- **The frame is square until told otherwise.** lottie-web fits the drawing inside the stage (`xMidYMid meet`), so a 16:9 file in the default `1 / 1` frame leaves empty bands. Set `ratio` to the file's own, such as `"16 / 9"`. <!-- src: src/elements/lottie/lottie.css:11; src/elements/lottie/lottie.js:65; plugins/bfb-elements/assets/vendor/lottie-light.min.js (preserveAspectRatio default) -->
- **Bricks' background and border paint the whole row.** The root spans its column; the animation sits in the stage. Use `stageBackground` and `stageBorder`, not `_background` and `_border`. <!-- src: plugins/bfb-elements/elements/lottie.php:204 -->
- **Align with `align`.** The root is flex from the stylesheet, and Bricks' `_justifyContent` stays hidden until `_display` is flex. `align` moves the stage once `width` is below 100%. <!-- src: plugins/bfb-elements/elements/lottie.php:195; docs/SESSION-HANDOFF.md "Round 269" -->
- **With scroll maps the passage through the viewport.** The first frame shows as the stage's top enters at the bottom, the last as its bottom leaves at the top. A stage already in view at load, such as a hero, starts part-way through. <!-- src: src/elements/lottie/lottie.js:84 -->
- **Without Loop, Immediately and When visible play once.** A finished play does not restart when the stage scrolls back into view. On hover and On click rewind at the end and play again. <!-- src: src/elements/lottie/lottie.js:81; src/elements/lottie/lottie.js:110 -->
- **On hover listens to the stage, not its card.** Hovering a card around it does nothing. Leaving pauses on the current frame; the next hover resumes from there. <!-- src: src/elements/lottie/lottie.js:116 -->
- **Direction changes where it rests; reduced motion does not.** Reverse starts on the last frame. Back and forth without Loop plays there and back once, then rests on the first frame. Reduced motion shows the file's first frame whatever Direction says. <!-- src: src/elements/lottie/lottie.js:74; src/elements/lottie/lottie.js:76; src/elements/lottie/lottie.js:101 -->

## Never do

- Do not set `url` without `source: "url"`, or `file` together with `source: "url"`.
- Do not set `loop`, `speed` or `direction` with `trigger: "scroll"`.
- Do not style or align the frame with Bricks' `_background`, `_border` or `_justifyContent`; use `stageBackground`, `stageBorder` and `align`.
- Do not leave `ariaLabel` empty on an animation that carries meaning: empty hides it from screen readers.
- Do not carry information in the motion alone: reduced motion shows the first frame for every trigger except `click`.
- Do not add `tabindex`, `role` or a link to a `trigger: "click"` Lottie, or nest it in a link or button: its stage is already the button.
- Do not point `url` at another domain unless that host sends cross-origin headers for the file.
