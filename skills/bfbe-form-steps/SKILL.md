---
name: bfbe-form-steps
description: "Use when placing, wiring or styling BFB Form Steps (`form-steps`): a feature on Bricks' own form, not a separate element: tick Starts a new step on a field and the form shows one step at a time. Read before writing its settings."
---

# BFB Form Steps (`form-steps`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.2 or later. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/form-steps.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/form-steps/

## What it is
A feature on Bricks' own form, not a separate element: tick Starts a new step on a field and the form shows one step at a time. Back, Next and a progress display come with it, and Next checks the step's own fields before moving on. The submission stays Bricks' own, and the form can end with a summary of every answer with a Change link per step.

**Not for:** Not a separate element, so there is no Steps element to drop in: the steps live on Bricks' own form. For steps with a live total, rules beyond one field's value, or Save for later, build the form with BFB Advanced Forms.

**Nestable:** no · **In a query loop:** no · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Where it lives
A feature, not an element: its controls are added to Bricks' own form element (`form`).

## Settings that decide the build

### Steps (`bfbeSteps`)
- `stepsHeading` (checkbox) **Step titles**. Off by default. Tick it to put each step's title and description above its fields, styled in the Step heading group.
- `stepsSummary` (checkbox) **End with a summary**. Off by default. Tick it to add a last step that lists every answer, with a Change link back to each step.
- `stepsClear` (checkbox) **Clear the form on success**. Off by default. Tick it to leave the success message on its own, with every step marked done.
- `stepsStill` (checkbox) **Keep the page still**. Off by default, so a step change scrolls to the form. Tick it to hold the page where it is.

### Steps panel (`bfbeStepsPanel`)
- `stepsPosition` (select) **Steps position**: options: `1` Left of the fields (default), `2` Right of the fields, `3` Above the fields; writes CSS. Left of the fields is the default. Choose Right of the fields or Above the fields, per breakpoint. Under 576px of the form's own width the panels stack whatever you pick.
Styling, in the schema file: `stepsPanelWidth`, `stepsPanelSpace`, `stepsPanelPadding`, `stepsPanelBackground`, `stepsPanelBorder`, `stepsPanelShadow`.

### Form panel (`bfbeFormPanel`)
- `stepsNav` (select) **Placement**: options: `space-between` Back at the start, the rest at the end (default), `flex-end` Start, `center` Centre, `flex-start` End, `stretch` Stretch; writes CSS. Under The buttons heading, where Back, Next and Send sit. Back at the start, the rest at the end is the default. The others are Start, Centre, End and Stretch, per breakpoint.
- `stepsNavPin` (select) **Position**: options: `0px` Under the fields (default), `auto` At the foot of the panel; writes CSS. Under the fields, the default, or At the foot of the panel.
- `stepsSayMissing` (checkbox) **Say what is still missing**. Tick it to list, under the buttons, the required fields still empty. The list updates as the visitor fills them in.
- `stepsMissingText` (text) **The words**: placeholder Still needed: %s; only when `stepsSayMissing` is set. The sentence for that list, Still needed: %s unless set, where %s stands for the fields. Missing list typography styles it.
Styling, in the schema file: `stepsFieldsWidth`, `stepsFieldsPadding`, `stepsFieldsBackground`, `stepsFieldsBorder`, `stepsFieldsShadow`, `stepsFieldsGap`, `stepsNavGap`, `stepsNavSpace`, `stepsMissingTypography`.

### Step marks (`bfbeMarks`)
- `stepsMarks` (select) **Show**: options: `full` Numbers and titles, `titles` Numbers, titles and descriptions, `numbers` Numbers (default), `bar` The bar only, `none` Nothing. Numbers is the default. The other choices are Numbers and titles, Numbers, titles and descriptions, The bar only, and Nothing.
- `stepsMarkClick` (select) **Clicking a mark**: options: `behind` Goes back to a step behind (default), `any` Goes to any step, `none` Does nothing; only when `stepsMarks` is not `bar` or `none`. Goes back to a step behind is the default. Choose Goes to any step, or Does nothing so the marks cannot be pressed.
- `stepsMarksWrap` (select) **Wrap**: options: `wrap` Wrap (default), `nowrap` No wrap, `wrap-reverse` Wrap reverse; writes CSS; only when `stepsMarks` is not `bar` or `none`
- `stepsWords` (select) **Titles and descriptions**: options: `flex` Shown (default), `none` Hidden; writes CSS; only when `stepsMarks` is `full` or `titles`. With Numbers and titles or Numbers, titles and descriptions, Shown or Hidden, per breakpoint, so a phone can show the numbers alone.
Styling, in the schema file: `stepsAccent`, `stepsMarkFade`, `stepsMarksDirection`, `stepsMarksJustify`, `stepsMarksAlign`, `stepsMarkGap`, `stepsMarkRowGap`, `stepsMarkGrow`, `stepsMarkShrink`, `stepsMarkBasis`, `stepsMarkInDirection`, `stepsMarkInJustify`, `stepsMarkInAlign`, `stepsNumGap`, `stepsTitleTypography`, `stepsCurrentTitleTypography`, `stepsTextTypography`, `stepsTextGap`.

### Mark number (`bfbeMarkNumber`)
The whole group shows only when `stepsMarks` is not `bar` or `none`.
- `stepsMarkNumber` (select) **Show it as**: options: `plain` 1 (default), `pad` 01, `word` Step 1, `none` No number. 1, the default, 01, Step 1 or No number.
- `stepsMarkPlain` (checkbox) **Just the figure**: only when `stepsMarkNumber` is not `none`. Under The chip heading, tick it to show the number with no chip behind it.
- `stepsMarkTick` (checkbox) **Done shows a tick**: only when `stepsMarkNumber` is not `none`. Tick it to show a tick in place of the number on a step that is done.
Styling, in the schema file: `stepsMarkTypography`, `stepsMarkSize`, `stepsMarkPadding`, `stepsMarkBorder`, `stepsMarkBackground`, `stepsMarkColor`, `stepsMarkOnBackground`, `stepsCurrent`, `stepsMarkDoneBackground`, `stepsTick`.

### Mark box (`bfbeMarkBox`)
The whole group shows only when `stepsMarks` is not `bar` or `none`.
Styling only, every key in the schema file: `stepsBoxPadding`, `stepsBoxBorder`, `stepsBoxBackground`, `stepsBoxColor`, `stepsBoxBorderColor`, `stepsBoxNowBackground`, `stepsBoxNowColor`, `stepsBoxNowBorder`, `stepsBoxDoneBackground`, `stepsBoxDoneColor`, `stepsBoxDoneBorder`.

### Step line (`bfbeStepLine`)
The whole group shows only when `stepsMarks` is not `none`.
- `stepsBarStyle` (select) **The line**: options: `fill` A bar that fills (default), `rule` A rule under the marks, `none` None. A bar that fills, the default, A rule under the marks with a thick line under the current step, or None.
- `stepsLineAt` (select) **Line position**: options: `under` Under the marks, `left` On the left (default), `right` On the right; writes CSS; only when `stepsBarStyle` is `` or `fill` and `stepsMarks` is not `bar` or `none` and `stepsPosition` is not `3` and `stepsMarksDirection` is not `row` or `row-reverse`. With the steps beside the fields, Under the marks, On the left, the default here, or On the right.
Styling, in the schema file: `stepsMarksSpace`, `stepsLine`, `stepsBarFill`, `stepsBarHeight`, `stepsBarBorder`.

### Count (`bfbeCount`)
- `stepsCount` (checkbox) **Show the count**. Off by default. Tick it to show the count text, Step 2 of 4. Screen readers hear it on every change, shown or hidden.
Styling, in the schema file: `stepsCountTypography`, `stepsCountGap`.

### Step heading (`bfbeLead`)
The whole group shows only when `stepsHeading` is set.
Styling only, every key in the schema file: `stepsLeadTitleTypography`, `stepsLeadTextTypography`, `stepsLeadAlign`, `stepsLeadGap`.

### Next button (`bfbeNextButton`)
- `stepsNext` (text) **Label**: placeholder Next; dynamic data accepted. The words on the button, Next unless set. It takes dynamic data.
- `stepsNextIcon` (icon) **Icon**. An icon beside the words. Icon position puts it After the words, the default, or Before the words.
- `stepsNextIconPosition` (select) **Icon position**: options: `right` After the words (default), `left` Before the words; only when `stepsNextIcon` is set
Styling, in the schema file: `stepsNextTypography`, `stepsNextPadding`, `stepsNextBackground`, `stepsNextBorder`, `stepsNextShadow`, `stepsNextHoverBackground`, `stepsNextHoverColor`, `stepsNextHoverBorder`.

### Back button (`bfbeBackButton`)
- `stepsBack` (text) **Label**: placeholder Back; dynamic data accepted. The words on the button, Next unless set. It takes dynamic data.
- `stepsBackIcon` (icon) **Icon**. An icon beside the words. Icon position puts it After the words, the default, or Before the words.
- `stepsBackIconPosition` (select) **Icon position**: options: `right` After the words, `left` Before the words (default); only when `stepsBackIcon` is set
- `stepsBackStyle` (select) **Looks**: options: `outline` A button (default), `text` A link. A button, the default, or A link, which shows Back as underlined text.
Styling, in the schema file: `stepsBackBtnTypography`, `stepsBackBtnPadding`, `stepsBackBtnBackground`, `stepsBackBtnBorder`, `stepsBackBtnShadow`, `stepsBackBtnHoverBackground`, `stepsBackBtnHoverColor`, `stepsBackBtnHoverBorder`.

### Summary (`bfbeSummary`)
The whole group shows only when `stepsSummary` is set.
- `stepsSummaryTitle` (text) **Summary title**: placeholder Summary. The name of the summary step and its mark, Summary unless set.
- `stepsEmpty` (text) **An empty answer reads**: placeholder Not given. What the summary shows for an answer left empty, Not given unless set.
- `stepsSkipEmpty` (checkbox) **Leave empty answers out**. Tick it to drop empty answers from the summary.
- `stepsByStep` (select) **Grouped**: options: `steps` By step, with a Change link each (default), `flat` One list. By step, with a Change link each, the default, or One list.

### Summary steps (`bfbeSumSteps`)
The whole group shows only when `stepsSummary` is set and `stepsByStep` is not `flat`.
- `stepsSumLines` (checkbox) **A line between them**
Styling, in the schema file: `stepsSumGap`, `stepsSumStepBackground`, `stepsSumStepBorder`, `stepsSumStepShadow`, `stepsSumStepPadding`, `stepsSumStepGap`, `stepsSumTitleTypography`.

### Summary rows (`bfbeSumRows`)
The whole group shows only when `stepsSummary` is set.
- `stepsSumStack` (select) **Label and answer**: options: `beside` Side by side (default), `under` Answer under the label; writes CSS. Side by side, the default, or Answer under the label, per breakpoint.
Styling, in the schema file: `stepsSumColumns`, `stepsSumAnswerColumn`, `stepsSumRowGap`, `stepsSumPairGap`, `stepsSumRowBackground`, `stepsSumRowBorder`, `stepsSumRowShadow`, `stepsSumRowPadding`, `stepsSumLabelTypography`, `stepsSumValueTypography`.

### Summary Change button (`bfbeSumChange`)
The whole group shows only when `stepsSummary` is set and `stepsByStep` is not `flat`.
- `stepsChange` (text) **Label**: placeholder Change; dynamic data accepted. The words on the button, Next unless set. It takes dynamic data.
- `stepsChangePlace` (select) **Place**: options: `title` In the title line (default), `below` Under the answers; writes CSS. In the title line, the default, or Under the answers. Align puts it at the Start, Centre or End, End unless set.
- `stepsChangeAlign` (select) **Align**: options: `start` Start, `center` Centre, `end` End (default); writes CSS
Styling, in the schema file: `stepsChangeTypography`, `stepsChangeBackground`, `stepsChangeBorder`, `stepsChangePadding`, `stepsChangeHoverBackground`, `stepsChangeHoverColor`.

### Motion (`bfbeMotion`)
- `stepsMotion` (select) **Transition**: options: `slide` Sliding (default), `fade` Fading, `none` At once. How one step gives way to the next. Sliding is the default. Choose Fading or At once to change it.
- `stepsEasing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS; only when `stepsMotion` is not `none`. The curve of the change, Snappy unless set. It is hidden when Transition is At once.
Styling, in the schema file: `stepsDuration`, `stepsEasingCustom`.

### In the builder (`bfbeBuilder`)
- `builderView` (select) **Show it**: options: `free` One step at a time, click any step (default), `open` Every step and field open, so you can style them, `live` Working, as on the site. One step at a time, click any step, the default, Every step and field open, so you can style them, or Working, as on the site, which checks the fields as the site does.

## What it guarantees for accessibility (do not undo)
- Next checks the step's own fields, shows the error for the earliest one that fails and puts focus on it.
- Enter in a text field moves to the next step, and Enter on the last step sends the form.
- Back and Next are real buttons, Back is hidden on the opening step, and Send stays hidden until the last step.
- Step marks are buttons, and the current one carries aria-current="step".
- Marks ahead of the current step are disabled unless Clicking a mark is set to Goes to any step.
- The count text, Step 2 of 4, is announced through a polite live region on every change, shown or hidden.
- Reduced motion cuts the step change instead of sliding it, and scrolls to the form without gliding.
<!-- bfbe:generated:end -->

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
