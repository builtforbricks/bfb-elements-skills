---
name: bfbe-copy
description: "Use when placing, wiring or styling BFB Copy to Clipboard (`bfbe-copy`): a button that copies fixed text, dynamic data, or the contents of another element on the page to the visitor's clipboard. Read before writing its settings."
---

# BFB Copy to Clipboard (`bfbe-copy`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-copy.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/copy/

## What it is
A button that copies fixed text, dynamic data, or the contents of another element on the page to the visitor's clipboard. After copying, the label and icon swap for the ones you set, then reset after a delay, and a polite live region announces it. It uses the clipboard API on secure pages and falls back to the older copy command elsewhere.

**Not for:** Anything it copies must already be in the page, either typed here or inside the element your selector finds. It cannot fetch text from a server when clicked, and it never pastes into fields.

**Costs a page:** CSS 0.45 KB, JS 0.84 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** no · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Bricks' query loop (`hasLoop`, `query`); Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### What to copy (`bfbeSource`)
- `source` (select) **Source**: options: `text` Text (default), `selector` An element on the page. Text is the default. An element on the page copies the value or text of whatever your selector matches when the button is clicked.
- `text` (textarea) **Text**: dynamic data accepted; only when `source` is not `selector`. The text to copy, in a multi-line field that accepts dynamic data, such as a coupon code from a custom field.
- `selector` (text) **CSS selector**: placeholder #coupon; only when `source` is `selector`. The element to read, such as #coupon. A form field gives its value and other elements give their text.

### Button (`bfbeButton`)
- `label` (text) **Label**: placeholder Copy; dynamic data accepted. The words on the button, Copy by default. They also name the button for screen readers, and the field accepts dynamic data.
- `icon` (icon) **Icon**. An optional icon beside the label.
- `iconPosition` (select) **Icon position**: options: `left` Left (default), `right` Right. Left of the label by default, or Right.
Styling, in the schema file: `hoverColor`, `hoverBackground`.

### Icon (`bfbeIcon`)
Styling only, every key in the schema file: `iconSize`, `iconColor`, `iconGap`.

### After copying (`bfbeDone`)
- `successLabel` (text) **Label after copying**: placeholder Copied; dynamic data accepted. The words shown once copied, Copied by default. Screen readers hear them too.
- `successIcon` (icon) **Icon after copying**. An optional icon that replaces the button's icon while the copied state shows.
- `resetAfter` (number) **Reset after (ms)**. How long the copied state stays, 2000 by default. Set 0 to keep it until the page reloads.
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS. How the swap speeds up and slows down, Snappy by default. Pick Custom and type your own curve in Custom curve.
Styling, in the schema file: `doneColor`, `doneBackground`, `doneBorder`, `duration`, `easingCustom`.

## What it guarantees for accessibility (do not undo)
- The element is a real button, so Enter and Space copy, and its name comes from the visible label.
- After a successful copy, the Label after copying text is written into a visually hidden polite live region, so screen readers announce it.
- The label and icon for the inactive state are hidden with visibility, so a screen reader meets one label at a time.
- With reduced motion requested, the label swap and the icon pop run with a duration of zero.
<!-- bfbe:generated:end -->

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
