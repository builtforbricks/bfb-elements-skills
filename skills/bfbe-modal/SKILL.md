---
name: bfbe-modal
description: "Use when placing, wiring or styling BFB Modal (`bfbe-modal`): a dialog for any Bricks content, rendered in the page inside the browser's own dialog element. Read before writing its settings."
---

# BFB Modal (`bfbe-modal`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
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
- `closePosition` (select) **Position**: options: `in-right` Inside, top right (default), `in-left` Inside, top left, `out-right` Outside, top right, `out-left` Outside, top left, `screen-right` Screen, top right, `screen-left` Screen, top left. Pick Centre (the default), Top, Left edge, Right edge or Bottom edge. The edges give a full-height drawer or a bottom sheet, and can differ per breakpoint so phones can have a sheet.
Styling, in the schema file: `closeGap`, `closeOffsetX`, `closeOffsetY`, `closeSize`, `closeTypography`, `closeColor`, `closeColorHover`, `closeBackground`, `closeBackgroundHover`, `closePadding`, `closeBorder`, `closeShadow`, `closeIconSize`, `closeIconColor`, `closeWeight`.

### Content (`bfbeViews`)
- `views` (checkbox) **Blocks inside are views**. Tick it to make the blocks inside take turns, one at a time, starting with the opening one. An element inside with the attribute data-bfbe-modal-show set to a view's number, next or prev switches to that view.
- `later` (checkbox) **Built when opened**. Tick it to hold back everything inside until the modal opens, which suits long query loops.
- `formDone` (select) **On sending**: options: `stay` Stays open (default), `close` Closes, `view` Shows a view, `modal` Opens another modal. When a Bricks form inside is sent, the modal Stays open by default. Choose Closes, Shows a view or Opens another modal instead.
- `formDoneView` (number) **View**: placeholder 2; only when `formDone` is `view` and `views` is set. With Shows a view, the number of the view to show, 2 by default. It needs Blocks inside are views ticked.
- `formDoneModal` (text) **Modal**: placeholder #brxe-abc123; only when `formDone` is `modal`. With Opens another modal, that modal's CSS selector, such as #brxe-abc123.
- `formDoneDelay` (number) **Delay (ms)**: placeholder 0; only when `formDone` is `close` or `view` or `modal`. With A delay, set how long after load the modal opens, 3000 by default.

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

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
