---
name: bfbe-content-switcher
description: "Use when placing, wiring or styling BFB Content Switcher (`bfbe-content-switcher`): two or more nested panels behind a pill toggle, the monthly and yearly pricing pattern. Read before writing its settings."
---

# BFB Content Switcher (`bfbe-content-switcher`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-content-switcher.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/content-switcher/

## What it is
Two or more nested panels behind a pill toggle, the monthly and yearly pricing pattern. The toggle follows the tabs pattern with one Tab stop and arrow keys between options, and each option can carry a badge. A choice can be written into the address as a hash and remembered in the visitor's browser.

**Not for:** Every panel is in the page, matched to its option by position, so all of their markup is delivered and one is visible. It suits a few short options such as monthly and yearly, not content that should load on demand.

**Costs a page:** CSS 1.00 KB, JS 1.39 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** yes · **In a query loop:** no · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Nestable: any Bricks element goes inside (blocks, headings, text, images, a form).
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-content-switcher",
    "settings": {},
    "children": [
        {
            "name": "block",
            "settings": {},
            "children": [
                {
                    "name": "heading",
                    "settings": {
                        "text": "Monthly",
                        "tag": "h3"
                    }
                }
            ]
        },
        {
            "name": "block",
            "settings": {},
            "children": [
                {
                    "name": "heading",
                    "settings": {
                        "text": "Yearly",
                        "tag": "h3"
                    }
                }
            ]
        }
    ]
}
```

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Options (`bfbeOptions`)
- `options` (repeater) **Options**. Add one row per option with a Label and a Badge, both taking dynamic data. Each row controls the nested block in the same position.
- `active` (number) **Selected at first**. Choose the option shown on load, 1 unless set. A number past the last option selects the last one.
- `hash` (checkbox) **Link with a hash**. Tick it to write a chosen option's label into the address, such as #yearly, so visiting that address selects it.
- `remember` (checkbox) **Remember the choice**. Tick it to keep the choice in the visitor's browser. With Link with a hash ticked, a hash in the address overrides it.
Styling, in the schema file: `align`.

### Toggle (`bfbeToggle`)
- `tabsOverflow` (select) **Overflow**: options: `wrap` Wrap (default), `scroll` Scroll sideways. Wrap, the default, puts options that do not fit on new lines. Scroll sideways keeps one row that scrolls.
Styling, in the schema file: `toggleBackground`, `toggleBorder`, `togglePadding`, `panelsGap`, `tabGap`.

### Option (`bfbeOption`)
Styling only, every key in the schema file: `tabTypography`, `tabPadding`, `tabRadius`, `tabBackgroundHover`, `activeBackground`, `activeColor`.

### Badge (`bfbeBadge`)
Styling only, every key in the schema file: `badgeTypography`, `badgeBackground`, `badgeColor`, `badgePadding`, `badgeBorder`, `badgeSelectedBackground`, `badgeSelectedColor`.

### Motion (`bfbeMotion`)
- `pillMotion` (select) **Pill**: options: `slide` Slides to the chosen option (default), `none` Switches at once. The pill Slides to the chosen option by default. Pick Switches at once for no movement.
- `panelEffect` (select) **Panel effect**: options: `none` None (default), `fade` Fade, `rise` Rise. None is the default. Fade or Rise animates the arriving panel while the one leaving disappears at once.
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS. Choose from the list or set a custom curve, Snappy by default. The pill and the panel share it.
Styling, in the schema file: `duration`, `easingCustom`.

### In the builder (`bfbeBuilder`)
- `builderView` (select) **Show it**: options: `open` Stacked, so you can style them (default), `closed` Closed, as the site leaves it, `live` Working, as on the site. Stacked, the default, lays every panel out for styling, Closed matches the site at rest, and Working lets the tabs switch panels in the canvas.

## What it guarantees for accessibility (do not undo)
- The toggle is a tablist; each option is a tab with aria-selected and aria-controls, and each panel is a tabpanel labeled by its tab.
- Arrow keys move between options and wrap round, Home and End jump to the ends, and the selected tab is the one Tab stop.
- Panels that are not selected carry the hidden attribute and display none, so assistive technology reads the chosen panel alone.
- Under reduced motion the sliding pill and the panel effect run with no duration, so the change is immediate.
<!-- bfbe:generated:end -->

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
