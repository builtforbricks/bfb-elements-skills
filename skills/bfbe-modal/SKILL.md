---
name: bfbe-modal
description: "Use when building a popup, dialog, lightbox, side drawer or bottom sheet with BFB Modal (`bfbe-modal`): opened by its own button, a click on any element, a hash link or a delay, with steps inside, a form that closes it or shows a thank-you view, and content built when opened. Read before writing its settings."
---

# BFB Modal (`bfbe-modal`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.3 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-modal.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/modal/

## What it is
A dialog for any Bricks content, rendered in the page inside the browser's own dialog element. It opens from its own button, a click on any element, a link with a hash or a delay. Position becomes a drawer or a bottom sheet per breakpoint, and a form sent inside it can close it, show another view or open another modal.

**Not for:** Not for stacked dialogs or exit-intent offers: opening a modal closes any other that is open, and there is no exit-intent trigger. With Once per visit ticked, the Delay trigger opens only once while the visitor browses in the same browser tab.

**Costs a page:** CSS 1.47 KB, JS 2.92 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** yes · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Nestable: any Bricks element goes inside (blocks, headings, text, images, a form).
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-modal",
    "settings": {},
    "children": [
        {
            "name": "heading",
            "settings": {
                "text": "Dialog title",
                "tag": "h3"
            }
        },
        {
            "name": "text-basic",
            "settings": {
                "text": "Anything can go in here."
            }
        }
    ]
}
```

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Trigger (`bfbeTrigger`)
- `trigger` (select) **Opens on**: options: `button` Its own button (default), `selector` A click on any element, `hash` A link with a hash, `delay` A delay. Its own button, the default, draws a button reading Open. A click on any element, A link with a hash and A delay are for triggers that live elsewhere on the page.
- `buttonLabel` (text) **Button label**: placeholder Open; dynamic data accepted; only when `trigger` is not `selector` or `hash` or `delay`. With Its own button, the words on the button, Open by default. It takes dynamic data.
- `buttonIcon` (icon) **Button icon**: only when `trigger` is not `selector` or `hash` or `delay`. With Its own button, an icon beside the words.
- `selector` (text) **CSS selector**: placeholder #brxe-abc123, .open-offer; only when `trigger` is `selector`. With A click on any element, type the selector that opens the modal, such as .open-offer. In a query loop, each item opens its own, the one nearest the click.
- `hash` (text) **Hash**: placeholder offer; only when `trigger` is `hash`. With A link with a hash, type the text after the # that opens it. In a query loop the item's id is added, so a link to #offer-{post_id} opens that item's modal.
- `delay` (number) **Delay (ms)**: only when `trigger` is `delay`. With A delay, set how long after load the modal opens, 3000 by default.
- `once` (checkbox) **Once per visit**: only when `trigger` is `delay`. With A delay, tick it to open the modal only once while the visitor browses in the same browser tab.

### Dialog (`bfbeDialog`)
- `size` (select) **Size**: options: `sm` Small, `md` Medium (default), `lg` Large, `full` Full screen. Small is 440px, Medium 640px (the default) and Large 900px, or pick Full screen. Width sets an exact width instead.
- `position` (select) **Position**: options: `center` Centre (default), `top` Top, `left` Left edge, `right` Right edge, `bottom` Bottom edge. Pick Centre (the default), Top, Left edge, Right edge or Bottom edge. The edges give a full-height drawer or a bottom sheet, and can differ per breakpoint so phones can have a sheet.
- `closeButton` (checkbox) **Close button**. Tick it to add a real close button. Escape closes the dialog either way, because the browser's own dialog handles it.
Styling, in the schema file: `width`, `gap`, `panelBackground`, `panelColor`, `panelPadding`, `panelBorder`, `panelShadow`.

### Motion (`bfbeMotion`)
- `animation` (select) **Effect**: options: `scale` Scale (default), `fade` Fade, `up` Slide up, `down` Slide down, `none` None. How the dialog comes and goes: Scale, Fade, Slide up, Slide down or None. Unset, it scales in, and a drawer or sheet slides in from its edge.
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS. Snappy by default. Pick another curve from the list, or Custom to type your own in Custom curve.
Styling, in the schema file: `duration`, `easingCustom`.

### Overlay (`bfbeOverlay`)
- `overlayClose` (checkbox) **Click outside to close**. Tick it to close the modal when a visitor clicks the dimmed area behind it.
- `back` (select) **Back button**: options: `close` Closes it (default), `page` Goes back a page. The default, Closes it, gives the open modal its own history entry, so a phone's back gesture closes it. Goes back a page leaves history alone, so back leaves the page as usual.
Styling, in the schema file: `overlayColor`, `overlayBlur`.

### Close button (`bfbeClose`)
The whole group shows only when `closeButton` is set.
- `closeShow` (select) **Shows**: options: `icon` An icon (default), `both` An icon and text, `text` Text. An icon is the default. Choose An icon and text or Text instead. This group shows once Close button is ticked in Dialog.
- `closeIcon` (icon) **Icon**: only when `closeShow` is not `text`. Choose any icon from the library. Unset, the button draws a thin cross, and Icon thickness sets its line, 2 by default.
- `closeText` (text) **Text**: placeholder Close; only when `closeShow` is `both` or `text`. With text showing, the word on the button, Close by default.
- `closeTextSide` (select) **Text side**: options: `after` After the icon (default), `before` Before the icon; only when `closeShow` is `both`. With An icon and text, put the text After the icon (the default) or Before the icon. Gap sets the space between them, 6px by default.
- `closePosition` (select) **Position**: options: `in-right` Inside, top right (default), `in-left` Inside, top left, `out-right` Outside, top right, `out-left` Outside, top left, `screen-right` Screen, top right, `screen-left` Screen, top left. Pick Inside, Outside or Screen, each at the top left or top right. Inside, top right is the default, and Horizontal offset and Vertical offset are 12px by default.
Styling, in the schema file: `closeGap`, `closeOffsetX`, `closeOffsetY`, `closeSize`, `closeTypography`, `closeColor`, `closeColorHover`, `closeBackground`, `closeBackgroundHover`, `closePadding`, `closeBorder`, `closeShadow`, `closeIconSize`, `closeIconColor`, `closeWeight`.

### Content (`bfbeViews`)
- `views` (checkbox) **Blocks inside are views**. Tick it to make the blocks inside take turns, one at a time, starting with the opening one. An element inside with the attribute data-bfbe-modal-show set to a view's number, next or prev switches to that view.
- `later` (checkbox) **Built when opened**. Tick it to hold back everything inside until the modal opens, which suits long query loops.
- `formDone` (select) **On sending**: options: `stay` Stays open (default), `close` Closes, `view` Shows a view, `modal` Opens another modal. When a Bricks form inside is sent, the modal Stays open by default. Choose Closes, Shows a view or Opens another modal instead.
- `formDoneView` (number) **View**: placeholder 2; only when `formDone` is `view` and `views` is set. With Shows a view, the number of the view to show, 2 by default. It needs Blocks inside are views ticked.
- `formDoneModal` (text) **Modal**: placeholder #brxe-abc123; only when `formDone` is `modal`. With Opens another modal, that modal's CSS selector, such as #brxe-abc123.
- `formDoneDelay` (number) **Delay (ms)**: placeholder 0; only when `formDone` is `close` or `view` or `modal`. How long to wait before the modal closes or moves on, 0 by default, so Bricks' own message can be read.

### Open button (`bfbeButton`)
The whole group shows only when `trigger` is not `selector` or `hash` or `delay`.
Styling only, every key in the schema file: `buttonTypography`, `buttonBackground`, `buttonBackgroundHover`, `buttonBorder`, `buttonPadding`.

### In the builder (`bfbeBuilder`)
- `builderView` (select) **Show it**: options: `open` Open, so you can style it (default), `closed` Closed, as the site leaves it, `live` Working, as on the site. Open, the default, lays the dialog out in the canvas so you can style it. Closed matches the site at rest, and Working lets a click open it in the canvas.

## What it guarantees for accessibility (do not undo)
- It opens with the browser's own showModal call on a real dialog element, so Escape closes it and the page behind it is held inert.
- The dialog takes its name from its opening heading, or the current view's heading, then from the open button's text, then from the word Dialog.
- The open button is a real button with aria-haspopup and aria-controls, and a close button that shows an icon alone is a real button named Close.
- Focus moves into the dialog on opening and returns to the control that opened it on closing, including when one modal hands over to another.
- The page behind cannot scroll while the modal is open.
- With Views on, the view you switch to takes focus on its heading, else its first control, else the view itself.
- Scale, fade and slide effects run on the shared motion duration, which reduced motion sets to zero, so the dialog appears and leaves without animation.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<div id="brxe-{id}" class="brxe-bfbe-modal bfbe-modal bfbe-modal--auto is-open" data-bfbe-trigger="button"
     data-bfbe-position="right" data-bfbe-position-at="478:bottom" data-bfbe-views="1"
     data-bfbe-form-done="view" data-bfbe-form-view="3" data-bfbe-label="Dialog">
  <button type="button" class="bfbe-modal__open bfbe-chip" data-bfbe-modal-open aria-haspopup="dialog"
          aria-controls="bfbe-{id}-dialog"><span>Open</span></button>
  <dialog id="bfbe-{id}-dialog" class="bfbe-modal__dialog bfbe-modal__dialog--md" data-bfbe-at="right"
          open data-bfbe-view="1" aria-labelledby="{heading id}">
    <!-- an Outside or Screen close button sits here, before the panel -->
    <div class="bfbe-modal__panel">
      <button type="button" class="bfbe-modal__close" data-bfbe-modal-close data-bfbe-close-at="in-right"
              data-bfbe-close-show="icon" aria-label="Close"><svg class="bfbe-modal__close-icon bfbe-modal__close-x">…</svg></button>
      <div class="bfbe-modal__content">… the children, or a <template class="bfbe-modal__later"> holding them …</div>
    </div>
  </dialog>
</div>
```

- Root `div.bfbe-modal`: `bfbe-modal--{animation}`, or `--auto` with **Effect** unset; `--canvas` in the builder's Open view and `data-bfbe-live="1"` in Working. The script reads `data-bfbe-trigger`, then `data-bfbe-selector`, `data-bfbe-hash` or `data-bfbe-delay` with `data-bfbe-once`; `data-bfbe-position` and `data-bfbe-position-at` (`width:value`, narrowest first); `data-bfbe-overlay-close`, `data-bfbe-back="page"`, `data-bfbe-views` and `data-bfbe-form-*`. All but the trigger and the base position are written only when their setting applies.
- The Open button renders with `trigger: "button"` alone; **Button icon** draws `.bfbe-modal__open-icon` before the words.
- The `<dialog>` is real on the site and in the canvas, opened with `showModal()`, so it sits in the top layer. `bfbe-modal__dialog--{sm|md|lg|full}` carries **Size**; `data-bfbe-at` is the position in force, rewritten by the script per breakpoint. Its id is `bfbe-{element id}-dialog`, with the loop's identifier added in a query loop (`bfbe-1505ce-0-dialog`).
- States: `[open]` on the dialog, `is-open` on the root and `bfbe-modal-lock` (overflow hidden) on `<html>` while open. With views, `data-bfbe-view="n"` on the dialog and `data-bfbe-view-off` on each hidden view.
- Close button: inside the panel for `in-*`, in the dialog before the panel for `out-*` and `screen-*`. Its word is `.bfbe-modal__close-text`; it carries `aria-label="Close"` only when no word shows.
- Where controls write: `width`, `gap`, `overlayColor`, `overlayBlur`, `closeSize`, `closeOffsetX`, `closeOffsetY`, `closeIconSize`, `duration` and `easing` set `--bfbe-modal-w`, `--bfbe-modal-gap`, `--bfbe-modal-overlay`, `--bfbe-modal-blur`, `--bfbe-modal-close`, `--bfbe-modal-close-x`, `--bfbe-modal-close-y`, `--bfbe-modal-close-icon`, `--bfbe-duration` and `--bfbe-ease` on the root. The `panel*` controls write to `.bfbe-modal__panel`, the `button*` controls to `.bfbe-modal__open`, and the overlay is the dialog's `::backdrop`. `.bfbe-modal__content` is a flex column spaced by `gap`.

## Wiring to other elements

- **By class, never by id.** Give the modal a class in `_cssClasses` (`modal-offer`) and point at `.modal-offer`. Inside a query loop Bricks moves `#brxe-{id}` into a class, and component instances share ids, so an id matches nothing in a loop and several modals in components.
- **`data-bfbe-modal-open`** with a selector, on any element anywhere (the page, a header, inside another modal), opens that modal. Add it through `_attributes`: `[{"name": "data-bfbe-modal-open", "value": ".modal-offer"}]`, plus `{"name": "data-bfbe-modal-show", "value": "2"}` to open at view 2. The selector may name the modal, anything inside it or a box holding it; of several matches, the one nearest the click opens, so a loop item opens its own.
- The click's default is cancelled when a modal is found, so a link to a real page still works on a page without that modal. Empty, the attribute does nothing; the Open button's own empty one is for itself.
- **`data-bfbe-modal-close`**, any value or none (`[{"name": "data-bfbe-modal-close"}]`), closes the modal it sits inside, at any depth. Outside every modal it does nothing.
- **`data-bfbe-modal-show`** on an element inside a modal with `views` switches to a number, `next` or `prev` (held at the first and last), with the click's default cancelled.
- **Selector trigger** (`trigger: "selector"`, `selector: ".open-offer"`): a click on a matching element or anything inside it opens the modal, and the click's default is cancelled, so a matched link does not navigate.
- **Hash trigger** (`trigger: "hash"`, `hash: "offer"`): a link to `#offer`, or a page loaded with it, opens the modal; closing removes the hash. In a loop the item's id is added, so link to `#offer-{post_id}`.
- **A form inside**: `formDone` acts on Bricks' `bricks/form/success` for a form inside this dialog, a Bricks **Form** or BFB Advanced Forms (`bfbe-form`); in a loop the item's form is matched by its loop id. `formDoneModal: ".modal-thanks"` hands over to another modal.
- **A modal only others open**: set `trigger: "hash"` (as the fixture's `.modal-thanks`) or `"selector"`, so no Open button renders. A handover closes the first, and focus later returns to the first one's opener.
- **Scripts**: the root dispatches `bfbe/modal/open`, `bfbe/modal/close`, `bfbe/modal/view` (`detail.view`) and `bfbe/modal/built`, all bubbling, and carries `bfbeModalOpen(view)`, `bfbeModalClose()` and `bfbeModalShow(which)`. It initialises again on Bricks' AJAX events (pagination, load page, query results, popup loaded), so modals in AJAX-loaded loops need nothing added.

## Verified patterns

**Steps, a form, then thanks** (fixture page `fixture-modal-flows`, `.modal-views`). `views` makes the three Blocks take turns; the Next button's `_attributes` and the link's `data-bfbe-modal-show="prev"` switch, and `formDone: "view"` with `formDoneView: 3` shows the thanks when the form sends. The Next button is a Bricks Button with `tag: "button"`, so a keyboard reaches it. The fixture's probe-only classes and placeholders are left out.

```json
{
  "name": "bfbe-modal",
  "settings": { "_cssClasses": "modal-views", "buttonLabel": "Open the steps", "closeButton": true, "views": true, "formDone": "view", "formDoneView": 3 },
  "children": [
    { "name": "block", "settings": {}, "children": [
      { "name": "heading", "settings": { "text": "Step one", "tag": "h2" } },
      { "name": "text-basic", "settings": { "text": "Read this first." } },
      { "name": "button", "settings": { "text": "Next", "tag": "button", "_attributes": [ { "name": "data-bfbe-modal-show", "value": "next" } ] } }
    ] },
    { "name": "block", "settings": {}, "children": [
      { "name": "heading", "settings": { "text": "Step two", "tag": "h2" } },
      { "name": "form", "settings": { "fields": [ { "id": "mfnam", "type": "text", "label": "Name", "required": true }, { "id": "mfeml", "type": "email", "label": "Email", "required": true } ], "showLabels": true, "submitButtonText": "Send", "actions": [ "email" ], "successMessage": "Sent." } },
      { "name": "text-basic", "settings": { "text": "<a href=\"#\" data-bfbe-modal-show=\"prev\">Back to step one</a>" } }
    ] },
    { "name": "block", "settings": {}, "children": [
      { "name": "heading", "settings": { "text": "Thanks", "tag": "h2" } },
      { "name": "text-basic", "settings": { "text": "We got it. <a href=\"#\" data-bfbe-modal-close>Done</a>" } }
    ] }
  ]
}
```

**Drawer on desktop, sheet on phones** (fixture page `fixture-modal-flows`, `.modal-drawer`). `position: "right"` with `position:mobile_portrait: "bottom"`, and **Width** per breakpoint so the sheet spans the phone. **Effect** is unset, so each slides in from its edge.

```json
{
  "name": "bfbe-modal",
  "settings": { "_cssClasses": "modal-drawer", "buttonLabel": "Open the drawer", "closeButton": true, "overlayClose": true, "position": "right", "position:mobile_portrait": "bottom", "width": "360px", "width:mobile_portrait": "100%" },
  "children": [
    { "name": "heading", "settings": { "text": "A drawer", "tag": "h2" } },
    { "name": "text-basic", "settings": { "text": "The full height at the right edge; a sheet at the bottom on a phone." } }
  ]
}
```

**A modal per loop item, built when opened** (fixture page `fixture-modal-loop`, `.modal-loop-later`). The Block's `hasLoop` repeats the item, and each modal gets its own dialog; with `later` its title, photo and form wait in a template until the first opening. `formDone: "close"` with `formDoneDelay: 300` closes it 300ms after the form sends. The fixture loops its own post type, `post` here. The image's id 22 is the demo site's and its `.local` addresses are replaced with https://example.com/...: use the target site's own attachment id and URLs.

```json
{
  "name": "block",
  "settings": { "hasLoop": true, "query": { "post_type": [ "post" ], "posts_per_page": 3, "orderby": "title", "order": "ASC" } },
  "children": [
    { "name": "bfbe-modal", "settings": { "_cssClasses": "modal-loop-later", "buttonLabel": "Details", "closeButton": true, "later": true, "formDone": "close", "formDoneDelay": 300 }, "children": [
      { "name": "heading", "settings": { "text": "{post_title}", "tag": "h2" } },
      { "name": "image", "settings": { "image": { "id": 22, "filename": "bfbe-before.png", "size": "medium", "url": "https://example.com/wp-content/uploads/2026/09/bfbe-before-300x188.png", "full": "https://example.com/wp-content/uploads/2026/09/bfbe-before.png" } } },
      { "name": "form", "settings": { "fields": [ { "id": "mfnam", "type": "text", "label": "Name", "required": true }, { "id": "mfeml", "type": "email", "label": "Email", "required": true } ], "showLabels": true, "submitButtonText": "Send", "actions": [ "email" ], "successMessage": "Sent." } }
    ] }
  ]
}
```

## Gotchas

- **Every direct child is a view.** With **Blocks inside are views** `views`, each direct child of the modal takes a turn, not Blocks alone: a Heading placed beside the Blocks becomes a view of its own. Each opening starts at view 1 unless the opener names another. <!-- src: src/elements/modal/modal.js:165 ; src/elements/modal/modal.js:238 ; src/elements/modal/modal.css:69 -->
- **A heading names the dialog.** The name is the shown view's heading, else the first heading inside, else the Open button's words; a Selector, Hash or Delay modal with no heading is announced as "Dialog". <!-- src: src/elements/modal/modal.js:171 ; plugins/bfb-elements-pro/elements/modal.php:829 -->
- **On sending needs its partner.** `formDone: "view"` does nothing unless `views` is ticked, and `formDone: "modal"` nothing without `formDoneModal`; the canvas shows a notice for each. **Delay (ms)** `formDoneDelay` is the wait after Bricks reports success, 0 unset, so give its success message time to be read. <!-- src: plugins/bfb-elements-pro/elements/modal.php:810 ; plugins/bfb-elements-pro/elements/modal.php:850 ; src/elements/modal/modal.js:347 -->
- **Openers elsewhere get nothing added.** The Selector trigger and `data-bfbe-modal-open` listen for clicks alone; no role, `tabindex` or `aria-*` is added, so the opener must be a link or a button. A Bricks Button with no link renders a `span`: set its **HTML tag** `tag: "button"`. <!-- src: src/elements/modal/modal.js:366 ; docs/elements/modal.md "Round 416" -->
- **Built when opened keeps the content out of the page.** With `later`, the children wait in a `<template>` until the first opening: no image is fetched, no form exists, search engines read nothing, and a link or script aimed at something inside finds nothing before then. The canvas always shows the content. <!-- src: plugins/bfb-elements-pro/elements/modal.php:915 ; src/elements/modal/modal.js:152 ; docs/elements/modal.md "Round 418" -->
- **A chosen Effect replaces the edge slide.** Unset, a drawer or sheet slides in from its edge; any chosen `animation`, `scale` included, plays wherever the dialog sits, so a drawer set to `fade` fades in place. <!-- src: plugins/bfb-elements-pro/elements/modal.php:751 ; src/elements/modal/modal.css:121 -->
- **A sheet is as wide as Width.** Drawers and sheets take **Width** (else Size) up to the screen's width, so a 360px drawer becomes a 360px sheet unless `width:mobile_portrait` is `100%`. Breakpoint positions are applied by the script with `max-width` queries; a centred or top dialog, Full screen aside, is never wider than the screen less 32px. <!-- src: src/elements/modal/modal.css:18 ; src/elements/modal/modal.css:45 ; src/elements/modal/modal.js:103 -->
- **Style the panel, not the element.** Bricks' universal `_background`, `_padding` and `_border` land on the root `div.bfbe-modal`, which on the page is the box around the Open button; the dialog's look is `panelBackground`, `panelColor`, `panelPadding`, `panelBorder` and `panelShadow`. The panel clips and its content scrolls within the screen's height less 32px, so a dropdown or tooltip that leaves it is cut. <!-- src: plugins/bfb-elements-pro/elements/modal.php:832 ; plugins/bfb-elements-pro/elements/modal.php:238 ; src/elements/modal/modal.css:54 ; src/elements/modal/modal.css:67 -->
- **Click outside to close also fires on a drag.** With `overlayClose`, a press inside a form field released on the dimmed area closes the modal, as when selecting text in a field. <!-- src: src/elements/modal/modal.js:290 ; measured 2026-10-08, headless Chrome on demo-bfb-modal -->
- **Touch needs a close control.** Without `closeButton`, `overlayClose` or an element carrying `data-bfbe-modal-close`, a touch visitor can close the modal with the back gesture alone, and not at all with `back: "page"`. <!-- src: plugins/bfb-elements-pro/elements/modal.php:876 ; src/elements/modal/modal.js:276 ; src/elements/modal/modal.js:296 -->
- **A Delay never waits its turn.** If another modal is open when the time comes, the delayed one is skipped for that page view. In a loop only the first item's opens, and **Once per visit** `once` is stored per element per tab. In Chrome, back still leaves the page after a Delay modal opens. <!-- src: src/elements/modal/modal.js:317 ; plugins/bfb-elements-pro/elements/modal.php:791 ; docs/elements/modal.md "Round 416" -->
- **The canvas shows a layout, not the behaviour.** **Show it** `builderView` unset (Open) lays the dialog in the flow, every view at once and drawers at their Width, with the script idle. Closed shows the Open button alone (nothing for Selector, Hash or Delay); `live` lets a click open it in the canvas. The setting changes nothing on the site. <!-- src: plugins/bfb-elements-pro/elements/modal.php:765 ; src/elements/modal/modal.css:146 ; src/elements/modal/modal.js:87 -->

## Never do

- Do not put loose elements beside the Blocks of a `views` modal; give each view one Block with its heading first.
- Do not point `selector`, `formDoneModal` or `data-bfbe-modal-open` at a `#brxe-` id; use a class set in `_cssClasses`.
- Do not set `formDone: "view"` without `views`, or `formDone: "modal"` without `formDoneModal`.
- Do not make an opener or a view switch from a `div`, a `span` or a Bricks Button with no link; use a link or `tag: "button"`.
- Do not set `animation` on a drawer or sheet that should slide from its edge.
- Do not leave a modal with no `closeButton`, no `overlayClose` and no `data-bfbe-modal-close` inside.
- Do not style the dialog with Bricks' universal `_background`, `_padding` or `_border`; use the `panel*` controls.
- Do not tick `later` for content that must be indexed, or found by a link or script, before the modal opens.
