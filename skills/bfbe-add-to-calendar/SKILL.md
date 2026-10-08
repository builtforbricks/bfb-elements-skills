---
name: bfbe-add-to-calendar
description: "Use when adding an add-to-calendar or save-the-date button for an event, or styling one, with BFB Add to Calendar (`bfbe-add-to-calendar`): one button that opens a menu, or a row of buttons, linking to Google, Outlook, Office 365, Yahoo and an Apple / ICS file. Read before writing its settings."
---

# BFB Add to Calendar (`bfbe-add-to-calendar`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-add-to-calendar.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/add-to-calendar/

## What it is
One button that opens a menu, or a row of buttons, linking to Google, Outlook, Office 365, Yahoo and an Apple / ICS file. Times are read in the site's time zone and sent as UTC. An all-day event goes out as calendar dates, with the exclusive end date calendars expect. Title, Starts, Ends, Location and Description all take dynamic data, so one element in a template serves a whole events post type.

**Not for:** It adds one event from a link or a downloaded file, and the file holds a single event with no repeat rule. A subscribable calendar feed, or a recurring series of events, needs a different approach.

**Costs a page:** CSS 0.81 KB, JS 0.66 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** no · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Bricks' query loop (`hasLoop`, `query`); Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Event (`bfbeEvent`)
- `title` (text) **Title**: placeholder {post_title}; dynamic data accepted. The event name. It takes dynamic data and falls back to the current post's title when empty.
- `start` (text) **Starts**: placeholder 2026-10-01 18:00; dynamic data accepted. Enter a date and time such as 2026-10-01 18:00. It is read in the site's time zone. Without one, the element draws nothing on the page.
- `end` (text) **Ends**: placeholder 2026-10-01 20:00; dynamic data accepted. Leave it empty for a one hour event, or a one day event when All day is ticked. An end before the start counts as empty.
- `allDay` (checkbox) **All day**. Tick it to send calendar dates instead of times. The end date is set to the day after the last day, as calendars expect.
- `location` (text) **Location**: dynamic data accepted. Where the event takes place, sent with the event to every calendar. It takes dynamic data.
- `description` (textarea) **Description**: dynamic data accepted. A few lines about the event, sent with it to every calendar. It takes dynamic data.

### Button (`bfbeButton`)
- `label` (text) **Label**: placeholder Add to calendar; dynamic data accepted. The words on the button, Add to calendar unless set. It takes dynamic data.
- `icon` (icon) **Icon**. A drawn calendar icon sits beside the label until you choose another. Icon size sets its size, 1em unless changed.
Styling, in the schema file: `iconSize`, `gap`, `caretSize`, `typography`, `background`, `hoverBackground`, `hoverColor`, `border`, `padding`.

### Calendars (`bfbeCalendars`)
- `layout` (select) **Show the calendars**: options: `menu` In a menu (default), `row` As a row of buttons. In a menu is the default, one button that opens a list. As a row of buttons shows each ticked calendar as its own button.
- `calIcons` (select) **Calendar icons**: options: `show` Show (default), `hide` Hide. Show, the default, draws a brand mark beside each calendar name. Hide removes them.
- `calGoogle` (checkbox) **Google**. Google, Outlook, Office 365 and Yahoo each have a checkbox and open that service's add-event page in a new tab. Tick at least one calendar, the ICS file included, or the element draws nothing on the page.
- `iconGoogle` (icon) **Google icon**: only when `calGoogle` is set and `calIcons` is not `hide`. With Calendar icons on Show, each ticked calendar has its own icon setting, such as Google icon, to put an icon of your own in place of the brand mark.
- `calOutlook` (checkbox) **Outlook**
- `iconOutlook` (icon) **Outlook icon**: only when `calOutlook` is set and `calIcons` is not `hide`
- `calOffice` (checkbox) **Office 365**
- `iconOffice` (icon) **Office 365 icon**: only when `calOffice` is set and `calIcons` is not `hide`
- `calYahoo` (checkbox) **Yahoo**
- `iconYahoo` (icon) **Yahoo icon**: only when `calYahoo` is set and `calIcons` is not `hide`
- `calIcs` (checkbox) **Apple / ICS file**. Downloads an .ics file for Apple Calendar and any app that reads the format. The file is built when the page is rendered.
- `iconIcs` (icon) **Apple / ICS file icon**: only when `calIcs` is set and `calIcons` is not `hide`
Styling, in the schema file: `markSize`, `markColor`.

### Menu (`bfbeMenu`)
Styling only, every key in the schema file: `menuBackground`, `menuBorder`, `menuShadow`, `menuWidth`, `menuPadding`, `itemPadding`, `itemBorder`, `itemGap`, `linkTypography`, `linkHoverBackground`.

### Motion (`bfbeMotion`)
- `menuEffect` (select) **Menu effect**: options: `fade` Fade (default), `rise` Rise, `none` None. How the menu opens. Fade is the default, Rise slides it up slightly, and None makes it appear at once.
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS. The curve the menu moves on, Snappy unless set.
Styling, in the schema file: `duration`, `easingCustom`.

## What it guarantees for accessibility (do not undo)
- In the menu layout the button is a native button with aria-expanded and aria-controls; opening it moves focus into the list of links.
- Escape closes the menu and returns focus to the button; a press outside the element, or focus moving out of it, also closes the menu.
- Each calendar is a real link; Tab moves through them in order, the menu binds no arrow keys, and icons are hidden from assistive technology.
- Under reduced motion the menu opens and closes with no transition, because the duration is set to zero.
<!-- bfbe:generated:end -->

## Rendered DOM

Root `div.bfbe-atc` with `bfbe-atc--menu` or `bfbe-atc--row` (from **Show the calendars**, `layout`) and `bfbe-atc--fx-fade`, `--fx-rise` or `--fx-none` (from **Menu effect**, `menuEffect`). No `data-bfbe-*` attributes: the script finds every `.bfbe-atc` itself. Links come in a fixed order: Google, Outlook, Office 365, Yahoo, ICS.

```html
<!-- layout "menu" (default) -->
<div class="bfbe-atc bfbe-atc--menu bfbe-atc--fx-fade">
  <button type="button" class="bfbe-atc__btn bfbe-atc__main bfbe-chip" aria-expanded="false" aria-controls="bfbe-...-menu">
    <svg class="bfbe-atc__icon">...</svg><span>Add to calendar</span><svg class="bfbe-atc__caret">...</svg>
  </button>
  <ul class="bfbe-atc__menu" id="bfbe-...-menu" role="list" hidden>
    <li><a class="bfbe-atc__link" href="https://calendar.google.com/..." target="_blank" rel="noopener"><i class="fab fa-google bfbe-atc__mark" aria-hidden="true"></i><span>Google</span></a></li>
    <li><a class="bfbe-atc__link" href="data:text/calendar;..." download="event-title.ics">...<span>Apple / ICS file</span></a></li>
  </ul>
</div>
<!-- layout "row": the label is a plain span, each calendar is a chip -->
<div class="bfbe-atc bfbe-atc--row bfbe-atc--fx-fade">
  <span class="bfbe-atc__lead"><svg class="bfbe-atc__icon">...</svg><span>Add to calendar</span></span>
  <ul class="bfbe-atc__menu bfbe-atc__menu--row" role="list">
    <li><a class="bfbe-atc__link bfbe-atc__btn bfbe-chip" href="..." target="_blank" rel="noopener">...</a></li>
  </ul>
</div>
```

- **Open state**: the script removes `hidden` from `.bfbe-atc__menu`, sets `aria-expanded="true"` on `.bfbe-atc__main` (the caret turns 180deg) and adds `.bfbe-atc__menu--end` when the menu would leave the window.
- **Where the styling lands**: the Button group's Look run (`typography`, `background`, `hoverBackground`, `hoverColor`, `border`, `padding`) writes to `.bfbe-atc__btn`, so the menu's button, or every calendar chip in a row. `iconSize` writes to `.bfbe-atc__icon`, `caretSize` to `.bfbe-atc__caret`.
- `menuBackground`, `menuBorder`, `menuShadow`, `menuWidth` (min-inline-size), `itemGap` and `menuPadding` write to `.bfbe-atc__menu`; `itemPadding`, `itemBorder` and `linkTypography` to `.bfbe-atc__link`; `linkHoverBackground` sets `--bfbe-atc-hover`, used on hover and keyboard focus.
- `markSize` and `markColor` write to `.bfbe-atc__mark`. `gap`, `duration` and `easing` set `--bfbe-atc-gap`, `--bfbe-duration` and `--bfbe-ease` on the root.

## Wiring to other elements

Stands alone; nothing targets it and it targets nothing.

Repeat it through a query loop or a single template rather than by copying: each rendered copy resolves its own dynamic data and gets its own menu id. Copies loaded by Bricks' AJAX pagination, load more, query filters and AJAX popups are initialised on Bricks' own events; for markup another script injects, call `window.bfbeAddToCalendar()`. Style or target it by a class in `_cssClasses`, never `_cssId`, because component instances share ids.

## Verified patterns

**A menu with three calendars**, from the demo page "ZZ demo: Add to Calendar" (`demo-bfb-add-to-calendar`). The default layout is the menu, so `layout` is not written. An empty `end` would mean one hour; here it is two.

```json
{
  "name": "bfbe-add-to-calendar",
  "settings": {
    "title": "Cupping class at Northwind",
    "start": "2026-10-03 10:00",
    "end": "2026-10-03 12:00",
    "location": "14 Bailey Street, Leeds LS1 4AB",
    "description": "Two hours, six coffees, one very loud spoon.",
    "calGoogle": true,
    "calOutlook": true,
    "calIcs": true,
    "markColor": { "hex": "#6e44ff" }
  }
}
```

**A save-the-date row for an all-day event**, from the fixture "PRO: Add to Calendar" (`fixture-add-to-calendar`). `allDay` with a date and no time, `layout: "row"` for one chip per calendar, and the label changed.

```json
{
  "name": "bfbe-add-to-calendar",
  "settings": {
    "title": "Open day",
    "start": "2026-11-15",
    "allDay": true,
    "layout": "row",
    "calGoogle": true,
    "calIcs": true,
    "label": "Save the date"
  }
}
```

**A menu with bordered, spaced items**, from the same fixture. All five calendars, and the Menu group's Items run: `itemPadding`, `itemBorder` (its corners are the border's radius) and `itemGap`, with smaller brand marks.

```json
{
  "name": "bfbe-add-to-calendar",
  "settings": {
    "title": "Launch party",
    "start": "2026-10-02 18:00",
    "end": "2026-10-02 22:00",
    "location": "The studio",
    "calGoogle": true,
    "calOutlook": true,
    "calOffice": true,
    "calYahoo": true,
    "calIcs": true,
    "markSize": "14px",
    "markColor": { "hex": "#e0a020" },
    "itemPadding": { "top": "12", "right": "16", "bottom": "12", "left": "16" },
    "itemBorder": {
      "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" },
      "style": "solid",
      "color": { "hex": "#e5e7eb" },
      "radius": { "top": "8", "right": "8", "bottom": "8", "left": "8" }
    },
    "itemGap": "6px"
  }
}
```

## Gotchas

- **A fresh insert draws nothing on the page.** No calendar is ticked by default, and without **Starts** (`start`) or a ticked calendar the page gets no markup at all; only the builder shows a notice. <!-- src: plugins/bfb-elements-pro/elements/add-to-calendar.php:578 and :635; plugins/bfb-elements/includes/abstract-element.php:538 -->
- **Dates are read by PHP's parser, and slashes mean month first.** `01/10/2026` becomes 10 January, while `13/10/2026` and a bare Unix timestamp render nothing. Write `2026-10-01 18:00`. <!-- src: add-to-calendar.php:520 (stamp()); measured 2026-10-08 with dev/wp.sh eval-file -->
- **A date tag needs a format.** A plain date tag follows the site's date format, which may use slashes; give it a format after a colon, as in `{post_date:Y-m-d H:i}`. <!-- src: add-to-calendar.php:570; measured 2026-10-08: {post_date} gave "October 6, 2026", {post_date:Y-m-d H:i} gave "2026-10-06 13:19" -->
- **Times are in the site's time zone unless they carry their own.** A plain time is read in the WordPress time zone and sent as UTC; a value ending in `Z` or an offset such as `+01:00` keeps that zone. <!-- src: add-to-calendar.php:520 and :599; measured 2026-10-08 with timezone_string Europe/Bucharest -->
- **A wrong end is not an error.** An empty **Ends** (`end`), or one before the start, becomes one hour after the start, or the same single day with **All day** (`allDay`). <!-- src: add-to-calendar.php:583 -->
- **An all-day end is the last day, inclusive.** The element adds the day calendars expect: start `2026-10-01` and end `2026-10-03` go out as `20261001/20261004`. <!-- src: add-to-calendar.php:601; measured 2026-10-08 -->
- **An empty title takes the current post's title.** On a static page that is the page's own name; inside a query loop it is the loop item's. <!-- src: add-to-calendar.php:569 -->
- **In a row, the Button styling moves onto the calendars.** With `layout: "row"` the icon and label sit in a plain `.bfbe-atc__lead` span that is not clickable, and `.bfbe-atc__btn` is on each calendar link, so the Look run styles the chips. The lead inherits the element's own typography, at weight 600. <!-- src: add-to-calendar.php:651-665; add-to-calendar.css:28 -->
- **The Menu group is for the menu layout.** Every Menu key except **Padding** (`menuPadding`) is hidden in a row and its selector excludes the row; **Caret size** (`caretSize`) too. `menuPadding` in a row pads the row's list. <!-- src: add-to-calendar.php:330, :379; docs/elements/add-to-calendar.md "round 350" and "round 351" -->
- **Gap is not the space between icon and label.** **Gap** (`gap`) spaces the lead and the chips of a row; the icon-to-label space is the chip's fixed `.45em`. In the menu layout the menu is positioned absolutely, so Gap has nothing to space. <!-- src: src/elements/add-to-calendar/add-to-calendar.css:2, :14, :33; plugins/bfb-elements/includes/class-assets.php:87 -->
- **A clipping ancestor cuts the menu.** The menu is `position: absolute` under the button at `z-index: 30`, so a parent with `overflow: hidden` clips it. It flips to the button's end edge only when it would leave the window. <!-- src: add-to-calendar.css:14-16; add-to-calendar.js:20-23 -->
- **The ICS file is fixed when the page renders.** It is a `data:` link built on render, and its UID comes from the title and the start, so two events sharing both are one event to a calendar app. HTML in any field is stripped; line breaks in the description survive. <!-- src: add-to-calendar.php:567-574, :624-632 -->

## Never do

- Do not insert it without `start` and at least one of `calGoogle`, `calOutlook`, `calOffice`, `calYahoo`, `calIcs`.
- Do not write `start` or `end` as `dd/mm/yyyy` or a Unix timestamp, and do not use a date tag without a `Y-m-d H:i` format.
- Do not add a day to `end` for an all-day event; give the last day and let the element make it exclusive.
- Do not style a row's chips with the Menu keys (`linkTypography`, `itemPadding`, `itemBorder`); use the Button group's Look keys.
- Do not set `caretSize` or any Menu key other than `menuPadding` with `layout: "row"`: the panel hides them and they are dropped.
- Do not use `gap` to space the icon from the label.
- Do not place the menu layout inside an ancestor with `overflow: hidden`.
- Do not toggle the menu's `hidden` or `aria-expanded` with a Bricks interaction; the script owns both.
