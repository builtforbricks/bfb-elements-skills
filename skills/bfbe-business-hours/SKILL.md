---
name: bfbe-business-hours
description: "Use when placing, wiring or styling BFB Business Hours (`bfbe-business-hours`): opening hours as a definition list of days and times, with an optional live status line that follows the site's time zone. Read before writing its settings."
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

**Costs a page:** CSS 0.88 KB, JS none (gzipped), no dependencies, loaded only on pages that use it.

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

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
