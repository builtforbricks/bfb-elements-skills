---
name: bfbe-notification-bar
description: "Use when building an announcement bar, promo banner or site notice with BFB Notification Bar (`bfbe-notification-bar`): a nestable bar at the top or bottom, in place, sticky or fixed, with a close button that is remembered and optional start and end dates. Read before writing its settings."
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

## Rendered DOM

The root is a `<div>` laid out as a flex row. The nested elements sit in `.bfbe-nbar__inner`; the close button follows it as the root's last child.

```html
<div class="brxe-bfbe-notification-bar bfbe-nbar bfbe-nbar--filled bfbe-nbar--top bfbe-nbar--sticky bfbe-nbar--close-fade"
     data-bfbe-close-at="end" data-bfbe-close-y="top" data-bfbe-key="bfbe-nbar-summer-sale" data-bfbe-remember="7">
  <script>/* hides a closed bar before first paint */</script>
  <div class="bfbe-nbar__inner"><!-- the nested elements --></div>
  <button type="button" class="bfbe-nbar__close" data-bfbe-nbar-close aria-label="Close"><svg aria-hidden="true">...</svg></button>
</div>
```

- Root modifiers: `bfbe-nbar--top|bottom` (`position`), `--flow|sticky|fixed` (`behaviour`), `--close-fade|slide|collapse|none` (`closeEffect`), `--off-480|640|768|992` (`offBelow`, absent for `never`).
- Also on the root: `--close-over` (`closeOver` with `dismiss`), `--filled` (a Bricks Background colour on the element itself), `--canvas` (the builder in the default view).
- `data-bfbe-close-at` is always written; `data-bfbe-close-y` only for `top` or `bottom`. `data-bfbe-key` is `bfbe-nbar-` plus the sanitised `key`, or the element's id when `key` is empty.
- The inline `<script>` and the `<button>` are rendered only with `dismiss`; the script is left out in the canvas. `data-bfbe-live="1"` marks the Working view there.
- Closing adds `is-closing` to the root for the effect (Collapse first adds `is-measured` and an inline `--bfbe-nbar-h`), then the `hidden` attribute.
- The memory sits under the `data-bfbe-key` name: `"1"` for Forever (`localStorage`) and This visit (`sessionStorage`), otherwise an expiry time in milliseconds in `localStorage`.
- **Text colour** (`color`) sets `--bfbe-nbar-fg` on the root, which the root's children read. **Padding** (`padding`), **Gap between items** (`gap`) and **Align content** (`align`) land on `.bfbe-nbar__inner` (10px 24px, 16px, centred by default).
- The close controls set `--bfbe-nbar-close*` properties on the root that `.bfbe-nbar__close` reads; **Border** (`closeBorder`) writes the button's border itself. `duration` and `easing` set `--bfbe-duration` and `--bfbe-ease`.
- Bricks' own Background, Border and Box Shadow land on the root.

## Wiring to other elements

Nothing in the pack targets the bar and it targets nothing. What it does expose:

- The script binds the first `[data-bfbe-nbar-close]` inside the root, the button that **Close button** (`dismiss`) renders. A Bricks button nested in the bar is content; it does not close the bar.
- Once the bar is hidden, its root dispatches the bubbling event `bfbe/bar/close`, for a page script to follow.
- Bars inserted by Bricks' AJAX pagination, load-page, query results or popups are set up again on Bricks' own events. For markup a custom script inserts, call `window.bfbeNotificationBar()`.
- Dark Mode Toggle (skill `bfbe-dark-mode`): with a colour in the bar's own `_background`, its default words stay white under the toggle's dark state.
- Two bars with the same **Message key** (`key`) share one memory: closing either hides both from the next page load.
- To reach a bar from CSS or a script, give it a class in `_cssClasses`, never `_cssId`: component instances share ids.

## Verified patterns

**Promotion bar in the page, filled and closable.** From the demo page "ZZ demo: Notification Bar" (Northwind). In place (`behaviour: "flow"`), closed for a week under its own `key`, white words through `color`. The fill is Bricks' `_background` as a colour object, kept from the page because the bar needs it. `closeSpace` evens the button's gap on a taller bar.

```json
{
    "name": "bfbe-notification-bar",
    "settings": {
        "behaviour": "flow",
        "dismiss": true,
        "remember": "7",
        "key": "northwind-delivery",
        "color": { "hex": "#ffffff" },
        "padding": { "top": "14", "right": "20", "bottom": "14", "left": "20" },
        "closeSpace": "26px",
        "_background": { "color": { "hex": "#6e44ff" } }
    },
    "children": [
        { "name": "text-basic", "settings": { "text": "Free delivery on orders over £30, until the Rwanda runs out.", "tag": "p" } },
        { "name": "button", "settings": { "text": "Shop the beans", "link": { "type": "external", "url": "#shop" }, "size": "sm" } }
    ]
}
```

**Sticky top bar with a remembered close.** From the fixture "FREE: Notification Bar". The builder's inserted children plus `dismiss` and a `key`; **Edge** and **Stays** keep their defaults, Top and Sticky. Place it at the root of the page content so it sticks for the whole page.

```json
{
    "name": "bfbe-notification-bar",
    "settings": { "dismiss": true, "remember": "7", "key": "summer-sale" },
    "children": [
        { "name": "text-basic", "settings": { "text": "Free shipping on orders over 50 until Sunday." } },
        { "name": "button", "settings": { "text": "Shop now", "size": "sm" } }
    ]
}
```

**Long notice with the close button at the top.** From the same fixture. A message that wraps in a padded bar. **Align** (`closeY: "top"`) lifts the button. **Space above or below it** (`closeSpaceY`, offered only with Top or Bottom) and **Space beside it** (`closeSpace`) set it 12px from both edges.

```json
{
    "name": "bfbe-notification-bar",
    "settings": {
        "behaviour": "flow",
        "dismiss": true,
        "key": "close-top",
        "closeY": "top",
        "closeSpaceY": "12px",
        "closeSpace": "12px",
        "padding": { "top": "24", "right": "24", "bottom": "24", "left": "24" }
    },
    "children": [
        { "name": "text-basic", "settings": { "text": "Our winter opening hours start on Monday: seven till four on weekdays, eight till two at weekends." } },
        { "name": "button", "settings": { "text": "See the hours", "size": "sm" } }
    ]
}
```

## Gotchas

- **The fill is Bricks' Background, as a colour object.** Without one the bar is filled with its inherited text colour and the words take `Canvas`. Write `_background: {"color": {"hex": "#..."}}`; a bare `{"hex"}` generates no CSS at all. <!-- src: src/elements/notification-bar/notification-bar.css:15; docs/SESSION-HANDOFF.md "Round 159" (Traps 1); bare hex measured through Bricks' CSS generator 2026-10-08 -->
- **Words take Text colour, not Typography on the root.** `color` writes `--bfbe-nbar-fg`, which the nested elements read. Bricks' Typography colour on the root repaints the fill when no Background is set, and never reaches the words. <!-- src: plugins/bfb-elements/elements/notification-bar.php:161-171; src/elements/notification-bar/notification-bar.css:17-19 -->
- **A Display on the root keeps a closed bar on screen.** Bricks writes `_display` as `#brxe-<id> { display: ... }`, which outranks `.bfbe-nbar[hidden]` and the **Hide below** rules. The root is already a flex row. <!-- src: src/elements/notification-bar/notification-bar.css:64,76-79; docs/SESSION-HANDOFF.md "Round 159" (the same trap on the Content Switcher); measured through Bricks' CSS generator 2026-10-08 -->
- **The closing controls need the Close button.** **Closing effect** (`closeEffect`), **Duration (ms)** (`duration`) and **Easing** (`easing`) show without `dismiss`. Only the close button closes the bar, so alone they do nothing. <!-- src: plugins/bfb-elements/elements/notification-bar.php:331-346; src/elements/notification-bar/notification-bar.js:27-28 -->
- **Without a key, each component instance remembers alone.** An empty `key` falls back to the element's id, which Bricks extends per component instance. A bar used as a component on several pages then closes page by page. Set one `key` in lowercase letters, digits, `-` and `_`. <!-- src: plugins/bfb-elements/elements/notification-bar.php:407-408; plugins/bfb-elements/includes/abstract-element.php:431 -->
- **A new key brings the bar back; a new duration does not.** **Stay closed for** (`remember`) is stored when the visitor closes the bar. A Forever close stays closed after you shorten it; change `key` to show the bar again. <!-- src: src/elements/notification-bar/notification-bar.js:36-46 -->
- **This visit lasts one tab.** `remember: "session"` writes `sessionStorage`, so a new tab opened on the site shows the bar again. <!-- src: src/elements/notification-bar/notification-bar.js:44 -->
- **Dates must be ones PHP's `strtotime()` reads.** `2026-12-01 09:00` works; `25/12/2026` is not understood, so the bar always shows (the canvas says so), and `05/12/2026` reads as 12 May. A dynamic tag in **Show from** (`start`) or **Until** (`end`) must output the same kind of date. <!-- src: plugins/bfb-elements/elements/notification-bar.php:398-405,454-456; strtotime() measured on the dev site 2026-10-08 -->
- **The canvas ignores dates and stays put.** In the builder a bar outside its dates still renders. With the default **Show it** (`builderView: "open"`) it is never sticky or fixed and its close button does nothing. <!-- src: plugins/bfb-elements/elements/notification-bar.php:403,434-436; src/elements/notification-bar/notification-bar.css:83; src/elements/notification-bar/notification-bar.js:25 -->
- **Working view writes the real memory.** With `builderView: "live"`, closing the bar in the canvas stores the dismissal in that browser for the site. A bar closed earlier is hidden in the canvas too. <!-- src: src/elements/notification-bar/notification-bar.js:25,36-47 -->
- **Sticky holds only within its parent.** `behaviour: "sticky"` sticks while the bar's parent is on screen; inside a section, or a header template that does not stick itself, it scrolls away with that parent. Place it at the root of the page content, or use `fixed`. <!-- src: src/elements/notification-bar/notification-bar.css:24-26 -->
- **The dark state needs the fill on the element.** Only a colour in the bar's own `_background` adds `bfbe-nbar--filled`. That class keeps the words white under the Dark Mode Toggle's dark state; a fill from a global class leaves them on `Canvas`. <!-- src: docs/elements/notification-bar.md "Round 394"; plugins/bfb-elements/elements/notification-bar.php:411-414 -->

## Never do

- Do not pass a bare `{"hex": ...}` to `_background`; write `{"color": {"hex": ...}}`.
- Do not colour the words with Typography on the bar's root; set `color`.
- Do not set `_display` on the bar.
- Do not set `closeEffect`, `duration` or `easing` on a bar without `dismiss`.
- Do not leave `key` empty on a bar used as a component on several pages.
- Do not write `start` or `end` as `d/m/Y`; use `Y-m-d H:i`.
- Do not nest a `sticky` bar in a section when it must stay on screen; place it at the root of the page content or use `fixed`.
- Do not add `role="alert"` or `aria-live` to the bar; it is plain page content by design.
