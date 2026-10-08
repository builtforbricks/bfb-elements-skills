---
name: bfbe-notification-bar
description: "Use when placing, wiring or styling BFB Notification Bar (`bfbe-notification-bar`): a bar for promotions and notices that holds any elements you nest in it, placed at the top or bottom, in place, sticky or fixed. Read before writing its settings."
---

# BFB Notification Bar (`bfbe-notification-bar`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-notification-bar.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/notification-bar/

## What it is
A bar for promotions and notices that holds any elements you nest in it, placed at the top or bottom, in place, sticky or fixed. Closing the bar is remembered for a visit, a day, a week, a month or forever, and a new message key brings it back. Show from and Until are checked when the page is built, and a bar outside its dates is left out of the page.

**Not for:** Dates are read when the page is built, so a full-page cache keeps showing the bar until the cache clears. A message that must switch on at an exact minute for every visitor cannot rely on these dates.

**Costs a page:** CSS 0.99 KB, JS 0.95 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** yes · **In a query loop:** no · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Nestable: any Bricks element goes inside (blocks, headings, text, images, a form).
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-notification-bar",
    "settings": {},
    "children": [
        {
            "name": "text-basic",
            "settings": {
                "text": "Free shipping on orders over 50 until Sunday."
            }
        },
        {
            "name": "button",
            "settings": {
                "text": "Shop now",
                "size": "sm"
            }
        }
    ]
}
```

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Bar (`bfbeBar`)
- `position` (select) **Edge**: options: `top` Top (default), `bottom` Bottom. Top is the default, or pick Bottom.
- `behaviour` (select) **Stays**: options: `flow` In place, `sticky` Sticky (default), `fixed` Fixed over the page. Sticky is the default. Choose In place to let the bar scroll with the page, or Fixed over the page to keep it on screen over your content.
- `offBelow` (select) **Hide below**: options: `never` Never (default), `480` 480px, `640` 640px, `768` 768px, `992` 992px. Never by default. Choose 480, 640, 768 or 992px to drop the bar on narrow screens.
Styling, in the schema file: `align`.

### Closing (`bfbeDismiss`)
- `dismiss` (checkbox) **Close button**. Off by default. Tick it to add a real button named Close, at the end of the bar unless Side under Look moves it.
- `remember` (select) **Stay closed for**: options: `session` This visit, `1` A day, `7` A week (default), `30` A month, `forever` Forever; only when `dismiss` is set. A week by default. Choose This visit, A day, A month or Forever instead. The choice is stored in the visitor's browser.
- `key` (text) **Message key**: placeholder summer-sale; only when `dismiss` is set. The name the choice is stored under, such as summer-sale. Change it to show a closed bar again.
- `closeEffect` (select) **Closing effect**: options: `fade` Fade (default), `slide` Slide away, `collapse` Collapse, `none` None. Fade by default. Choose Slide away, Collapse or None instead.
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS. How it speeds up and slows down, Snappy by default. Pick Custom and type your own curve in Custom curve.
Styling, in the schema file: `duration`, `easingCustom`.

### Schedule (`bfbeSchedule`)
- `start` (text) **Show from**: placeholder 2026-12-01 09:00; dynamic data accepted. A date and time such as 2026-12-01 09:00, in the site's time zone. It accepts dynamic data.
- `end` (text) **Until**: placeholder 2026-12-24 18:00; dynamic data accepted. The end date and time, in the same format. Once it passes, the next page build leaves the bar out.

### Look (`bfbeLook`)
- `closeAt` (select) **Side**: options: `end` End (default), `start` Start; only when `dismiss` is set. The close button sits at the End of the bar by default, or at the Start.
- `closeY` (select) **Align**: options: `middle` Middle (default), `top` Top, `bottom` Bottom; only when `dismiss` is set. Middle by default, or Top or Bottom, for the close button's height in the bar. Space above or below it sets its distance from that edge, 8px by default.
- `closeOver` (checkbox) **Over the bar**: only when `dismiss` is set. Tick it and the close button floats over the bar, and the words center across its whole width.
Styling, in the schema file: `color`, `padding`, `gap`, `closeSize`, `closeColor`, `closeBackground`, `closeSpace`, `closeSpaceY`, `closeIcon`, `closeBackgroundHover`, `closeBorder`.

### In the builder (`bfbeBuilder`)
- `builderView` (select) **Show it**: options: `open` In the flow, so you can style it (default), `live` Working, as on the site. The bar is shown in the flow by default, so you can style it. Working makes the bar sit and close as it does on the site.

## What it guarantees for accessibility (do not undo)
- The close control is a real button named Close, so it answers Enter and Space.
- When the bar closes while focus is inside it, focus moves to the next focusable element after the bar.
- The bar is plain page content with no alert role or live region, so nothing is announced when it appears.
- With reduced motion requested, the closing effect runs with a duration of zero and the bar disappears at once.
<!-- bfbe:generated:end -->

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
