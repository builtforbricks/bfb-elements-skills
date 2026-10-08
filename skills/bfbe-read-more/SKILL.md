---
name: bfbe-read-more
description: "Use when placing, wiring or styling BFB Read More (`bfbe-read-more`): clamps any content you nest inside it to a number of lines or a height, with a real button that expands the rest. Read before writing its settings."
---

# BFB Read More (`bfbe-read-more`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-read-more.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/read-more/

## What it is
Clamps any content you nest inside it to a number of lines or a height, with a real button that expands the rest. The button carries aria-expanded and aria-controls, and the clamped content stays in the page rather than being removed. If the content already fits, the button hides itself, and tabbing into clamped content expands it.

**Not for:** Each Read More clamps one block with its own button, so panels where opening one closes another need a different structure. The clamped part is still in the page, so content that must stay out of the page until requested does not belong here.

**Costs a page:** CSS 0.65 KB, JS 0.96 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** yes · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Nestable: any Bricks element goes inside (blocks, headings, text, images, a form).
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-read-more",
    "settings": {},
    "children": [
        {
            "name": "text",
            "settings": {
                "text": "<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.</p>"
            }
        }
    ]
}
```

## Settings that decide the build
Also on this element, as on every element: Bricks' query loop (`hasLoop`, `query`); Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Clamp (`bfbeClamp`)
- `mode` (select) **Clamp by**: options: `lines` Lines (default), `height` Height. Lines is the default. Height clamps to a set height instead, which suits content that mixes images and text.
Styling, in the schema file: `lines`, `maxHeight`.

### Button (`bfbeButton`)
- `labelMore` (text) **Collapsed label**: placeholder Read more; dynamic data accepted. The words on the button while it is closed, Read more by default. It accepts dynamic data.
- `labelLess` (text) **Expanded label**: placeholder Show less; dynamic data accepted. The words once the content is open, Show less by default. It also accepts dynamic data.
- `icon` (icon) **Icon**. An optional icon that turns 180 degrees when the content opens.
- `iconPosition` (select) **Icon position**: options: `right` After the words (default), `left` Before the words; only when `icon` is set. After the words is the default, or pick Before the words.
Styling, in the schema file: `iconSize`, `buttonAlign`, `buttonGap`, `buttonTypography`, `buttonBackground`, `buttonBorder`, `buttonPadding`, `buttonHoverColor`, `buttonHoverBackground`.

### Fade (`bfbeFade`)
- `fade` (checkbox) **Fade the last lines**. Off by default. Tick it and the clamped edge fades out instead of cutting off hard.
Styling, in the schema file: `fadeSize`.

### Motion (`bfbeMotion`)
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS. How they speed up and slow down, Snappy by default. Pick Custom and type your own curve in Custom curve.
Styling, in the schema file: `duration`, `easingCustom`.

### In the builder (`bfbeBuilder`)
- `builderView` (select) **Show it**: options: `open` Open, so you can style it (default), `closed` Closed, as the site leaves it, `live` Working, as on the site. The content is shown open by default, so you can style it. Closed shows the clamped state, and Working lets the button expand the content in the builder.

## What it guarantees for accessibility (do not undo)
- The toggle is a real button with aria-expanded and aria-controls pointing at the content, so Enter and Space both work.
- Tabbing into clamped content, such as a link in the hidden lines, expands the element, so the focused link comes into view.
- Clamped content stays in the DOM, and a short block that already fits hides its button.
- Without script the content is not clamped, because the clamp applies after a one-line inline script marks the element ready.
- With reduced motion requested, the content opens and closes with no transition.
<!-- bfbe:generated:end -->

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
