---
name: bfbe-add-to-calendar
description: "Use when placing, wiring or styling BFB Add to Calendar (`bfbe-add-to-calendar`): one button that opens a menu, or a row of buttons, linking to Google, Outlook, Office 365, Yahoo and an Apple / ICS file. Read before writing its settings."
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

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
