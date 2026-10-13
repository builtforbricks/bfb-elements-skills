---
name: bfbe-toast
description: "Use when placing, wiring or styling BFB Toast (`bfbe-toast`): a short message that slides in at a corner of the window and closes by itself, holding any elements you nest in it. Read before writing its settings."
---

# BFB Toast (`bfbe-toast`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.1.1 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-toast.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/toast/

## What it is
A short message that slides in at a corner of the window and closes by itself, holding any elements you nest in it. It shows after the page loads, when an element is clicked, when a form sends or fails, or from any Bricks interaction. Toasts in one corner stack, each closes after its time, 6 s unless you set one, and the time stops while the pointer or the focus is on it or the browser tab is hidden. It never takes focus, and screen readers hear its words each time it shows.

**Not for:** Not for a message that must be answered or must stay in view: use Modal for a dialog. A toast does not send email or store anything on the site. It is shown by its script, so a visitor with scripts off never sees it.

**Costs a page:** CSS 0.97 KB, JS 2.19 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** yes · **In a query loop:** no · **Dynamic data:** no · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Nestable: any Bricks element goes inside (blocks, headings, text, images, a form).
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-toast",
    "settings": {},
    "children": [
        {
            "name": "text-basic",
            "settings": {
                "text": "Thanks, your message is on its way."
            }
        }
    ]
}
```

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### When it shows (`bfbeWhen`)
- `trigger` (select) **Show**: options: `load` After the page loads (default), `click` When an element is clicked, `form` When a form sends, `formError` When a form fails, `manual` Only from an interaction. After the page loads is the default. Choose When an element is clicked, When a form sends, When a form fails, or Only from an interaction, which waits for a Bricks interaction to show it.
- `delay` (number) **Delay (s)**: placeholder 2; only when `trigger` is `` or `load`. For After the page loads, how long it waits, 2 by default.
- `clickSelector` (text) **Element (CSS selector)**: placeholder .add-to-wishlist; only when `trigger` is `click`. For When an element is clicked, type the selector of the element that shows it, such as .add-to-wishlist. Until you do, the toast is left out of the page.
- `formSelector` (text) **Form (CSS selector)**: placeholder #brxe-abc123; only when `trigger` is `form` or `formError`. For When a form sends and When a form fails. Leave it empty to listen to any form on the page, Bricks' own form and BFB Advanced Forms alike, or type one form's selector, such as #brxe-abc123.
- `again` (select) **Show it again**: options: `each` On every page view (default), `visit` Once per visit, `once` Only once; only when `trigger` is `` or `load`. For After the page loads. On every page view is the default. Choose Once per visit or Only once instead; it is remembered in the visitor's browser.
- `key` (text) **Message key**: placeholder welcome; only when `trigger` is `` or `load` and `again` is `visit` or `once`. For Once per visit and Only once, the name it is remembered under, such as welcome. Change it to show the toast again.

### Toast (`bfbeToast`)
- `corner` (select) **Corner**: options: `bottom-right` Bottom right (default), `bottom-left` Bottom left, `bottom-center` Bottom centre, `top-right` Top right, `top-left` Top left, `top-center` Top centre. Bottom right is the default. Choose Bottom left, Bottom centre, Top right, Top left or Top centre instead. Toasts in one corner stack 12px apart.
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS. How it speeds up and slows down, Snappy by default. Pick Custom and type your own curve in Custom curve.
Styling, in the schema file: `width`, `offset`, `duration`, `easingCustom`.

### Closing (`bfbeClose`)
- `closeAfter` (number) **Closes after (s)**: placeholder 6. 6 by default. Type 0 to keep it until it is closed. The time stops while the pointer or the focus is on the toast or the browser tab is hidden.
- `timeLeft` (checkbox) **Show the time left**. Tick it to draw a bar along the toast's foot that empties over its time. Time left colour sets the bar's colour.
- `noClose` (checkbox) **Hide the close button**. Tick it to take the close button away. Close button colour sets its colour while it is there.
Styling, in the schema file: `barColor`, `closeColor`.

### bfbeBuilder (`bfbeBuilder`)
- `builderView` (select) **Show it**: options: `open` In place, so you can style it (default), `live` Working, as on the site. In place, so you can style it is the default. Working puts it in its corner and lets its trigger show it, as on the site.

## What it guarantees for accessibility (do not undo)
- The toast never takes focus: it appears without moving the visitor's place on the page.
- Screen readers hear its words through a polite live region the script keeps on the page, or an assertive one for a form that failed, once each time it shows.
- Its time stops while the pointer or the keyboard focus is on it and while the browser tab is hidden, so its words can be read and its buttons reached before it closes.
- The close button is a real button named Close, so it answers Enter and Space, and Escape closes the toast while the focus is inside it.
- Under reduced motion the toast appears and leaves without sliding or fading, and the time-left bar is left out.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<div id="brxe-{id}" class="brxe-bfbe-toast bfbe-toast bfbe-toast--bottom-right" data-bfbe-toast="load"
     data-bfbe-toast-after="6000" data-bfbe-toast-delay="2000" hidden>
  <div class="bfbe-toast__body">… the nested elements …</div>
  <button type="button" class="bfbe-toast__close" aria-label="Close"><svg viewBox="0 0 16 16" aria-hidden="true" focusable="false">…</svg></button>
  <span class="bfbe-toast__bar" aria-hidden="true"></span>
</div>
<!-- added to the end of <body> the first time a toast shows, one per kind, kept for the page's life; a toast lifted into an open dialog speaks through a pair at the end of that dialog -->
<div class="bfbe-toast-live" aria-live="polite" aria-atomic="true">… the last toast's words …</div>
```

- The root is the card itself: `bfbe-toast--{corner}` and `data-bfbe-toast` (the trigger: `load`, `click`, `form`, `formError`, `manual`). `data-bfbe-toast-after` is **Closes after** in ms, `0` to keep it. Only `load` writes `data-bfbe-toast-delay` (ms), and with `again` at `visit` or `once` also `data-bfbe-toast-again` and `data-bfbe-toast-key="bfbe-toast-{key}"`. `click`, and `form` or `formError` with a selector, write the selector in `data-bfbe-toast-on`.
- On the site the root always renders `hidden`; the script removes it to show the toast. In the canvas, **Show it** `builderView` unset adds `bfbe-toast--canvas` (in the flow, fully drawn, script idle); `live` renders `hidden` with `data-bfbe-live="1"`, as on the site.
- `.bfbe-toast__close` renders unless **Hide the close button** `noClose` is ticked. `.bfbe-toast__bar` renders only with `timeLeft` ticked and `closeAfter` above 0.
- States: `is-open` (no `hidden`) while shown, `is-in` a frame later (full opacity, no shift), `is-timing` while the bar runs, `is-paused` while held, `is-leaving` during the exit, then `hidden` again. The script writes `--bfbe-toast-stack` (px lifted by the open toasts before it in its corner) and `--bfbe-toast-time` inline on the root. Shown while a modal dialog is open, the root also carries `popover="manual"` and sits inside that `dialog`, with an HTML comment ` bfbe-toast ` left where it came from; both go when it closes.
- `.bfbe-toast-live` is visually hidden. A toast with `trigger: "formError"` speaks in the `assertive` region, every other in the `polite` one. The words are the text of `.bfbe-toast__body` alone, emptied and written again 60ms later, so the same words twice are said twice.
- The card's own CSS: `position: fixed`, `inset: auto`, `margin: 0`, `z-index: 99990`, `inline-size: min(var(--bfbe-toast-w), 100vw - 2 * var(--bfbe-toast-edge))`, a flex row (body, then close button) aligned to the top, `padding: 14px 16px`, a 1px `--bfbe-line` border, the pack's radius and shadow, `overflow: hidden`, a solid `#ffffff` background and `#101828` text. `.bfbe-toast__body` is a flex column spaced by the pack's small gap. Closed (no `is-open`, outside the canvas), it is `visibility: hidden; pointer-events: none` as well as `hidden`.
- Where controls write: `width` and `offset` set `--bfbe-toast-w` (360px) and `--bfbe-toast-edge` (24px) on the root; `duration` and `easing` set `--bfbe-duration` and `--bfbe-ease`; `barColor` is the background of `.bfbe-toast__bar` (the pack's accent unless set); `closeColor` is the colour of `.bfbe-toast__close`. Bricks' own `_background`, `_border`, `_padding`, `_boxShadow` and `_typography` style the card, since the root is the card.

## Wiring to other elements

- **By class, never by id.** Give the element that shows the toast, the form, and the toast itself a class in `_cssClasses`, and point `clickSelector`, `formSelector` and interaction targets at those classes. Component instances share ids.
- **Click** (`trigger: "click"`, `clickSelector: ".add-to-wishlist"`): one listener on the document; a click on a matching element or anything inside it shows every click toast whose selector matches. The click's default is not cancelled, so a link to another page leaves before the toast is read. Clicking again while the toast is open starts its time over and says its words again.
- **Form** (`trigger: "form"` or `"formError"`): listens for Bricks' `bricks/form/success` and `bricks/form/error` on the document. Without `formSelector` any form on the page shows it. With one, the form is found from the event's `detail.elementId`, as `form[data-element-id]`, then `[data-script-id]`, then `#brxe-{id}`, and matches when the form itself or a box around it matches the selector. Bricks' **Form** and BFB Advanced Forms (`bfbe-form`) both send these events; both were sent for real in `dev/toast-forms-probe.mjs`, each with a toast aimed at it by class, plus a toast for any form.
- **Bricks Interactions** (`trigger: "manual"`, or any trigger, since a script can show any toast): on the element that should show it, add an interaction with the action **JavaScript (Function)**, **Target** CSS selector naming the toast's class, **Function name** `bfbeToast.show` and the argument `%brx%`. As settings: `"_interactions": [{ "id": "tsint1", "trigger": "click", "action": "javascript", "target": "custom", "targetSelector": ".toast-saved", "jsFunction": "bfbeToast.show", "jsFunctionArgs": [{ "id": "tsarg1", "jsFunctionArg": "%brx%" }] }]`. Bricks calls the function once per target with `%brx%.target` set to it. `bfbeToast.hide` closes it the same way.
- The argument may also be a selector string (`".toast-saved"`) or an element. With **Target** left at Self, `%brx%` carries the clicked element, not the toast, and nothing shows.
- **Your own script**: `window.bfbeToast.show(".toast-saved")` and `window.bfbeToast.hide(...)` take a selector, an element, or an object with `target` or `targets`. `window.bfbeToast()` initialises toasts added to the page later; click, form and interaction toasts are looked up when their event fires, so only a later `load` toast needs it.
- The toast dispatches no events of its own and adds nothing to the element that shows it: no role, `aria-*` or `tabindex`.

## Verified patterns

**A toast on Add to bag, with its time left** (demo page `demo-bfb-toast`, `.toast-bag`). The demo's two Add to bag buttons are Bricks Buttons linking to `#bag` with the class `hollis-add`; a click on either shows this toast for 6 seconds with a bar emptying along its foot. The demo's load toast sits earlier in the page in the same corner, so this one stacks above it. The demo's ink and muted text colours are left out (Gotchas: BFB Dark Mode).

```json
{
  "name": "bfbe-toast",
  "settings": { "_cssClasses": "toast-bag", "trigger": "click", "clickSelector": ".hollis-add", "closeAfter": "6", "timeLeft": true, "barColor": { "hex": "#6e44ff" }, "corner": "bottom-right", "width": "340px", "_border": { "width": { "top": 1, "right": 1, "bottom": 1, "left": 1 }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": 16, "right": 16, "bottom": 16, "left": 16 } }, "_padding": { "top": "16", "right": "18", "bottom": "16", "left": "20" } },
  "children": [
    { "name": "text-basic", "settings": { "text": "Added to your bag", "tag": "p", "_typography": { "font-size": "15px", "font-weight": "600" }, "_margin": { "bottom": "0" } } },
    { "name": "text-basic", "settings": { "text": "Delivered by Thursday. Free returns for thirty days.", "tag": "p", "_typography": { "font-size": "14px" }, "_margin": { "bottom": "0" } } }
  ]
}
```

**A newsletter form and the toast for its send** (feature-visual page `bfb-toast`, "When a form sends"). The Bricks `form` carries `actions: ["email"]`, which on the site sends Bricks' Email action for real to the admin address; a form with no action fails with "No action has been set for this form." The toast has no `formSelector`, so any form on the page shows it; add `formSelector: ".nl-form"` to answer this form alone. `closeAfter: "0"` keeps it until it is closed. The page's form and text styling is left out, and the two are wrapped in a Block here.

```json
{
  "name": "block",
  "settings": {},
  "children": [
    { "name": "form", "settings": { "_cssClasses": "nl-form", "fields": [ { "id": "nlmail", "type": "email", "label": "Email", "placeholder": "you@example.com", "required": true } ], "actions": [ "email" ], "emailSubject": "The Hollis letter", "emailTo": "admin_email", "successMessage": "Thank you.", "submitButtonText": "Subscribe" } },
    { "name": "bfbe-toast", "settings": { "trigger": "form", "corner": "bottom-right", "closeAfter": "0", "width": "340px" }, "children": [
      { "name": "text-basic", "settings": { "text": "You are on the list", "tag": "p", "_typography": { "font-weight": "600" }, "_margin": { "bottom": "0" } } },
      { "name": "text-basic", "settings": { "text": "The first letter comes on Friday.", "tag": "p", "_margin": { "bottom": "0" } } }
    ] }
  ]
}
```

**A failure toast for one form** (fixture page `fixture-toast`, `.t-err`). Shows at the top centre when the form with the class `probe-form` fails, said in the assertive region. In the fixture `.probe-form` is a stand-in whose events the probe fires; on a real page put the class in the form's `_cssClasses`.

```json
{ "name": "bfbe-toast", "settings": { "_cssClasses": "t-err", "trigger": "formError", "formSelector": ".probe-form", "corner": "top-center", "closeAfter": 0 }, "children": [ { "name": "text-basic", "settings": { "text": "That did not send. Please try again." } } ] }
```

**Shown once, ever, after the page loads** (fixture page `fixture-toast`, `.t-once`). The default `trigger` is `load`; `delay: 0.2` shows it 0.2s after the page is ready, and `again: "once"` with `key: "probe-once"` stores `bfbe-toast-probe-once` in the visitor's localStorage, so the next page view skips it. Use `again: "visit"` for once per visit.

```json
{ "name": "bfbe-toast", "settings": { "_cssClasses": "t-once", "delay": 0.2, "again": "once", "key": "probe-once", "corner": "top-left", "closeAfter": 0 }, "children": [ { "name": "text-basic", "settings": { "text": "This shows only once." } } ] }
```

## Gotchas

- **The stack follows page order, not showing order.** Open toasts in one corner stack 12px apart with the one earliest in the page at the edge, whichever showed first; a toast earlier in the page that shows later takes the edge and lifts the others. The stack is measured when a toast shows or leaves and on resize. <!-- src: src/elements/toast/toast.js:38 ; src/elements/toast/toast.js:105 ; src/elements/toast/toast.js:122 ; src/elements/toast/toast.js:207 -->
- **Where it sits decides keyboard order.** The toast never takes focus, and its corner is only drawn: Tab reaches its close button and content where the toast sits in the page. Escape closes it only while the focus is inside it. Since BFB Elements Pro 1.1.2, closing it from inside (Escape, its close button) sends the focus back to where it came from, or lets it go when it came from nowhere. Place it straight after the button or form that shows it. <!-- src: src/elements/toast/toast.js:123 ; src/elements/toast/toast.js:240 ; src/elements/toast/toast.js:251 ; measured 2026-10-13 by dev/fixes-1.1.2-probe.mjs: Escape and Enter on the close button returned the focus to the link it came from -->
- **Nothing to close it with.** With `noClose` ticked and `closeAfter: 0`, the toast stays until a script hides it, and a toast with no focusable content gives Escape nowhere to start. <!-- src: plugins/bfb-elements-pro/elements/toast.php:302 ; src/elements/toast/toast.js:62 ; src/elements/toast/toast.js:197 -->
- **A click opener must be reachable and stay on the page.** The Click trigger listens for clicks alone and cancels nothing: a Bricks Button with no link renders a `span` a keyboard cannot reach (the fixture's `.toast-btn` does), and a link to another page leaves at once. Use a link to `#something` or **HTML tag** `tag: "button"`. <!-- src: src/elements/toast/toast.js:157 ; wp-content/themes/bricks/includes/elements/button.php:170 -->
- **"When a form fails" means the server said no.** Bricks sends `bricks/form/error` only after the server answers with an error (no action set, an action that failed). A required field left empty is stopped by the browser and shows nothing; a Click toast on the submit button would show even then. <!-- src: wp-content/themes/bricks/assets/js/bricks.min.js (bricks/form/success and bricks/form/error dispatched after the AJAX answer) ; src/elements/toast/toast.js:167 -->
- **A selector that finds no form shows nothing.** With `formSelector` set, the toast shows only when the sending form is found by its element id and matches; a typo stays silent. Empty, every form on the page shows it, including forms in the header or footer. <!-- src: src/elements/toast/toast.js:171 ; src/elements/toast/toast.js:176 -->
- **Show it again works only for After the page loads.** `again` and `key` are written for `trigger: "load"` alone. The flag is set the moment the toast shows, not when it is closed. Once per visit is sessionStorage, so a new tab shows it again; Only once is localStorage. `key` passes through WordPress' `sanitize_key` (lower case, letters, digits, `-` and `_`), so `Welcome Back` is stored as `welcomeback`; left empty, the element's id is used, and a copied element starts a new memory. Two toasts with one key share it. <!-- src: plugins/bfb-elements-pro/elements/toast.php:255 ; src/elements/toast/toast.js:47 ; src/elements/toast/toast.js:107 ; src/elements/toast/toast.js:151 -->
- **Bricks' layout settings on the card fight it.** Since BFB Elements Pro 1.1.2 a `_display` set on the toast no longer leaves the closed card in the way: closed, it is not drawn and takes no clicks whatever displays it, and open it shows with that display. `_position`, `_opacity` and `_transform` still fight its corner, fade and slide, and `_width` drops the window clamp and pulls a centred toast off centre: use `width`. <!-- src: src/elements/toast/toast.css:33 ; src/elements/toast/toast.css:36 ; measured 2026-10-13 by dev/fixes-1.1.2-probe.mjs with _display flex: closed visibility hidden, no click caught; open display flex -->
- **BFB Dark Mode leaves it a light card.** Since BFB Elements Pro 1.1.2 the toast is one of Dark Mode's light islands, as a block with `bfbe-keep` is: colours set through Bricks on it or inside it stay as set, and in the older page background and text style its headings and links keep the toast's ink. To have a dark toast in the dark, set its own `_background` and text colours; they are kept. <!-- src: plugins/bfb-elements-pro/includes/class-dark-mode-paint.php:480 ; plugins/bfb-elements-pro/elements/dark-mode.php:405 ; measured 2026-10-13 by dev/fixes-1.1.2-probe.mjs in a dark system scheme: text rgb(16, 24, 40) on rgb(255, 255, 255) -->
- **Inside a hidden or transformed box it goes with the box.** The card is `position: fixed`, so a parent hidden on a breakpoint, a closed Bricks popup or an off-canvas hides it, and a parent with a `transform` or `filter` makes it sit in that box instead of the window's corner. Put toasts at the page level. <!-- src: src/elements/toast/toast.css:8 -->
- **Over an open modal it is lifted into the dialog.** Since BFB Elements Pro 1.1.2, a toast shown while a modal dialog is open (BFB Modal's or any `showModal()`), such as one for a form inside the modal, is moved into that dialog and shown in the top layer above it, where it can be hovered and closed; Escape inside it closes the toast, not the dialog, and its words are said from inside the dialog. It goes back to its place when it closes or the dialog does, still shown in its corner if the dialog closed first. A toast already open when a modal opens stays under the backdrop. <!-- src: src/elements/toast/toast.js:100-121 ; src/elements/toast/toast.js:254 ; measured 2026-10-13 by dev/fixes-1.1.2-probe.mjs: drawn over the backdrop, its close button took the click, the modal stayed open -->
- **The time pauses, then resumes with what was left.** The pointer on it, the focus inside it, or a hidden browser tab stops the time and the bar; leaving resumes the rest, not the whole. Since BFB Elements Pro 1.1.1, a toast whose time ran out just as the pointer reached it closes when the pointer leaves instead of starting over. <!-- src: src/elements/toast/toast.js:59 ; src/elements/toast/toast.js:74 ; src/elements/toast/toast.js:185 ; src/elements/toast/toast.js:200 ; dev/toast-probe.mjs, "its time ran out under the pointer" -->
- **Right and left follow the page's direction.** The corners are written with logical properties, so on a right-to-left site Bottom right sits at the bottom left. **Distance from the edge** `offset` applies to the side and the top or bottom alike. <!-- src: src/elements/toast/toast.css:30 ; src/elements/toast/toast.css:32 -->
- **Reduced motion keeps the toast, drops the movement.** The slide is 0, the fade takes 0ms (the pack's base sets `--bfbe-duration: 0ms` on every BFB element) and the bar is not drawn, while the time still runs. <!-- src: src/elements/toast/toast.css:71 ; plugins/bfb-elements/includes/class-assets.php:106 -->
- **The canvas's In place view shows no behaviour.** With `builderView` unset the toast sits in the flow, fully drawn, with a static bar, and its trigger does nothing. `live` hides it until its trigger fires in the canvas, as on the site. <!-- src: plugins/bfb-elements-pro/elements/toast.php:278 ; src/elements/toast/toast.css:65 ; src/elements/toast/toast.js:90 -->
- **It says, it does not do.** A toast sends no email and stores nothing on the site; a form toast reports what the form's own actions did, and the form shows its own success message beside it. <!-- src: plugins/bfb-elements-pro/elements/toast.php:240 ; src/elements/toast/toast.js:167 -->

## Never do

- Do not leave `clickSelector` empty with `trigger: "click"`; the toast is left out of the page.
- Do not point `clickSelector`, `formSelector` or an interaction's `targetSelector` at a `#brxe-` id; use a class set in `_cssClasses`.
- Do not show a toast from a `span`, a Bricks Button with no link, or a link to another page; use `tag: "button"` or a link that stays on the page.
- Do not tick `noClose` on a toast with `closeAfter: 0`.
- Do not set Bricks' `_position`, `_opacity`, `_transform` or `_width` on the toast; use `corner`, `offset` and `width`.
- Do not put a toast inside a popup, an off-canvas, a box hidden on a breakpoint or a transformed box.
- Do not call `bfbeToast.show` from an interaction with **Target** left at Self, or without the `%brx%` argument.
- Do not put a message that must be answered or must stay in view in a toast; use BFB Modal.
