---
name: bfbe-add-to-calendar
description: "Use when adding an add-to-calendar or save-the-date button for an event, or styling one, with BFB Add to Calendar (`bfbe-add-to-calendar`): one button that opens a menu, or a row of buttons, linking to Google, Outlook, Office 365, Yahoo and an Apple / ICS file. Read before writing its settings."
---

# BFB Add to Calendar (`bfbe-add-to-calendar`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
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
Also on this element, as on every element: Bricks' query loop (`hasLoop`, `query`); Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Event (`bfbeEvent`)
- `source` (select) **Date from**: options: `event` The fields below (default), `shop_delivery` The order: expected delivery date, `shop_release` The product: release date. The fields below is the default. With WooCommerce, pick The order: expected delivery date, on a thank-you page, an account order page or in an orders loop, or The product: release date, the Release date on a product's General tab, read on its page or in a product loop. The event is then that whole day and Starts, Ends and All day step aside. With no date, nothing shows on the page and the builder says which date is missing. Left empty, the Title becomes Delivery of order #1234, or the product's name and release.
- `title` (text) **Title**: placeholder {post_title}; dynamic data accepted. The event name. It takes dynamic data and falls back to the current post's title when empty.
- `start` (text) **Starts**: placeholder 2026-10-01 18:00; dynamic data accepted; only when `source` is not `shop_delivery` and `source` is not `shop_release`. Write it as 2026-10-01 18:00, or give a date tag that format. It is read in the site's time zone. A date of numbers such as 11/10/2026 is read in your site's date order (Settings, General): day first for d/m/Y, month first for m/d/Y. If your date format writes the month as a word, a date that could be read either way is not used, and the builder says so. Without a start, the element draws nothing on the page. Developers can set the order with the bfbe_pro/calendar_date_order filter ('dm' or 'md').
- `end` (text) **Ends**: placeholder 2026-10-01 20:00; dynamic data accepted; only when `source` is not `shop_delivery` and `source` is not `shop_release`. Leave it empty for a one hour event, or a one day event when All day is ticked. An end before the start counts as empty.
- `allDay` (checkbox) **All day**: only when `source` is not `shop_delivery` and `source` is not `shop_release`. Tick it to send calendar dates instead of times. The end date is set to the day after the last day, as calendars expect.
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

- **A date from the shop** (`source: "shop_delivery"` or `"shop_release"`, 2.0.0) changes no markup: the event is that one whole day, sent as calendar dates as with **All day**, and an empty **Title** becomes "Delivery of order #1234" or "{product}: release".
- **Open state**: the script removes `hidden` from `.bfbe-atc__menu`, sets `aria-expanded="true"` on `.bfbe-atc__main` (the caret turns 180deg) and adds `.bfbe-atc__menu--end` when the menu would leave the window.
- **Where the styling lands**: the Button group's Look run (`typography`, `background`, `hoverBackground`, `hoverColor`, `border`, `padding`) writes to `.bfbe-atc__btn`, so the menu's button, or every calendar chip in a row. `iconSize` writes to `.bfbe-atc__icon`, `caretSize` to `.bfbe-atc__caret`.
- `menuBackground`, `menuBorder`, `menuShadow`, `menuWidth` (min-inline-size), `itemGap` and `menuPadding` write to `.bfbe-atc__menu`; `itemPadding`, `itemBorder` and `linkTypography` to `.bfbe-atc__link`; `linkHoverBackground` sets `--bfbe-atc-hover`, used on hover and keyboard focus.
- `markSize` and `markColor` write to `.bfbe-atc__mark`. `gap`, `duration` and `easing` set `--bfbe-atc-gap`, `--bfbe-duration` and `--bfbe-ease` on the root.

## Wiring to other elements

Nothing targets it and it targets nothing. With WooCommerce and Pro's shop, **Date from** `source` takes the date from the shop instead of the fields:

- `shop_delivery`: the order's expected delivery date (`_bfbe_delivery_date`, saved by the Delivery feature `shop-delivery`, or the day the shopper chose at checkout), read for the order in hand: the thank-you page, the account's order page, a Customer orders loop row (`bfbe-shop-tags-and-conditions`).
- `shop_release`: the product's **Release date** (WooCommerce, Product data, General), read for the product in hand: a product page or a product loop row; a variation takes its parent's.

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

**The delivery day on the thank-you page.** From the demo shop's thank-you template (`bfb-demo-thankyou`), where it sits under the order's facts (order tags); one such fact stands beside it here. The date and the title come from the order in hand; three calendars in the menu. Trimmed: the demo's button and menu look, and the rest of the page.

```json
{
  "name": "block",
  "settings": {},
  "children": [
    { "name": "text-basic", "settings": { "text": "Order {bfbe_order_number}" } },
    { "name": "bfbe-add-to-calendar", "settings": { "source": "shop_delivery", "label": "Add the delivery day to my calendar", "layout": "menu", "calGoogle": true, "calIcs": true, "calOutlook": true } }
  ]
}
```

**A release reminder on each upcoming product.** From the fixture `fixture-shop-p8`, here in a product card of a Bricks products loop: each card's calendar reads its own product's release date, and a product without one shows no button.

```json
{
  "name": "block",
  "settings": { "hasLoop": true, "query": { "objectType": "post", "post_type": [ "product" ], "posts_per_page": 4 } },
  "children": [
    { "name": "product-title", "settings": { "tag": "h3", "linkToProduct": true } },
    { "name": "bfbe-add-to-calendar", "settings": { "source": "shop_release", "label": "Remind me of the release", "layout": "row", "calGoogle": true, "calIcs": true, "_cssClasses": "cal-release" } }
  ]
}
```

## Gotchas

- **A fresh insert draws nothing on the page.** No calendar is ticked by default, and without **Starts** (`start`) or a ticked calendar the page gets no markup at all; only the builder shows a notice. A shop source needs no `start`. <!-- src: plugins/bfb-elements-pro/elements/add-to-calendar.php:713 and :770; plugins/bfb-elements/includes/abstract-element.php:538 -->
- **A shop date that is missing hides the button.** With `source: "shop_delivery"` outside an order page or loop, or an order without a delivery date, and with `shop_release` on a product without a release date (or outside a product), nothing renders; the builder names the missing meta. Without WooCommerce, either source renders nothing. <!-- src: plugins/bfb-elements-pro/elements/add-to-calendar.php:633-662, 679-690 --> <!-- src: docs/elements/add-to-calendar.md "Shop 2.0.0: a date from the shop (row F8)" -->
- **A shop date is always a whole day.** **Starts**, **Ends** and **All day** are not offered with a shop source and are ignored if written; the event is the one day, with no time. <!-- src: plugins/bfb-elements-pro/elements/add-to-calendar.php:158-189, 691-694 -->
- **A date of numbers follows the site's own date order.** `11/10/2026`, `11.10.2026` and `11-10-26` are read in the order the site's date format (Settings, General) prints: `d/m/Y` day first, `m/d/Y` or `Y-m-d` month first. A part over 12 is the day whatever the format. Where the format prints the month as a word (WordPress's default, `F j, Y`) an ambiguous date draws no button and the builder says why; a bare Unix timestamp renders nothing. `2026-10-01 18:00` reads the same on every site. <!-- src: add-to-calendar.php stamp() and date_order() (1.0.0-beta.4); measured with dev/calendar-dates.php, 21 readings -->
- **A date tag needs a format.** A plain date tag follows the site's date format, which may use slashes; give it a format after a colon, as in `{post_date:Y-m-d H:i}`. <!-- src: add-to-calendar.php:676-677; measured 2026-10-08: {post_date} gave "October 6, 2026", {post_date:Y-m-d H:i} gave "2026-10-06 13:19" -->
- **Times are in the site's time zone unless they carry their own.** A plain time is read in the WordPress time zone and sent as UTC; a value ending in `Z` or an offset such as `+01:00` keeps that zone. <!-- src: add-to-calendar.php:563; measured 2026-10-08 with timezone_string Europe/Bucharest -->
- **A wrong end is not an error.** An empty **Ends** (`end`), or one before the start, becomes one hour after the start, or the same single day with **All day** (`allDay`). <!-- src: add-to-calendar.php:716-717 -->
- **An all-day end is the last day, inclusive.** The element adds the day calendars expect: start `2026-10-01` and end `2026-10-03` go out as `20261001/20261004`. <!-- src: add-to-calendar.php:734; measured 2026-10-08 -->
- **An empty title takes the current post's title.** On a static page that is the page's own name; inside a query loop it is the loop item's. <!-- src: add-to-calendar.php:673-675 -->
- **In a row, the Button styling moves onto the calendars.** With `layout: "row"` the icon and label sit in a plain `.bfbe-atc__lead` span that is not clickable, and `.bfbe-atc__btn` is on each calendar link, so the Look run styles the chips. The lead inherits the element's own typography, at weight 600. <!-- src: add-to-calendar.php:783-792; add-to-calendar.css:28 -->
- **The Menu group is for the menu layout.** Every Menu key except **Padding** (`menuPadding`) is hidden in a row and its selector excludes the row; **Caret size** (`caretSize`) too. `menuPadding` in a row pads the row's list. <!-- src: add-to-calendar.php:355, :404; docs/elements/add-to-calendar.md "round 350" and "round 351" -->
- **Gap is not the space between icon and label.** **Gap** (`gap`) spaces the lead and the chips of a row; the icon-to-label space is the chip's fixed `.45em`. In the menu layout the menu is positioned absolutely, so Gap has nothing to space. <!-- src: src/elements/add-to-calendar/add-to-calendar.css:2, :14, :33; plugins/bfb-elements/includes/class-assets.php:87 -->
- **A clipping ancestor cuts the menu.** The menu is `position: absolute` under the button at `z-index: 30`, so a parent with `overflow: hidden` clips it. It flips to the button's end edge only when it would leave the window. <!-- src: add-to-calendar.css:14-16; add-to-calendar.js:20-23 -->
- **The ICS file is fixed when the page renders.** It is a `data:` link built on render, and its UID comes from the title and the start, so two events sharing both are one event to a calendar app. HTML in any field is stripped; line breaks in the description survive. <!-- src: add-to-calendar.php:697-698, :755-760 -->

## Never do

- Do not insert it without `start` and at least one of `calGoogle`, `calOutlook`, `calOffice`, `calYahoo`, `calIcs`.
- Do not write `start` or `end` as a Unix timestamp, and on a site whose date format prints the month as a word, do not use a date tag without a `Y-m-d H:i` format.
- Do not add a day to `end` for an all-day event; give the last day and let the element make it exclusive.
- Do not style a row's chips with the Menu keys (`linkTypography`, `itemPadding`, `itemBorder`); use the Button group's Look keys.
- Do not set `caretSize` or any Menu key other than `menuPadding` with `layout: "row"`: the panel hides them and they are dropped.
- Do not use `gap` to space the icon from the label.
- Do not place the menu layout inside an ancestor with `overflow: hidden`.
- Do not toggle the menu's `hidden` or `aria-expanded` with a Bricks interaction; the script owns both.
- Do not write `start`, `end` or `allDay` with `source: "shop_delivery"` or `"shop_release"`.
- Do not place a `shop_delivery` calendar where no order is in hand, or a `shop_release` one outside a product page or loop.
