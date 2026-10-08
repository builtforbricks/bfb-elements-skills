---
name: bfbe-business-hours
description: "Use when adding opening hours, an Open now badge or holiday hours with BFB Business Hours (`bfbe-business-hours`): a week of days and times, a live status line in the site's time zone, and dated exceptions. Read before writing its settings."
---

# BFB Business Hours (`bfbe-business-hours`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-business-hours.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/business-hours/

## What it is
Opening hours as a definition list of days and times, with an optional live status line that follows the site's time zone. The status is recalculated in the browser every minute, so a cached page does not keep showing a stale Open or Closed. Days can have two openings, a Closed switch with its own wording, and dated exceptions that appear for a window you choose.

**Not for:** The element holds one weekly schedule in the site's single time zone, so locations with different hours need one element each. It writes no structured data for search engines, so add opening-hours markup separately if you want it.

**Costs a page:** CSS 0.88 KB, JS none (gzipped), no dependencies, loaded only on pages that use it. Only where used, the live status and special dates: JS 1.48 KB.

**Nestable:** no · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** no · **Reduced motion:** yes

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Bricks' query loop (`hasLoop`, `query`); Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Days (`bfbeDays`)
- `days` (repeater) **Days**. One row per day, with Day, Label, Closed, Closed text, Opens, Closes, Opens again and Closes again. Label replaces the day's name. Text fields accept dynamic data.
- `closedText` (text) **Closed text**: placeholder Closed; dynamic data accepted; only when `show` is not `status`. The word shown for closed days, Closed by default. A day's own Closed text overrides it.
- `separator` (text) **Between the times**: placeholder -; only when `show` is not `status`. The text between an opening and a closing time, a hyphen by default.
- `breakSeparator` (text) **Between the openings**: placeholder ,; only when `show` is not `status`. The text between a day's two openings, a comma by default.
- `highlightToday` (checkbox) **Highlight today**: only when `show` is not `status`. Off by default. Today's row takes the Today styling when ticked. The day is chosen when the page is built, so a full-page cache can keep an earlier day.

### Layout (`bfbeLayout`)
- `show` (select) **Show**: options: `week` The week (default), `status` The status, `both` The status and the week. The week is the default. The status shows the Open now line alone, and The status and the week shows both. The Status group appears once the status shows.
- `statusPlace` (select) **The status sits**: options: `above` Above the week (default), `below` Below the week; only when `show` is `both`. Above the week by default, or Below the week. It appears when Show is The status and the week.
- `layout` (select) **Layout**: options: `side` Side by side (default), `stacked` Day above the hours, `across` The week across; only when `show` is not `status`. Side by side is the default. Day above the hours stacks each row, and The week across lays the days out as columns.
- `align` (select) **Align**: options: `start` Start (default), `center` Centre, `end` End; only when `layout` is `stacked` or `across` and `show` is not `status`. Start, Centre or End, with Start as the default. It lines up each day and its hours, and the status, in Day above the hours and The week across.
Styling, in the schema file: `acrossWidth`, `partsGap`.

### Status (`bfbeStatus`)
The whole group shows only when `show` is `status` or `both`.
- `builderPreview` (select) **Preview in the builder**: options: `live` Live (default), `open` Open, `soon` Closes soon, `closed` Closed. Live is the default and shows the state at the current time. Pick Open, Closes soon or Closed to see and style that state in the builder.
- `soonMinutes` (number) **Closes soon within**: placeholder 30. How many minutes before closing the status switches to Closes soon, 30 by default. Set 0 and it never says it.
- `statusOnly` (checkbox) **Just the state**. Off by default. Tick it to drop the words after the state, so the line reads Open now or Closed now with no times.
- `openText` (text) **Open**: placeholder Open now; dynamic data accepted. Under Words, your wording for each state. Open, Closing soon and Closed read Open now, Closes soon and Closed now by default.
- `soonText` (text) **Closing soon**: placeholder Closes soon; dynamic data accepted
- `closedNowText` (text) **Closed**: placeholder Closed now; dynamic data accepted
- `untilText` (text) **Until it closes**: placeholder until {time}; dynamic data accepted; only when `statusOnly` is not set. The words after the state while open, until {time} by default. Opens later today, Opens tomorrow and Opens another day do the same while closed, filling in {time} and {day}.
- `opensAtText` (text) **Opens later today**: placeholder opens at {time}; dynamic data accepted; only when `statusOnly` is not set
- `opensTomorrowText` (text) **Opens tomorrow**: placeholder opens tomorrow at {time}; dynamic data accepted; only when `statusOnly` is not set
- `opensOnText` (text) **Opens another day**: placeholder opens {day} at {time}; dynamic data accepted; only when `statusOnly` is not set
- `statusSep` (text) **Between the two**: placeholder ·; only when `statusOnly` is not set. What sits between the state and the words after it, a middle dot by default.
- `dot` (select) **Dot**: options: `none` None, `still` Still (default), `pulse` Pulsing. Still is the default. Pulsing adds an expanding ring while open or closing soon, and None removes the dot. When open, When closing soon and When closed set its colors.
Styling, in the schema file: `dotOpen`, `dotSoon`, `dotClosed`, `dotSize`, `statusTypography`, `statusBackground`, `statusPadding`, `statusBorder`.

### Special dates (`bfbeSpecial`)
- `specials` (repeater) **Special dates**. One row per exception, such as a holiday, with a Date, a Label beside it, and a day's Closed and opening fields. It overrides its weekday in the status.
- `specialsShow` (select) **Show them**: options: `none` Hide them, `7` The next 7 days, `14` The next 14 days (default), `30` The next 30 days, `all` Every one to come; only when `show` is not `status`. The next 14 days by default, or pick The next 7 days, The next 30 days, Every one to come or Hide them. Dates outside the window stay out of sight.
- `specialsTitle` (text) **Title**: placeholder None; dynamic data accepted; only when `specialsShow` is not `none` and `show` is not `status`. An optional title above the dated rows, such as Holiday hours. It accepts dynamic data.
- `dateFormat` (select) **Date format**: options: `short` Fri 25 Dec (default), `long` Friday 25 December, `day` 25 December, `site` The site's date format; only when `specialsShow` is not `none` and `show` is not `status`. A short date such as Fri 25 Dec by default. The other choices look like Friday 25 December and 25 December, plus The site's date format.
Styling, in the schema file: `specialsTitleTypography`.

### Rows (`bfbeRows`)
The whole group shows only when `show` is not `status`.
- `divided` (checkbox) **Line between rows**: only when `layout` is not `across`. Off by default. Tick it to add a divider with its own Divider colour and Divider thickness. It does not apply to The week across layout.
Styling, in the schema file: `rowPadding`, `rowGap`, `dividerColor`, `dividerWidth`, `dayWidth`, `rowBackground`, `rowBorder`.

### Day name (`bfbeDay`)
The whole group shows only when `show` is not `status`.
Styling only, every key in the schema file: `dayTypography`.

### Hours (`bfbeTime`)
The whole group shows only when `show` is not `status`.
Styling only, every key in the schema file: `timeTypography`, `closedTypography`, `sepColor`.

### Today (`bfbeToday`)
The whole group shows only when `highlightToday` is set and `show` is not `status`.
Styling only, every key in the schema file: `todayTypography`, `todayBackground`, `todayBorder`.

## What it guarantees for accessibility (do not undo)
- Days and times form a description list, with each day as a term and its hours as the description.
- Times written as times, such as 09:00 or 9am, are wrapped in time elements with a 24-hour datetime value.
- Today's row carries aria-current set to date and a visually hidden Today label when Highlight today is ticked.
- The status dot is aria-hidden and the state is plain text, which is not announced when it changes.
- A pulsing dot animates unless the visitor has asked for reduced motion, in which case the dot stays still.
<!-- bfbe:generated:end -->

## Rendered DOM

The root `div.bfbe-hours` is a flex column with a layout class (`bfbe-hours--side`, `--stacked` or `--across`),
`bfbe-hours--align-center` or `--align-end` in the last two, and `bfbe-hours--divided` for **Line between rows**. Its
parts, in order: the status when it sits above, the week, the status when it sits below, the special dates.

```html
<div class="bfbe-hours bfbe-hours--side bfbe-hours--divided">
  <p class="bfbe-hours__status bfbe-hours__status--pulse" data-bfbe-state="open" data-bfbe-live="{…}">
    <span class="bfbe-hours__dot" aria-hidden="true"></span><span class="bfbe-hours__now">Open now</span>
    <span class="bfbe-hours__then"><span class="bfbe-hours__then-sep" aria-hidden="true">·</span> <span class="bfbe-hours__then-text">until 17:00</span></span></p>
  <dl class="bfbe-hours__week">
    <div class="bfbe-hours__row bfbe-hours__row--today" aria-current="date"><dt class="bfbe-hours__day">Friday <span class="bfbe-sr">(Today)</span></dt>
      <dd class="bfbe-hours__time"><time datetime="09:00">09:00</time> <span class="bfbe-hours__sep">-</span> <time datetime="13:00">13:00</time><span class="bfbe-hours__and">,</span> <time datetime="14:00">14:00</time> …</dd></div>
    <div class="bfbe-hours__row"><dt class="bfbe-hours__day">Sunday</dt><dd class="bfbe-hours__time bfbe-hours__time--closed">Closed</dd></div></dl>
  <div class="bfbe-hours__specials" data-bfbe-window="14" data-bfbe-tz="Europe/London"><p class="bfbe-hours__specials-title">Holiday hours</p>
    <dl class="bfbe-hours__week bfbe-hours__week--special"><div class="bfbe-hours__row bfbe-hours__row--special" data-bfbe-date="2026-12-25">
      <dt class="bfbe-hours__day">Fri 25 Dec <span class="bfbe-hours__note">Christmas Day</span></dt><dd class="bfbe-hours__time bfbe-hours__time--closed">Closed</dd></div></dl></div>
</div>
```

- `data-bfbe-state` is `open`, `soon`, `closed` or `unknown`; style a state with `[data-bfbe-state="soon"]`. Each minute
  the script rewrites it, `.bfbe-hours__now` and `.bfbe-hours__then-text` from the JSON in `data-bfbe-live`, and sets
  `hidden` on the status while the state is `unknown`.
- The special dates are a second `dl.bfbe-hours__week` of `.bfbe-hours__row` rows, so the layout class and the Rows, Day
  name and Hours controls style both lists. Rows outside the window are in the HTML with `hidden`; the script applies the
  window again in the browser.
- **Space between the parts** (`partsGap`) is the root's `gap`, **Space between rows** (`rowGap`) each list's. The Rows
  group lands on `.bfbe-hours__row`, Today on `.bfbe-hours__row--today`, the status box on `.bfbe-hours__status`, and
  **Separator colour** (`sepColor`) on `.bfbe-hours__sep` between two times, not on the status's `·`.
- Custom properties: `--bfbe-hours-col` (`acrossWidth`), `--bfbe-hours-divider` and `--bfbe-hours-divider-width` on the
  root; `--bfbe-hours-dot` and `--bfbe-hours-dot-open`, `-soon` and `-closed` on `.bfbe-hours__dot`, each colour read in
  its own state only (green, amber and red by default).
- The status hugs its words, so a background and a border read as a badge. The pulse is a `::after` on the dot, written
  only under `prefers-reduced-motion: no-preference` and only while open or closing soon.
- `business-hours-live.min.js` (1.48 KB gzipped, beyond the cost line above) loads when **Show** is not The week or
  Special dates has rows, and always in the builder, where Bricks runs `bfbeHoursLive` after each render.

## Wiring to other elements

Stands alone; nothing targets it and it targets nothing. Each element works out its status from its own Days and Special
dates, so a status badge in the header and the full week on the contact page are two elements that each carry both lists.

## Verified patterns

**The status above the week, with holiday hours.** From the demo page "ZZ demo: Business Hours"
(`demo-bfb-business-hours`), its text, today and divider colours and row padding trimmed. `show: "both"` puts the status
above the week; `dot: "pulse"`, `statusBackground`, `statusPadding` and a 999 radius in `statusBorder` make it a badge.
Sunday's `open2`/`close2` is a lunch break, and `specialsShow: "all"` lists every special date to come under its title.

```json
{ "name": "bfbe-business-hours", "settings": {
  "show": "both", "dot": "pulse", "highlightToday": true, "divided": true,
  "statusBackground": { "color": { "hex": "#f0ecff" } },
  "statusPadding": { "top": "6", "right": "14", "bottom": "6", "left": "12" },
  "statusBorder": { "radius": { "top": 999, "right": 999, "bottom": 999, "left": 999 } },
  "days": [
    { "day": "mon", "open": "07:00", "close": "18:00" }, { "day": "tue", "open": "07:00", "close": "18:00" },
    { "day": "wed", "open": "07:00", "close": "18:00" }, { "day": "thu", "open": "07:00", "close": "18:00" },
    { "day": "fri", "open": "07:00", "close": "19:00" }, { "day": "sat", "open": "08:00", "close": "19:00" },
    { "day": "sun", "open": "08:00", "close": "12:00", "open2": "13:00", "close2": "16:00" } ],
  "specialsShow": "all", "specialsTitle": "Holiday hours",
  "specials": [
    { "date": "2026-12-24", "label": "Christmas Eve", "open": "07:00", "close": "14:00" },
    { "date": "2026-12-25", "label": "Christmas Day", "closed": true, "closedText": "Closed, see you on the 27th" },
    { "date": "2026-12-26", "label": "Boxing Day", "closed": true } ] } }
```

**The week across, for a footer band.** From the fixture page "FREE: Business Hours, round 402"
(`fixture-business-hours-more`). `layout: "across"` lays the days out as columns at least `acrossWidth` wide, wrapping
when the line runs out, and `rowGap` spaces them. Sunday is a row with `closed: true`, so it shows as Closed.

```json
{ "name": "bfbe-business-hours", "settings": {
  "layout": "across", "acrossWidth": "120px", "rowGap": "8px",
  "days": [
    { "day": "mon", "open": "09:00", "close": "17:00" }, { "day": "tue", "open": "09:00", "close": "17:00" },
    { "day": "wed", "open": "09:00", "close": "17:00" }, { "day": "thu", "open": "09:00", "close": "17:00" },
    { "day": "fri", "open": "09:00", "close": "13:00", "open2": "14:00", "close2": "18:00" },
    { "day": "sat", "open": "10:00", "close": "14:00" }, { "day": "sun", "closed": true } ] } }
```

**The status alone, in its own words.** Same fixture page. `show: "status"` draws one line for a header or a contact
card; `statusOnly` drops the words after the state and `dot: "none"` removes the dot. `openText`, `soonText` and
`closedNowText` replace Open now, Closes soon and Closed now. The page also has it with `dot: "pulse"` and special dates.

```json
{ "name": "bfbe-business-hours", "settings": {
  "show": "status", "statusOnly": true, "dot": "none",
  "openText": "We are open", "soonText": "Last orders", "closedNowText": "Back soon",
  "days": [
    { "day": "mon", "open": "09:00", "close": "17:00" }, { "day": "tue", "open": "09:00", "close": "17:00" },
    { "day": "wed", "open": "09:00", "close": "17:00" }, { "day": "thu", "open": "09:00", "close": "17:00" },
    { "day": "fri", "open": "09:00", "close": "13:00", "open2": "14:00", "close2": "18:00" },
    { "day": "sat", "open": "10:00", "close": "14:00" }, { "day": "sun", "closed": true } ] } }
```

## Gotchas

- **An empty day row reads as 09:00 to 17:00.** A row with neither **Opens** (`open`) nor **Closes** (`close`) shows the
  placeholders, and the status counts that day open. Tick **Closed** (`closed: true`) for a closed day. <!-- src: plugins/bfb-elements/elements/business-hours.php:1032 and :786 -->
- **Every weekday needs a row with `day` set.** A row without `day` renders and counts as Monday. A weekday with no row
  is closed for the status but missing from the list. <!-- src: plugins/bfb-elements/elements/business-hours.php:1198, :831 and :887 -->
- **The status reads times, not words.** Opens and Closes take 9, 09:30, 9.30, 9am, 5 pm, and 24:00 for a midnight close.
  Words ("By appointment", "noon") or one side left blank hide the status that day, with a notice in the builder only. <!-- src: plugins/bfb-elements/elements/business-hours.php:750, :779, :1008 and :1017 -->
- **Dynamic data must resolve to a time.** Opens and Closes resolve their tags before the status reads them, so a field
  returning 09:00:00 or a full date counts as words. Return a format such as 09:00 or 9:00 am. <!-- src: plugins/bfb-elements/elements/business-hours.php:713 and :751 -->
- **A close before the opening runs past midnight.** 18:00 to 02:00 is one overnight opening, and the status keeps it
  open into the next morning, even when that next day's hours are words. <!-- src: plugins/bfb-elements/elements/business-hours.php:800 and :894 -->
- **The times are the business's.** The status works in the site's time zone (Settings, General, Timezone) and prints
  times as typed, whatever the visitor's zone. A UTC offset there stays fixed through daylight saving; a named zone follows it. <!-- src: src/elements/business-hours-live/business-hours-live.js:12 and plugins/bfb-elements/elements/business-hours.php:993 -->
- **Today's highlight is fixed when the page is built.** **Highlight today** (`highlightToday`) is chosen on the server,
  while the status and the special dates are worked out again in the browser, so a full-page cache can mark yesterday. <!-- src: docs/elements/business-hours.md "Round 402" -->
- **Special dates steer the status whatever is shown.** A `specials` row overrides its weekday with `show: "status"` or
  `specialsShow: "none"` too, where no list is drawn. The last row for a date wins. <!-- src: plugins/bfb-elements/elements/business-hours.php:973 and :854 -->
- **A special date is `YYYY-MM-DD`.** `date` must start with a real date such as `2026-12-25`, as the builder's picker
  stores it. Any other value drops the row from the list and the status, with no notice. <!-- src: plugins/bfb-elements/elements/business-hours.php:850 -->
- **No days, nothing on the page.** The builder shows a sample week, marked as a sample, until Days has a row. The page
  draws no element at all, the status included. <!-- src: plugins/bfb-elements/elements/business-hours.php:1126 -->
- **The canvas holds states the page does not.** **Preview in the builder** (`builderPreview`) freezes the status in the
  canvas only, the canvas lists every special date whatever the window, and its `dl`, `dt` and `dd` are `div`s. <!-- src: plugins/bfb-elements/elements/business-hours.php:988 and :1102; plugins/bfb-elements/includes/abstract-element.php:419 -->
- **The week across takes the full width.** `layout: "across"` sets the root to `inline-size: 100%`, so in a row of
  elements it takes the whole line. Its columns are at least `acrossWidth` (110px by default) and wrap when seven do not fit. <!-- src: src/elements/business-hours/business-hours.css:45-50 -->

## Never do

- Do not leave a day's `open` and `close` empty to mean closed; set `closed: true`.
- Do not write a row without `day`, and do not leave out a closed weekday the list should show.
- Do not write a day's hours in words where the status shows; tick `closed` and put the words in that row's `closedText`.
- Do not feed Opens and Closes from a dynamic tag that returns seconds or a full date.
- Do not write a special date's `date` in any form but `YYYY-MM-DD`.
- Do not judge the status, the special-date window or the description list from the canvas; check the page.
- Do not rely on Highlight today on a page served from a full-page cache; exclude the page or shorten its cache.
- Do not leave the site's time zone as a UTC offset where the clocks change; pick a named zone.
