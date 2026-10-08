---
name: bfbe-hotspots
description: "Use when placing, wiring or styling BFB Image Hotspots (`bfbe-hotspots`): an image with pins, each a real button that opens its own nested block as a tooltip or as a card grown from the pin. Read before writing its settings."
---

# BFB Image Hotspots (`bfbe-hotspots`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-hotspots.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/hotspots/

## What it is
An image with pins, each a real button that opens its own nested block as a tooltip or as a card grown from the pin. Each pin's expanded state is written into the HTML, opening a panel moves focus into it, and Escape returns focus to the pin. Color, size and icon can be set per pin in the same list, and a link can lie over a whole panel.

**Not for:** Pins sit at fixed percentages of one picture, and each opens a block you place yourself. It does not zoom or pan, and it cannot build pins from a query loop.

**Costs a page:** CSS 1.78 KB, JS 2.40 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** yes · **In a query loop:** no · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Nestable: any Bricks element goes inside (blocks, headings, text, images, a form).
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-hotspots",
    "settings": {},
    "children": [
        {
            "name": "block",
            "settings": {}
        },
        {
            "name": "block",
            "settings": {}
        }
    ]
}
```

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Image (`bfbeImage`)
- `image` (image) **Image**. Choose the picture the pins sit on. With none chosen, the page draws nothing, while the builder shows a stand-in.
Styling, in the schema file: `imageBorder`.

### Pins (`bfbePins`)
- `pins` (repeater) **Pins**. One row per pin with its Name, Left (%) and Top (%), Text on the pin, Icon, Link on the whole panel, Colour and Size. Pin 2 opens the second block inside the element, and so on.
- `openOn` (select) **Opens on**: options: `click` Click (default), `hover` Hover and click. Click is the default. Hover and click also opens a panel when the pointer enters a pin.
- `pinIcon` (icon) **On every pin**. Choose an icon for every pin. A pin with its own Icon keeps it.
- `pulse` (checkbox) **Pulse**. Tick it to make a ring pulse from each pin at the Pulse speed, 2 seconds unless set.
Styling, in the schema file: `size`, `pinBackground`, `pinText`, `pinTypography`, `pinBorder`, `pinPadding`, `pinShadow`, `iconSize`, `iconColor`, `pulseColor`, `pinHoverBackground`.

### Panels (`bfbePanel`)
- `panelStyle` (select) **Panel**: options: `tooltip` Beside the pin (default), `expand` Grown from the pin. Beside the pin, a tooltip, is the default. Grown from the pin makes the dot itself grow into the card. Style each panel on its block's own Style tab.
- `expandFrom` (select) **Grows towards**: options: `auto` Where there is room (default), `tl` Right and down, `tr` Left and down, `bl` Right and up, `br` Left and up; only when `panelStyle` is `expand`. Where there is room is the default. Pick Right and down, Left and down, Right and up or Left and up so the card extends from the pin's position.
- `placement` (select) **Panel side**: options: `auto` Wherever there is room (default), `top` Top, `bottom` Bottom, `left` Left, `right` Right; only when `panelStyle` is not `expand`. Wherever there is room is the default. Pick Top, Bottom, Left or Right to choose a side. The tooltip flips to the other side when it would not fit.
Styling, in the schema file: `panelMinWidth`, `panelBlur`.

### Motion (`bfbeMotion`)
- `panelEffect` (select) **Panel effect**: options: `fade` Fade (default), `rise` Rise, `scale` Scale, `none` None. Choose how a panel appears: Fade (the default), Rise, Scale or None.
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS. Snappy by default. Pick another curve from the list, or Custom to type your own in Custom curve.
Styling, in the schema file: `duration`, `easingCustom`, `pulseSpeed`, `pulseScale`.

### In the builder (`bfbeBuilder`)
- `builderView` (select) **Show it**: options: `open` Open, so you can style them (default), `closed` Closed, as the site leaves it, `live` Working, as on the site. Open, the default, lays the panels out for styling, Closed matches the site at rest, and Working lets a click open a panel in the canvas.

## What it guarantees for accessibility (do not undo)
- Each pin is a native button whose aria-expanded is in the server-rendered HTML, with aria-controls naming its own panel.
- Enter or Space opens a panel and moves focus into it; Escape closes it and returns focus to the pin.
- A pin's name is its visible text plus a hidden Name, which reads Pin and its number when empty.
- With Hover and click, a panel also opens as the pointer enters a pin; keyboard focus on a pin does not open it.
- A pin's link is a real anchor laid over the panel and labeled with the pin's name.
- Under reduced motion the pulse is switched off and panels beside the pin open without a transition.
<!-- bfbe:generated:end -->

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
