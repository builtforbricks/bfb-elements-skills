---
name: bfbe-copy
description: "Use when building a copy button with BFB Copy to Clipboard (`bfbe-copy`): a coupon code, a Wi-Fi password, a link or a code sample, copied from fixed text, dynamic data or another element on the page, with a Copied confirmation. Read before writing its settings."
---

# BFB Copy to Clipboard (`bfbe-copy`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 1.0.0-beta.3 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-copy.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/copy/

## What it is
A button that copies fixed text, dynamic data, or the contents of another element on the page to the visitor's clipboard. After copying, the label and icon swap for the ones you set, then reset after a delay, and a polite live region announces it. It uses the clipboard API on secure pages and falls back to the older copy command elsewhere.

**Not for:** Anything it copies must already be in the page, either typed here or inside the element your selector finds. It cannot fetch text from a server when clicked, and it never pastes into fields.

**Costs a page:** CSS 0.45 KB, JS 0.84 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** no · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Bricks' query loop (`hasLoop`, `query`); Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### What to copy (`bfbeSource`)
- `source` (select) **Source**: options: `text` Text (default), `selector` An element on the page. Text is the default. An element on the page copies the value or text of whatever your selector matches when the button is clicked.
- `text` (textarea) **Text**: dynamic data accepted; only when `source` is not `selector`. The text to copy, in a multi-line field that accepts dynamic data, such as a coupon code from a custom field.
- `selector` (text) **CSS selector**: placeholder #coupon; only when `source` is `selector`. The element to read, such as #coupon. A form field gives its value and other elements give their text.

### Button (`bfbeButton`)
- `label` (text) **Label**: placeholder Copy; dynamic data accepted. The words on the button, Copy by default. They also name the button for screen readers, and the field accepts dynamic data.
- `icon` (icon) **Icon**. An optional icon beside the label.
- `iconPosition` (select) **Icon position**: options: `left` Left (default), `right` Right. Left of the label by default, or Right.
Styling, in the schema file: `hoverColor`, `hoverBackground`.

### Icon (`bfbeIcon`)
Styling only, every key in the schema file: `iconSize`, `iconColor`, `iconGap`.

### After copying (`bfbeDone`)
- `successLabel` (text) **Label after copying**: placeholder Copied; dynamic data accepted. The words shown once copied, Copied by default. Screen readers hear them too.
- `successIcon` (icon) **Icon after copying**. An optional icon that replaces the button's icon while the copied state shows.
- `resetAfter` (number) **Reset after (ms)**. How long the copied state stays, 2000 by default. Set 0 to keep it until the page reloads.
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS. How the swap speeds up and slows down, Snappy by default. Pick Custom and type your own curve in Custom curve.
Styling, in the schema file: `doneColor`, `doneBackground`, `doneBorder`, `duration`, `easingCustom`.

## What it guarantees for accessibility (do not undo)
- The element is a real button, so Enter and Space copy, and its name comes from the visible label.
- After a successful copy, the Label after copying text is written into a visually hidden polite live region, so screen readers announce it.
- The label and icon for the inactive state are hidden with visibility, so a screen reader meets one label at a time.
- With reduced motion requested, the label swap and the icon pop run with a duration of zero.
<!-- bfbe:generated:end -->

## Rendered DOM

On the page the root is a real `<button type="button">`, so Bricks' own Typography, Background, Border and Spacing
style it. The shared `.bfbe-chip` rule draws the default pill, in the theme's font and colour.

```html
<button class="brxe-bfbe-copy bfbe-copy bfbe-chip bfbe-copy--icon-left" type="button"
        data-bfbe-reset="2000" data-bfbe-copy="SAVE20">
  <span class="bfbe-copy__icons">
    <i class="bfbe-copy__icon bfbe-copy__icon--idle" aria-hidden="true"></i>
    <i class="bfbe-copy__icon bfbe-copy__icon--done" aria-hidden="true"></i>
  </span>
  <span class="bfbe-copy__labels">
    <span class="bfbe-copy__label bfbe-copy__label--idle">Copy</span>
    <span class="bfbe-copy__label bfbe-copy__label--done">Copied</span>
  </span>
</button>
```

- `data-bfbe-copy` holds the resolved Text; with `source: "selector"` it is `data-bfbe-copy-selector` instead.
  `data-bfbe-reset` is **Reset after (ms)**, `0` meaning never.
- `.bfbe-copy__icons` appears only when **Icon** or **Icon after copying** is set; each `<i>` appears only for its own icon.
- `bfbe-copy--icon-right` sets `flex-direction: row-reverse` on the root; the source order stays icons first.
- After a successful write the script adds `is-copied` to the root and removes it after `data-bfbe-reset` ms. The idle
  parts take `opacity: 0` and `visibility: hidden`, the done parts show, and the done icon pops.
- One visually hidden `<div class="bfbe-copy-live" aria-live="polite">` is appended to `body` per page; it receives
  the done label's text 50 ms after each copy.
- Where controls write: `iconSize` and `iconColor` to `.bfbe-copy__icon`; `iconGap`, `duration` (`--bfbe-duration`),
  `easing` (`--bfbe-ease`) and `easingCustom` to the root; `hoverColor` and `hoverBackground` to the root's `:hover`
  and `:focus-visible`; `doneColor`, `doneBackground` and `doneBorder` to the root's `.is-copied`.

## Wiring to other elements

- **Reads another element** with **Source** `source: "selector"` and **CSS selector** `selector`. At click time the
  script copies the first match's `value` if it is a form field with one, otherwise its visible text (`innerText`).
- Give the target a class through `_cssClasses` (for example `coupon-code`) and set `selector: ".coupon-code"`. Not
  `_cssId`, because component instances share ids.
- Nothing points at the Copy button. It has no trigger attribute and reacts to its own click, Enter or Space.
- The script re-binds every `.bfbe-copy` after Bricks' `bricks/ajax/pagination/completed`,
  `bricks/ajax/load_page/completed`, `bricks/ajax/query_result/displayed` and `bricks/ajax/popup/loaded` events. A
  button your own script inserts needs `window.bfbeCopy()` afterwards; calling it twice is safe.

## Verified patterns

**A coupon code in Text, the copied state recoloured.** From the Northwind demo (`demo-bfb-copy`). The code is
fixed Text and the label stays the default Copy; **Colour** `doneColor` and **Background** `doneBackground` under
After copying style the confirmation. The demo stores `doneBackground` as a bare colour, which writes no CSS, so
this tree uses the Background shape that does.

```json
{
  "name": "bfbe-copy",
  "settings": {
    "text": "FIRSTBAG20", "successLabel": "Copied",
    "doneColor": { "hex": "#6e44ff" },
    "doneBackground": { "color": { "hex": "#f0ecff" } }
  }
}
```

**Copy the text of another element.** From the fixture page `fixture-copy` (selector source, icon right, custom
labels, never resets). Both icons are set so neither state shows a gap, and `resetAfter: 0` keeps Code copied on
screen. The fixture targets `#coupon`; here the target is a Basic Text carrying a class, as Wiring asks.

```json
{
  "name": "block",
  "settings": {},
  "children": [
    { "name": "text-basic", "settings": { "text": "WELCOME-2026", "_cssClasses": "coupon-code" } },
    {
      "name": "bfbe-copy",
      "settings": {
        "source": "selector", "selector": ".coupon-code",
        "label": "Copy code", "successLabel": "Code copied",
        "icon": { "library": "themify", "icon": "ti-files" },
        "successIcon": { "library": "themify", "icon": "ti-check" },
        "iconPosition": "right",
        "resetAfter": 0
      }
    }
  ]
}
```

**One button per post, in a query loop.** Built from the schema; no demo or fixture page loops this element. The
element's own `hasLoop` repeats the button and `{post_url}` in Text resolves for each post. The same Text works on a
Copy button inside a looped Block card, beside the post title.

```json
{
  "name": "bfbe-copy",
  "settings": {
    "hasLoop": true,
    "query": { "post_type": ["post"], "posts_per_page": 3 },
    "text": "{post_url}",
    "label": "Copy link", "successLabel": "Link copied"
  }
}
```

## Gotchas

- **Nothing to copy means no button.** An empty Text, a dynamic tag that resolves empty, or the selector source with
  no CSS selector renders nothing on the page and a notice in the canvas. <!-- src: plugins/bfb-elements/elements/copy.php:254-270 -->
- **The selector takes the first match on the page.** Every button reading `.coupon-code` copies the first
  `.coupon-code`, so in a query loop or a component placed twice all of them copy the same value. <!-- src: src/elements/copy/copy.js:39 -->
- **A form field gives its value, anything else its visible text.** A `select` copies the chosen option's `value`,
  which can differ from the words shown; an empty input copies nothing. <!-- src: src/elements/copy/copy.js:41,53 -->
- **A failed copy is silent.** A selector that is invalid or matches nothing, or a clipboard write the browser
  refuses, adds no `is-copied` and announces nothing. <!-- src: src/elements/copy/copy.js:39-40,53,63 -->
- **Bricks' own Background or Border hides the default copied look.** They write to `#brxe-{id}`, which outranks
  `.bfbe-copy.is-copied`; style the idle button and you must set `doneBackground`, `doneBorder` or `doneColor` too. <!-- src: src/elements/copy/copy.css:13; docs/API-PROBE.md "8. The css control mapping" -->
- **Background controls take an object.** `doneBackground` and `hoverBackground` need `{"color": {"hex": "#f0ecff"}}`;
  a bare `{"hex": ...}` saves but writes no CSS. `doneColor` and `hoverColor` take the bare form. <!-- src: docs/SESSION-HANDOFF.md:1162 "Demo data slips"; measured on demo-bfb-copy 2026-10-08: only #brxe-5121c3.is-copied {color} is printed -->
- **Set both icons or neither.** The two icons share one cell that keeps its size in both states, so a lone Icon
  leaves a blank gap once copied, and a lone Icon after copying leaves one before. <!-- src: src/elements/copy/copy.css:8-11; plugins/bfb-elements/elements/copy.php:276-293 -->
- **The button is as wide as its longer label.** Both labels stack in one grid cell so the width never jumps, which
  means a long **Label after copying** `successLabel` widens the idle button too. <!-- src: src/elements/copy/copy.css:2,8-9 -->
- **Icon Colour beats the copied Colour on the icon.** `iconColor` is set on `.bfbe-copy__icon` itself, so the done
  icon keeps it while `doneColor` recolours the label; leave `iconColor` empty to let the icon follow. <!-- src: plugins/bfb-elements/elements/copy.php:145-151,193-199 -->
- **A Label that resolves empty leaves the button nameless.** An empty **Label** falls back to Copy, but a dynamic
  tag that resolves to nothing prints an empty label, and both icons are `aria-hidden`. <!-- src: plugins/bfb-elements/includes/abstract-element.php:1265-1273; plugins/bfb-elements/elements/copy.php:231,278 -->
- **Custom curve needs Easing set to Custom.** `easingCustom` writes `--bfbe-ease-custom`, which is read only when
  `easing` is `"var(--bfbe-ease-custom, ease)"`. <!-- src: plugins/bfb-elements/includes/abstract-element.php:1067-1082 -->
- **Verify on the frontend, with clipboard permission.** The canvas draws the root as a `<div>` without `type`. A
  headless browser refuses the write unless granted `clipboardReadWrite` and `clipboardSanitizedWrite`, and then no
  `is-copied` appears. <!-- src: plugins/bfb-elements/elements/copy.php:241,248-252; plugins/bfb-elements/includes/abstract-element.php:419-421; src/elements/copy/copy.js:19,54-63; dev/demo/features.mjs:108-109 -->

## Never do

- Do not use `source: "selector"` for content that repeats on the page; copy it with `text` and dynamic data.
- Do not point `selector` at a `_cssId`; give the target a class in `_cssClasses`.
- Do not write a bare colour into `doneBackground` or `hoverBackground`; wrap it as `{"color": {...}}`.
- Do not style the button with Bricks' Background or Border without setting the After copying styles as well.
- Do not set `icon` without `successIcon`, or `successIcon` without `icon`.
- Do not set `easingCustom` unless `easing` is `"var(--bfbe-ease-custom, ease)"`.
- Do not make **Label** a lone dynamic tag that can resolve empty.
- Do not add `aria-label`, `role` or `tabindex` through `_attributes`; the name comes from the visible label.
