---
name: bfbe-popover
description: "Use when placing, wiring or styling BFB Popover (`bfbe-popover`): one element with two modes: Tooltip shows short plain text on hover and keyboard focus, and Popover holds nested Bricks content behind a button. Read before writing its settings."
---

# BFB Popover (`bfbe-popover`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-popover.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/popover/

## What it is
One element with two modes: Tooltip shows short plain text on hover and keyboard focus, and Popover holds nested Bricks content behind a button. The panel is placed on the side with room, shifted to stay on screen, and can carry an arrow that follows the trigger. It uses the browser's Popover API where there is one, with a fallback that handles dismissal itself.

**Not for:** Not for content that must be reachable without a click or a hover, or for a full-screen dialog: use Modal for that. Tooltip mode holds short plain text, so links and buttons belong in Popover mode.

**Costs a page:** CSS 0.94 KB, JS 1.91 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** yes · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Nestable: any Bricks element goes inside (blocks, headings, text, images, a form).
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-popover",
    "settings": {},
    "children": [
        {
            "name": "text-basic",
            "settings": {
                "text": "Popover content. Put anything here."
            }
        }
    ]
}
```

## Settings that decide the build
Also on this element, as on every element: Bricks' query loop (`hasLoop`, `query`); Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Mode (`bfbeMode`)
- `mode` (select) **Mode**: options: `popover` Popover (nested content) (default), `tooltip` Tooltip (short text). Popover (nested content) is the default. Tooltip (short text) holds plain text and drops anything nested inside the element.
- `text` (textarea) **Tooltip text**: placeholder Tooltip text; dynamic data accepted; only when `mode` is `tooltip`. Type the words a tooltip shows. They accept dynamic data, and line breaks are kept. Links or buttons belong in Popover mode instead.
- `openOn` (select) **Opens on**: options: `click` Click (default), `hover` Hover and click; only when `mode` is not `tooltip`. Click is the default. Choose Hover and click to open on hover too. A tooltip always opens on hover and on keyboard focus.
- `delay` (number) **Hover delay (ms)**. Set how long the pointer rests before a tooltip or a hover popover opens, 100 by default. Raise it if the panel flickers as the mouse crosses the page.

### Trigger (`bfbeTrigger`)
- `label` (text) **Text**: placeholder More; dynamic data accepted. Type the label on the trigger button, More by default. It accepts dynamic data, so each query loop item can name its own popover.
- `icon` (icon) **Icon**. Choose an icon from the library to sit beside the label. Icon size, 1em, and Icon gap, .45em by default, come with it.
- `triggerStyle` (select) **Looks like**: options: `chip` Button (default), `link` Link, `plain` Plain text. Button is the default. Choose Link or Plain text instead. The trigger stays a real button in all three, so just the style changes.
Styling, in the schema file: `iconSize`, `triggerGap`, `triggerTypography`, `triggerBackground`, `triggerBackgroundHover`, `triggerBorder`, `triggerPadding`.

### Placement (`bfbePlace`)
- `placement` (select) **Side**: options: `auto` Wherever there is room (default), `top` Top, `bottom` Bottom, `left` Left, `right` Right. Wherever there is room, the default, tries bottom, top, right and left in turn. A fixed side flips to the opposite one when it does not fit and that side has more room.
- `offset` (number) **Distance (px)**. Set the gap between the trigger and the panel, 8 by default. The panel is kept inside the viewport whichever side it takes.
Styling, in the schema file: `inset`.

### Panel (`bfbePanel`)
- `arrow` (checkbox) **Arrow**. Tick it to draw an arrow that points at the trigger, sized by Arrow size, 10px by default.
Styling, in the schema file: `maxWidth`, `panelBackground`, `panelColor`, `panelTypography`, `panelPadding`, `panelGap`, `panelBorder`, `lineColor`, `panelShadow`, `arrowSize`.

### Motion (`bfbeMotion`)
- `effect` (select) **Effect**: options: `fade` Fade (default), `rise` Rise, `scale` Scale, `none` None. Choose how the panel arrives and leaves: Fade (the default), Rise, Scale or None.
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS. Snappy by default. Pick another curve from the list of ten, or Custom to type your own in Custom curve.
Styling, in the schema file: `duration`, `easingCustom`.

### In the builder (`bfbeBuilder`)
- `builderView` (select) **Show it**: options: `open` Open, so you can style it (default), `closed` Closed, as the site leaves it, `live` Working, as on the site. Open, the default, shows the panel so you can style it. Closed matches the site at rest, and Working lets a click open it in the canvas.

## What it guarantees for accessibility (do not undo)
- Tooltip mode ties the plain-text panel to a focusable trigger with aria-describedby and role tooltip.
- A tooltip shows on hover and focus, and it hides again on blur or Escape.
- Popover mode puts aria-expanded and aria-controls on a real button, and opening it by click or key moves focus into the panel. Tab then wraps within the panel's controls, and in a panel with no controls Tab closes it.
- Escape closes a popover and returns focus to the trigger, and a click outside closes it through the browser's light dismiss or the fallback.
- The popover panel is named by its trigger through aria-labelledby.
- Fade, rise and scale run on the shared motion duration, which reduced motion sets to zero, so the panel appears without animation.
<!-- bfbe:generated:end -->

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
