---
name: bfbe-age-gate
description: "Use when a page needs an age check or age verification before it can be used, built with BFB Age Gate (`bfbe-age-gate`): a yes or no such as I am 18 or older, or a date of birth checked against a minimum age, with a remembered pass and a redirect on fail. Read before writing its settings."
---

# BFB Age Gate (`bfbe-age-gate`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-age-gate.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/age-gate/

## What it is
A gate shown before the page can be used: a yes or no question, or a date of birth checked against a minimum age. It is built on a native dialog with no close button and no Escape, so the answers are the way through. A pass is remembered for the days you choose, and a failed answer can send the visitor to another address.

**Not for:** It confirms what a visitor says and nothing more: the date is checked in the browser, and the page's content stays in the HTML underneath. The gate opens from script, so a visitor with scripts off sees the page, and whether you need one is a question for your lawyer.

**Costs a page:** CSS 1.20 KB, JS 1.32 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** yes · **In a query loop:** no · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Nestable: any Bricks element goes inside (blocks, headings, text, images, a form).
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-age-gate",
    "settings": {},
    "children": [
        {
            "name": "heading",
            "settings": {
                "text": "Are you old enough?",
                "tag": "h2"
            }
        },
        {
            "name": "text-basic",
            "settings": {
                "text": "You must be of legal age to enter this site."
            }
        }
    ]
}
```

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Gate (`bfbeGate`)
- `mode` (select) **Ask for**: options: `confirm` A yes or no (default), `dob` A date of birth. A yes or no, the default, shows two buttons. A date of birth shows day, month and year fields, checked against the Minimum age.
- `minAge` (number) **Minimum age**. The age a visitor must be, 18 unless set. Empty button labels use it too.
- `remember` (number) **Remember for (days)**. How long a pass is kept in the visitor's browser, 30 unless set. Enter 0 to keep it until the browser tab is closed.
- `redirect` (text) **Redirect on fail**: placeholder https://example.com; dynamic data accepted. An address to send the visitor to about 1.5 seconds after a failed answer. It can come from dynamic data.
- `skipLoggedIn` (checkbox) **Skip for logged-in users**. Off by default. Tick it to let logged-in users skip the gate. A logged-in administrator still sees it on every load, and a pass is never stored for them.

### Labels and messages (`bfbeText`)
- `yesLabel` (text) **Yes button**: placeholder I am 18 or older; dynamic data accepted; only when `mode` is not `dob`. The words on the button that passes. Left empty, it reads I am 18 or older, using the Minimum age.
- `noLabel` (text) **No button**: placeholder I am under 18; dynamic data accepted; only when `mode` is not `dob`. The words on the failing button. Left empty, it reads I am under 18, with the number from Minimum age. It takes dynamic data like the other labels.
- `dobLabel` (text) **Date field label**: placeholder Your date of birth; dynamic data accepted; only when `mode` is `dob`. With A date of birth, the caption over the three boxes, Your date of birth unless set.
- `invalidText` (text) **Invalid date message**: placeholder Enter a real date.; dynamic data accepted; only when `mode` is `dob`. Shown for a date that cannot exist, such as 31 February. It is kept apart from a failed answer, and reads Enter a real date unless you set it.
- `enterLabel` (text) **Enter button**: placeholder Enter; dynamic data accepted; only when `mode` is `dob`. With A date of birth, the words on the button that sends the date, Enter unless set.
- `failText` (text) **Fail message**: placeholder Sorry, you are not old enough to enter this site.; dynamic data accepted. Shown after a failed answer and announced to screen readers. The default reads Sorry, you are not old enough to enter this site.

### Panel (`bfbePanel`)
Styling only, every key in the schema file: `width`, `panelBackground`, `panelColor`, `panelPadding`, `panelBorder`, `panelShadow`, `overlay`, `overlayBlur`, `messageColor`, `messageTypography`.

### Buttons (`bfbeButtons`)
Styling only, every key in the schema file: `buttonsAlign`, `buttonTypography`, `buttonPadding`, `buttonBorder`, `buttonGap`, `yesBackground`, `yesBackgroundHover`, `yesColor`, `noBackground`, `noBackgroundHover`, `noColor`.

### Date field (`bfbeField`)
The whole group shows only when `mode` is `dob`.
- `partLabels` (checkbox) **Day, month, year labels**: only when `mode` is `dob`. Unticked, the words stay for screen readers while DD, MM and YYYY show as placeholders. Tick it to draw the words above the boxes.
- `fieldOrder` (select) **Order**: options: `site` Follow the site date format (default), `dmy` Day, month, year, `mdy` Month, day, year, `ymd` Year, month, day; only when `mode` is `dob`. The order of the day, month and year fields. Follow the site date format is the default. Or fix it to start with the day, the month or the year.
- `fieldWidth` (select) **Widths**: options: `fill` Fill the row (default), `compact` Compact; only when `mode` is `dob`. Fill the row is the default, so the three fields share the width. Choose Compact for short boxes sized to their digits.
- `fieldAlign` (select) **Align**: options: `start` Start (default), `center` Centre, `end` End; writes CSS; only when `mode` is `dob`. Choose Start, Centre or End. It places the date field's caption and, with Compact widths, the row of boxes.
Styling, in the schema file: `fieldTypography`, `partLabelTypography`, `fieldGap`, `inputTypography`, `placeholderColor`, `inputBackground`, `inputBorder`, `inputPadding`, `inputShadow`, `inputFocusBackground`, `inputFocusBorderColor`, `inputFocusShadow`.

### Motion (`bfbeMotion`)
- `effect` (select) **Effect**: options: `fade` Fade (default), `rise` Rise, `scale` Scale, `none` None. How the gate arrives and leaves. Choose Fade, the default, Rise, Scale or None.
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS. The curve the gate moves on, Snappy unless set.
Styling, in the schema file: `duration`, `easingCustom`.

## What it guarantees for accessibility (do not undo)
- On the page the gate is a native modal dialog, so the rest of the page is inert while it is open.
- Escape is ignored and there is no close button; the dialog closes when an answer passes, and reopens if anything else closes it.
- The dialog is named by the heading in the nested content and described by that content.
- Failed and invalid answers are announced through a region with role alert.
- The date of birth is a fieldset with a legend and three labeled inputs, with a numeric keyboard and birthday autofill values.
- Filling a box moves focus to the next, and Enter submits the form.
- Under reduced motion the gate and its overlay appear and leave with no transition.
<!-- bfbe:generated:end -->

## Rendered DOM

The root is Bricks' own box (`#brxe-...`, class `bfbe-gate`). It stays where it is placed, 0 px tall, and the script opens the dialog in the top layer with `showModal()` on arrival.

```html
<div id="brxe-..." class="bfbe-gate bfbe-gate--confirm bfbe-gate--fx-fade" data-bfbe-min="18" data-bfbe-remember="30"
     data-bfbe-redirect="..." data-bfbe-invalid="..." data-bfbe-fail="...">
  <dialog class="bfbe-gate__dialog" id="bfbe-...-dialog" aria-labelledby="(the heading's id)" aria-describedby="bfbe-...-title">
    <div class="bfbe-gate__panel">
      <div class="bfbe-gate__content" id="bfbe-...-title"><!-- the nested elements --></div>
      <form class="bfbe-gate__form" data-bfbe-gate-form>
        <fieldset class="bfbe-gate__field bfbe-gate__field--dob"><legend>...</legend>          <!-- dob -->
          <div class="bfbe-gate__parts">
            <label class="bfbe-gate__part bfbe-gate__part--d"><span class="bfbe-sr">Day</span><input name="dob-d" maxlength="2" autocomplete="bday-day" required></label>
            <!-- then --m (dob-m) and --y (dob-y, maxlength 4), in the chosen order -->
          </div></fieldset>
        <div class="bfbe-gate__actions">
          <button type="submit" class="bfbe-gate__btn bfbe-gate__btn--yes"><span>...</span></button>
          <button type="button" class="bfbe-gate__btn bfbe-gate__btn--no" data-bfbe-gate-no><span>...</span></button> <!-- confirm -->
        </div>
        <p class="bfbe-gate__message" role="alert" hidden></p>
      </form></div></dialog></div>
```

- `mode` and `effect` are root classes (`bfbe-gate--dob`, `bfbe-gate--fx-rise`). `fieldWidth: "compact"` adds `bfbe-gate__field--compact`; ticking `partLabels` drops `bfbe-sr` from the day, month and year words.
- In the builder the root adds `bfbe-gate--canvas` and the dialog is a `div`. For a logged-in administrator the root carries `data-bfbe-review="1"`.
- While it asks: `dialog[open]` and `html.bfbe-gate-lock` (page scroll off). A fail or an impossible date un-hides `.bfbe-gate__message` with the root's `data-bfbe-fail` or `data-bfbe-invalid` text.
- A pass closes the dialog and stores `bfbe-gate-pass-<minAge>` in `localStorage` (an expiry time in ms), or `"1"` in `sessionStorage` when `remember` is 0.
- Custom properties on the root: `width` (`--bfbe-gate-w`, 480px, never wider than the window less 32px), `overlay` and `overlayBlur` (painted on `::backdrop`), `messageColor`, `fieldAlign`, `duration`, `easing`, and all six button colours (`--bfbe-gate-btn`, `-btn-hover`, `-on-btn`, `-btn-no`, `-btn-no-hover`, `-on-btn-no`).
- Written to parts: the panel keys to `.bfbe-gate__panel` (default `Canvas` on `CanvasText`, text centred); `buttonTypography`, `buttonPadding`, `buttonBorder` to `.bfbe-gate__btn`; `buttonsAlign`, `buttonGap` to `.bfbe-gate__actions`; `fieldGap` to `.bfbe-gate__parts`; the input keys to `.bfbe-gate__field input` and `input:focus`; `fieldTypography` to the `legend`; `partLabelTypography` to `.bfbe-gate__part > span`; `messageTypography` to `.bfbe-gate__message`.

## Wiring to other elements

Stands alone: no attribute points at it and it points at nothing. Three things reach past its box.

- **Events.** A pass dispatches `bfbe/gate/pass` and a fail `bfbe/gate/fail` from the root, both bubbling. Listen on `document` and tell gates apart by a class in `_cssClasses` on `event.target`, never by `_cssId`: component instances share ids.
- **One pass per age, across the site.** Every gate with the same `minAge` reads the same stored pass, so one answer opens every 18 gate on the site, and a 21 gate still asks.
- **Dark Mode Toggle.** Under its dark state the Yes button's words, with no `yesColor` set, turn black or white from the button's fill.

## Verified patterns

A yes or no gate, from the demo page `demo-bfb-age-gate`: `mode: "confirm"` with both labels, a 30-day pass, a fail that redirects, and the brand colours through the button keys. Two changes from the page: the demo's real redirect address is a placeholder, and `panelBackground` carries its colour under `color`, which the demo leaves out (so its panel paints nothing).

```json
{
  "name": "bfbe-age-gate",
  "settings": {
    "mode": "confirm", "minAge": 18, "remember": 30, "skipLoggedIn": true,
    "yesLabel": "I am 18 or over", "noLabel": "I am not", "redirect": "https://example.com/",
    "effect": "fade", "overlay": { "raw": "rgba(16, 24, 40, 0.5)" }, "overlayBlur": "6px",
    "panelBackground": { "color": { "hex": "#ffffff" } }, "panelColor": { "hex": "#101828" },
    "yesBackground": { "hex": "#6e44ff" }, "yesColor": { "hex": "#ffffff" },
    "noBackground": { "hex": "#f7f8fa" }, "noColor": { "hex": "#101828" }
  },
  "children": [
    { "name": "text-basic", "settings": { "text": "Two Harbours", "tag": "p" } },
    { "name": "heading", "settings": { "text": "Old enough for this?", "tag": "h2" } },
    { "name": "text-basic", "settings": { "text": "You need to be 18 to come in. We will ask once and then leave you alone for a month.", "tag": "p" } }
  ]
}
```

A date of birth gate at 21, from the fixture page `fixture-age-gate`: `mode: "dob"` with `minAge: 21`, a pass kept for one day, and the Scale effect on the Overshoot curve over 700 ms.

```json
{
  "name": "bfbe-age-gate",
  "settings": {
    "mode": "dob", "minAge": 21, "remember": 1, "redirect": "https://example.com", "skipLoggedIn": true,
    "effect": "scale", "duration": 700, "easing": "cubic-bezier(0.34, 1.56, 0.64, 1)"
  },
  "children": [
    { "name": "heading", "settings": { "text": "Are you 21?", "tag": "h2" } },
    { "name": "text-basic", "settings": { "text": "Enter your date of birth." } }
  ]
}
```

A styled date field, from the fixture page `fixture-age-gate-styled`: day, month, year in compact boxes, centred, dark inputs with an amber ring on focus, and a pass kept until the tab closes (`remember: 0`). Its `buttonsAlign` and an empty `partLabels` are left out (see Gotchas), and the explanation line is the element's default.

```json
{
  "name": "bfbe-age-gate",
  "settings": {
    "mode": "dob", "minAge": 18, "remember": 0,
    "fieldOrder": "dmy", "fieldWidth": "compact", "fieldAlign": "center", "fieldGap": "16px",
    "fieldTypography": { "font-weight": "700" },
    "inputBackground": { "color": { "hex": "#1f2937" } },
    "inputTypography": { "color": { "hex": "#ffffff" }, "font-size": "20px" },
    "placeholderColor": { "hex": "#9ca3af" },
    "inputPadding": { "top": "14", "right": "10", "bottom": "14", "left": "10" },
    "inputFocusBorderColor": { "hex": "#e0a020" },
    "inputFocusShadow": { "values": { "offsetX": 0, "offsetY": 0, "blur": 0, "spread": 3 }, "color": { "hex": "#e0a020" } }
  },
  "children": [
    { "name": "heading", "settings": { "text": "How old are you?", "tag": "h2" } },
    { "name": "text-basic", "settings": { "text": "You must be of legal age to enter this site." } }
  ]
}
```

## Gotchas

- **Background controls want an object.** `panelBackground`, `inputBackground` and `inputFocusBackground` are Background controls, so the colour goes under `color`: `{"color": {"hex": "#ffffff"}}`. A bare `{"hex": ...}` writes no CSS at all. <!-- src: docs/SESSION-HANDOFF.md:1162 "Demo data slips"; plugins/bfb-elements-pro/elements/age-gate.php:189; measured on demo-bfb-age-gate 2026-10-08, no panel background rule printed -->
- **Buttons sit moves nothing.** Two answers grow to share the row and the Enter button takes all of it, so **Buttons sit** (`buttonsAlign`) has no free space to place them. <!-- src: src/elements/age-gate/age-gate.css:54-55; measured 2026-10-08: demo buttons 236 + 8 + 188 = 432 of 432 px, styled fixture Enter 432 of 432 px under space-between -->
- **Button colours are custom properties.** The Yes words sit in a span with a colour of their own, so set **Text** (`yesColor`); a colour inside **Typography** (`buttonTypography`) reaches the No button and not the Yes. Custom CSS that writes `background` onto `.bfbe-gate__btn` outranks the hover rule. <!-- src: src/elements/age-gate/age-gate.css:45-52; plugins/bfb-elements-pro/elements/age-gate.php:327-331 -->
- **An administrator always gets the gate.** Logged in with `manage_options`, the gate shows on every load whatever `skipLoggedIn` says, and no pass is stored. With `skipLoggedIn` ticked, other logged-in users get no markup at all. <!-- src: plugins/bfb-elements-pro/elements/age-gate.php:676-681; src/elements/age-gate/age-gate.js:30-53 -->
- **A pass belongs to the age, not the gate.** The key is `bfbe-gate-pass-<minAge>` and its expiry is fixed when the visitor passes, so a later change to **Remember for** (`remember`) leaves stored passes as they are. Remove that key from the browser's storage to see the gate again. <!-- src: src/elements/age-gate/age-gate.js:26-53 -->
- **A fail does not lock.** No, or a date under the age, shows **Fail message** (`failText`) and leaves the gate open with nothing stored, so the visitor can answer again. **Redirect on fail** (`redirect`) is what moves them, about 1.5 seconds later. <!-- src: src/elements/age-gate/age-gate.js:63-67 -->
- **An impossible date is not a fail.** 31 February, a 0 or a two-digit year shows **Invalid date message** (`invalidText`) and never redirects. Empty boxes are stopped earlier by the browser's own required check. <!-- src: src/elements/age-gate/age-gate.js:89-105 (new Date reads a year under 100 as 19xx); plugins/bfb-elements-pro/elements/age-gate.php:663 -->
- **The canvas shows it settled.** In the builder the dialog is a `div` in the flow with a dashed outline: no overlay, no motion, no scroll lock. Check those on the page, logged out. <!-- src: plugins/bfb-elements-pro/elements/age-gate.php:701-705; src/elements/age-gate/age-gate.css:60-62 -->
- **Keep a heading among the children.** The dialog takes its name from the heading (h1 to h6) that comes earliest in its content; with none, it is named by every word in it. With no children the page shows the buttons alone. <!-- src: src/elements/age-gate/age-gate.js:16-23; plugins/bfb-elements-pro/elements/age-gate.php:710-717 -->
- **The panel's shadow is clipped.** The dialog is exactly the panel's size and clips its overflow, so a **Shadow** (`panelShadow`) is cut off at the panel's box, square at the corners. <!-- src: docs/SESSION-HANDOFF.md:1157 "Plugin defects found on the way"; src/elements/age-gate/age-gate.css:3; measured 2026-10-08: dialog overflow auto, dialog and panel both 480 px -->
- **The date caption sits at the start.** The panel centres its text, but the legend follows **Align** (`fieldAlign`), Start by default. With Fill the row widths, Align moves the legend alone; set `fieldAlign: "center"` to line it up with a centred heading. <!-- src: src/elements/age-gate/age-gate.css:18-28; plugins/bfb-elements-pro/elements/age-gate.php:473-476 -->
- **Follow the site date format reads one letter.** The opening letter of the WordPress date format decides: m, n, F or M leads with the month, Y with the year, anything else with the day, so `l, F j, Y` leads with the day. Set `fieldOrder` when the order matters. <!-- src: plugins/bfb-elements-pro/elements/age-gate.php:643-649 -->

## Never do

- Do not pass a bare colour to `panelBackground`, `inputBackground` or `inputFocusBackground`; put it under `color`.
- Do not count on `buttonsAlign` to place the buttons.
- Do not write button backgrounds onto `.bfbe-gate__btn` in custom CSS; set `yesBackground`, `noBackground` and their hover keys.
- Do not set `noLabel`, `noBackground`, `noBackgroundHover` or `noColor` with `mode: "dob"`: that gate has no No button.
- Do not judge the remembered pass while logged in as an administrator.
- Do not leave the gate without a heading among its children.
- Do not add a close button or an interaction that closes the dialog: the gate reopens until an answer passes.
- Do not treat a No as a lock; set `redirect` when a fail must leave the page.
