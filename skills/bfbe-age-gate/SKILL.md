---
name: bfbe-age-gate
description: "Use when placing, wiring or styling BFB Age Gate (`bfbe-age-gate`): a gate shown before the page can be used: a yes or no question, or a date of birth checked against a minimum age. Read before writing its settings."
---

# BFB Age Gate (`bfbe-age-gate`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-age-gate.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/age-gate/

## What it is
A gate shown before the page can be used: a yes or no question, or a date of birth checked against a minimum age. It is built on a native dialog with no close button and no Escape, so the answers are the way through. A pass is remembered for the days you choose, and a failed answer can send the visitor to another address.

**Not for:** It confirms what a visitor says and nothing more: the date is checked in the browser, and the page's content stays in the HTML underneath. The gate opens from script, so a visitor with scripts off sees the page, and whether you need one is a question for your lawyer.

**Costs a page:** CSS 1.20 KB, JS 1.32 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** yes · **In a query loop:** no · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Nestable: any Bricks element goes inside (blocks, headings, text, images, a form).
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-age-gate",
    "settings": {},
    "children": [
        {
            "name": "heading",
            "settings": {
                "text": "Are you old enough?",
                "tag": "h2"
            }
        },
        {
            "name": "text-basic",
            "settings": {
                "text": "You must be of legal age to enter this site."
            }
        }
    ]
}
```

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Gate (`bfbeGate`)
- `mode` (select) **Ask for**: options: `confirm` A yes or no (default), `dob` A date of birth. A yes or no, the default, shows two buttons. A date of birth shows day, month and year fields, checked against the Minimum age.
- `minAge` (number) **Minimum age**. The age a visitor must be, 18 unless set. Empty button labels use it too.
- `remember` (number) **Remember for (days)**. How long a pass is kept in the visitor's browser, 30 unless set. Enter 0 to keep it until the browser tab is closed.
- `redirect` (text) **Redirect on fail**: placeholder https://example.com; dynamic data accepted. An address to send the visitor to about 1.5 seconds after a failed answer. It can come from dynamic data.
- `skipLoggedIn` (checkbox) **Skip for logged-in users**. Off by default. Tick it to let logged-in users skip the gate. A logged-in administrator still sees it on every load, and a pass is never stored for them.

### Labels and messages (`bfbeText`)
- `yesLabel` (text) **Yes button**: placeholder I am 18 or older; dynamic data accepted; only when `mode` is not `dob`. The words on the button that passes. Left empty, it reads I am 18 or older, using the Minimum age.
- `noLabel` (text) **No button**: placeholder I am under 18; dynamic data accepted; only when `mode` is not `dob`. The words on the failing button. Left empty, it reads I am under 18, with the number from Minimum age. It takes dynamic data like the other labels.
- `dobLabel` (text) **Date field label**: placeholder Your date of birth; dynamic data accepted; only when `mode` is `dob`. With A date of birth, the caption over the three boxes, Your date of birth unless set.
- `invalidText` (text) **Invalid date message**: placeholder Enter a real date.; dynamic data accepted; only when `mode` is `dob`. Shown for a date that cannot exist, such as 31 February. It is kept apart from a failed answer, and reads Enter a real date unless you set it.
- `enterLabel` (text) **Enter button**: placeholder Enter; dynamic data accepted; only when `mode` is `dob`. With A date of birth, the words on the button that sends the date, Enter unless set.
- `failText` (text) **Fail message**: placeholder Sorry, you are not old enough to enter this site.; dynamic data accepted. Shown after a failed answer and announced to screen readers. The default reads Sorry, you are not old enough to enter this site.

### Panel (`bfbePanel`)
Styling only, every key in the schema file: `width`, `panelBackground`, `panelColor`, `panelPadding`, `panelBorder`, `panelShadow`, `overlay`, `overlayBlur`, `messageColor`, `messageTypography`.

### Buttons (`bfbeButtons`)
Styling only, every key in the schema file: `buttonsAlign`, `buttonTypography`, `buttonPadding`, `buttonBorder`, `buttonGap`, `yesBackground`, `yesBackgroundHover`, `yesColor`, `noBackground`, `noBackgroundHover`, `noColor`.

### Date field (`bfbeField`)
The whole group shows only when `mode` is `dob`.
- `partLabels` (checkbox) **Day, month, year labels**: only when `mode` is `dob`. Unticked, the words stay for screen readers while DD, MM and YYYY show as placeholders. Tick it to draw the words above the boxes.
- `fieldOrder` (select) **Order**: options: `site` Follow the site date format (default), `dmy` Day, month, year, `mdy` Month, day, year, `ymd` Year, month, day; only when `mode` is `dob`. The order of the day, month and year fields. Follow the site date format is the default. Or fix it to start with the day, the month or the year.
- `fieldWidth` (select) **Widths**: options: `fill` Fill the row (default), `compact` Compact; only when `mode` is `dob`. Fill the row is the default, so the three fields share the width. Choose Compact for short boxes sized to their digits.
- `fieldAlign` (select) **Align**: options: `start` Start (default), `center` Centre, `end` End; writes CSS; only when `mode` is `dob`. Choose Start, Centre or End. It places the date field's caption and, with Compact widths, the row of boxes.
Styling, in the schema file: `fieldTypography`, `partLabelTypography`, `fieldGap`, `inputTypography`, `placeholderColor`, `inputBackground`, `inputBorder`, `inputPadding`, `inputShadow`, `inputFocusBackground`, `inputFocusBorderColor`, `inputFocusShadow`.

### Motion (`bfbeMotion`)
- `effect` (select) **Effect**: options: `fade` Fade (default), `rise` Rise, `scale` Scale, `none` None. How the gate arrives and leaves. Choose Fade, the default, Rise, Scale or None.
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS. The curve the gate moves on, Snappy unless set.
Styling, in the schema file: `duration`, `easingCustom`.

## What it guarantees for accessibility (do not undo)
- On the page the gate is a native modal dialog, so the rest of the page is inert while it is open.
- Escape is ignored and there is no close button; the dialog closes when an answer passes, and reopens if anything else closes it.
- The dialog is named by the heading in the nested content and described by that content.
- Failed and invalid answers are announced through a region with role alert.
- The date of birth is a fieldset with a legend and three labeled inputs, with a numeric keyboard and birthday autofill values.
- Filling a box moves focus to the next, and Enter submits the form.
- Under reduced motion the gate and its overlay appear and leave with no transition.
<!-- bfbe:generated:end -->

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
