---
name: bfbe-form-steps
description: "Use when turning Bricks' own form (`form`) into a multi-step form or wizard with BFB Form Steps (`form-steps`): fields that start a step, step marks or a progress bar, Back and Next, a summary to check before sending, a step shown only when a field has a value. Read before writing its settings."
---

# BFB Form Steps (`form-steps`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.3 or later. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/form-steps.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/form-steps/

## What it is
A feature on Bricks' own form, not a separate element: tick Starts a new step on a field and the form shows one step at a time. Back, Next and a progress display come with it, and Next checks the step's own fields before moving on. The submission stays Bricks' own, and the form can end with a summary of every answer with a Change link per step.

**Not for:** Not a separate element, so there is no Steps element to drop in: the steps live on Bricks' own form. For steps with a live total, rules beyond one field's value, or Save for later, build the form with BFB Advanced Forms.

**Nestable:** no · **In a query loop:** no · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Where it lives
A feature, not an element: its controls are added to Bricks' own form element (`form`).
It also adds controls to each field of the form (the rows of its `fields` repeater), listed under `fieldControls` in the schema file: `bfbeStep`, `bfbeStepTitle`, `bfbeStepText`, `bfbeStepHeading`, `bfbeStepWhen`, `bfbeStepValue`.

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
- `stepsBack` (text) **Label**: placeholder Back; dynamic data accepted. The words on the button, Back unless set. It takes dynamic data.
- `stepsBackIcon` (icon) **Icon**. An icon beside the words. Icon position puts it Before the words, the default, or After the words.
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
- `stepsChange` (text) **Label**: placeholder Change; dynamic data accepted. The button's words, Change unless set. It takes dynamic data.
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

## Rendered DOM

The server adds attributes to the form Bricks renders; the script then holds the form's own nodes in two panels. Every field wrapper stays Bricks' `.form-group`. On the page, after the script:

```html
<form id="brxe-…" class="brxe-form bfbe-fs bfbe-fs--first" data-element-id="…" data-bfbe-steps="{…}" data-bfbe-motion="slide" data-bfbe-live="1">
  <div class="bfbe-fs__head" tabindex="-1">                      <!-- steps panel -->
    <div class="bfbe-pc__progress bfbe-pc--marks-titles" data-bfbe-progress="1">
      <p class="bfbe-pc__count" aria-live="polite">Step 1 of 4</p>
      <div class="bfbe-pc__rail"><ol class="bfbe-pc__marks">
        <li class="bfbe-pc__mark is-current"><button type="button" class="bfbe-pc__mark-btn" data-bfbe-mark="0" aria-current="step">
          <span class="bfbe-pc__mark-n"><span>1</span></span><span class="bfbe-pc__mark-body"><span class="bfbe-pc__mark-t">You</span><span class="bfbe-pc__mark-d">…</span></span></button></li>
        <li class="bfbe-pc__mark"><button type="button" class="bfbe-pc__mark-btn" data-bfbe-mark="1" disabled>…</button></li>
      </ol><div class="bfbe-pc__bar" role="progressbar" aria-valuenow="1" aria-valuemax="4"><span class="bfbe-pc__bar-fill"></span></div></div>
    </div>
  </div>
  <div class="bfbe-fs__fields">                                   <!-- form panel -->
    <div class="bfbe-fs__ui bfbe-fs__lead"><p class="bfbe-fs__lead-title">You</p><p class="bfbe-fs__lead-text">…</p></div>
    <div class="bfbe-fs__rows">
      <div class="form-group" data-bfbe-step="You" data-bfbe-step-text="…">…</div>
      <div class="form-group bfbe-fs__off" data-bfbe-step="The work">…</div>
      <div class="bfbe-fs__ui bfbe-fs__summary bfbe-sum bfbe-fs__off" data-bfbe-summary="{…}"></div>
    </div>
    <div class="bfbe-fs__ui bfbe-fs__nav">
      <div class="form-group submit-button-wrapper">…</div>         <!-- Bricks' Send, moved in -->
      <button type="button" class="bricks-button bfbe-fs__next …"><span class="text">Next</span></button>
      <button type="button" class="bricks-button bfbe-fs__back …" hidden><span class="text">Back</span></button>
    </div>
  </div>
</form>
```

- Nothing is added, and no file loads, unless a field has `bfbeStep`. Then the form gets `bfbe-fs`, `data-bfbe-steps` (labels, switches and the panel markup with one mark to copy per step), `data-bfbe-motion`, and `bfbe-fs--back-text` with `stepsBackStyle: "text"`. In the canvas it carries `data-bfbe-free`, `data-bfbe-live` or neither, by `builderView`, plus `bfbe-fs--canvas`. A wrapper that starts a step carries `data-bfbe-step` (its title, possibly empty), and `data-bfbe-step-text` and `data-bfbe-step-heading` when set.
- States: the form toggles `bfbe-fs--first`, `bfbe-fs--last` and, after a send with `stepsClear`, `bfbe-fs--done`. Groups off the current step get `bfbe-fs__off` (`display: none`); the step coming in gets `bfbe-fs__in` with `data-bfbe-dir="next"` or `"back"`. Marks take `is-current` and `is-done`, a skipped step's mark `hidden`; Back and Next take `hidden`. Send's wrapper is hidden by the stylesheet until `bfbe-fs--last`.
- Without **Show the count** the count is `p.bfbe-sr.bfbe-pc__count-sr`, still a live region; `.bfbe-fs__head` takes focus on each step change, so it is read out. The bar's fill reads `--bfbe-pc-progress` (0 to 1) on `.bfbe-pc__progress`.
- Where styling lands: Steps panel on `.bfbe-fs__head`, Form panel on `.bfbe-fs__fields` (Column gap on `.bfbe-fs__rows`, the button keys on `.bfbe-fs__nav`), Step heading on `.bfbe-fs__lead`. The mark groups write `.bfbe-pc__*`; Next and Back write `.bfbe-fs__nav .bfbe-fs__next.bricks-button` and `.bfbe-fs__back`. The summary groups write `.bfbe-sum__step`, `.bfbe-sum__row > dt`, `> dd` and `.bfbe-sum__change`. `stepsPosition` and `stepsPanelWidth` set `--bfbe-fs-pos` and `--bfbe-fs-rail` on the form.

## Wiring to other elements

- **Host.** Bricks' own `form`, nothing else. BFB Advanced Forms (`bfbe-form`) has steps of its own, built from Form Step elements; see that skill.
- **The per-field keys are not in the schema file.** They sit on each row of `fields`, after `label`:
  - `bfbeStep` (checkbox) **Starts a new step**: `true` opens a step at this field; it runs to the next field with `bfbeStep`.
  - `bfbeStepTitle` **Step title** and `bfbeStepText` **Step description** (text): plain words, tags stripped. Offered only with `bfbeStep`, as are the three below.
  - `bfbeStepHeading` (select) **Above the fields**: `none`, `title` or `both`; unset, it follows the form's `stepsHeading`.
  - `bfbeStepWhen` (text) **Show this step only when field**: another row's `id`. `bfbeStepValue` (text) **Has the value**: empty for any value, `a, b` for one of several, `!a` for anything but.
- **BFB Form Fields** (`bfbe-form-fields`) shares the rows: cards, pills and a field's own condition (`bfbeShowWhen`). Its script runs the step condition too; a step with every field hidden is skipped with its mark.
- **Bricks' submit stays Bricks'.** Send is moved into the button row and posts every field. The script listens for Bricks' `bricks/form/error` (back to the step holding the error) and `bricks/form/success` (with `stepsClear`), matched on the form's `data-element-id`.
- **Listening.** The form dispatches `bfbe/step` on itself, not bubbling, on every change: `detail.at` (from 0), `detail.of`, `detail.focus`. After adding a stepped form by script, call `window.bfbeFormSteps()`.
- **By class, never `_cssId`.** Reach the form from your own CSS or script through a class in `_cssClasses`: component instances share ids.

## Verified patterns

**Numbered marks with titles, beside the fields.** From the Form Steps fixture (`fixture-form-steps`), "Steps, titles". An HTML field opens the first step as an intro. Its last field, a hidden "Source" carrying the fixture's name, is dropped.

```json
{ "name": "form", "settings": {
  "stepsMarks": "titles", "stepsCount": true,
  "showLabels": true, "requiredAsterisk": true, "submitButtonText": "Send",
  "actions": ["save-submission"], "successMessage": "Thanks, it went through.",
  "fields": [
    { "id": "st1int", "type": "html", "label": "Intro", "html": "<p>Three short steps. Nothing is sent before the last one.</p>", "bfbeStep": true, "bfbeStepTitle": "About you" },
    { "id": "st1nam", "type": "text", "label": "Name", "required": true, "placeholder": "Your name" },
    { "id": "st1eml", "type": "email", "label": "Email", "required": true, "placeholder": "you@example.com", "errorMessage": "We need a working email address." },
    { "id": "st2typ", "type": "select", "label": "What is it about", "required": true, "options": "A new site\nA redesign\nSomething else", "placeholder": "Choose one", "bfbeStep": true, "bfbeStepTitle": "Your project" },
    { "id": "st2bud", "type": "radio", "label": "Budget", "required": true, "options": "Under 2k\n2k to 5k\nOver 5k" },
    { "id": "st2fea", "type": "checkbox", "label": "Needs", "options": "Shop\nBlog\nBookings" },
    { "id": "st3msg", "type": "textarea", "label": "Anything else", "placeholder": "Optional", "bfbeStep": true, "bfbeStepTitle": "Send it" }
  ]
} }
```

**Steps on the right, above the fields on phones, ending in a summary.** From the Form Steps demo (`demo-bfb-form-steps`). `stepsPosition` and `stepsWords` change at `mobile_landscape`, so a phone shows the numbers in a row above. Dropped: the painted panels and buttons, the Form Fields keys and the "Which one" field its condition showed.

```json
{ "name": "form", "settings": {
  "stepsPosition": "2", "stepsPosition:mobile_landscape": "3",
  "stepsMarks": "titles", "stepsWords:mobile_landscape": "none",
  "stepsHeading": true, "stepsSummary": true, "stepsCount": true,
  "showLabels": true, "requiredAsterisk": true, "submitButtonText": "Send the enquiry",
  "actions": ["save-submission"], "successMessage": "Thanks. We will come back today with a number.",
  "fields": [
    { "id": "rl1nam", "type": "text", "label": "Your name", "required": true, "placeholder": "First and last", "bfbeStep": true, "bfbeStepTitle": "You", "bfbeStepText": "Who we should come back to." },
    { "id": "rl1frm", "type": "text", "label": "Firm", "required": true, "placeholder": "The name over the door" },
    { "id": "rl1eml", "type": "email", "label": "Email", "required": true, "placeholder": "you@firm.co.uk" },
    { "id": "rl2trd", "type": "radio", "label": "What do you do", "required": true, "options": "Heating and plumbing\nElectrical\nRefrigeration\nSomething else", "bfbeStep": true, "bfbeStepTitle": "The work", "bfbeStepText": "So we know which plan fits." },
    { "id": "rl2siz", "type": "radio", "label": "Engineers on the road", "required": true, "options": "2 to 5\n6 to 15\n16 to 40\nMore than 40" },
    { "id": "rl3now", "type": "radio", "label": "What are you using now", "options": "Paper and a whiteboard\nSpreadsheets\nAnother system", "bfbeStep": true, "bfbeStepTitle": "Today", "bfbeStepText": "What we would be moving you off." },
    { "id": "rl4msg", "type": "textarea", "label": "Anything we should know", "placeholder": "Optional", "bfbeStep": true, "bfbeStepTitle": "Send it", "bfbeStepText": "Check it over and send." }
  ]
} }
```

**A bar above the fields, Back as a link, fading.** From the six designed forms (`fixture-form-steps-designed`), "Havenly". Both buttons sit at the end (`stepsNav: "flex-start"` is End) and Send takes size `xl`. Kept: **Done colour**, the bar's fill. Dropped: the rest of the styling and the Form Fields keys.

```json
{ "name": "form", "settings": {
  "stepsPosition": "3", "stepsMarks": "bar", "stepsCount": true, "stepsHeading": true,
  "stepsAccent": { "hex": "#b4654a" },
  "stepsBackStyle": "text", "stepsNav": "flex-start", "stepsMotion": "fade", "stepsDuration": 240,
  "showLabels": true, "requiredAsterisk": true, "submitButtonText": "Join the list", "submitButtonSize": "xl",
  "actions": ["save-submission"], "successMessage": "You are on the list. The first making run opens in the spring.",
  "fields": [
    { "id": "hvname", "type": "text", "label": "Your name", "required": true, "placeholder": "First and last", "bfbeStep": true, "bfbeStepTitle": "You", "bfbeStepText": "Where the invitation goes." },
    { "id": "hvmail", "type": "email", "label": "Email", "required": true, "placeholder": "you@example.co.uk" },
    { "id": "hvwant", "type": "checkbox", "label": "What are you after", "options": "Beds\nTables\nSeating\nStorage", "bfbeStep": true, "bfbeStepTitle": "The pieces", "bfbeStepText": "Pick as many as you like." },
    { "id": "hvroom", "type": "select", "label": "Which room comes first", "options": "Bedroom\nLiving room\nKitchen and dining\nStudy", "placeholder": "Choose one" },
    { "id": "hvarea", "type": "select", "label": "Where are you", "required": true, "options": "Scotland\nThe North\nThe Midlands\nWales\nThe South\nLondon", "placeholder": "Choose one", "bfbeStep": true, "bfbeStepTitle": "Delivery", "bfbeStepText": "We open one region at a time." },
    { "id": "hvpost", "type": "text", "label": "Postcode", "placeholder": "The first half is enough" }
  ]
} }
```

## Gotchas

- **The first field must start a step.** Fields above the first `bfbeStep` make an untitled step of their own, counted in the marks and the count. <!-- src: src/elements/form-steps/form-steps.js:49-56 -->
- **Under two steps, no steps.** Fields that group into one step leave the plain form, unless **End with a summary** adds a second. <!-- src: src/elements/form-steps/form-steps.js:58-59 -->
- **Titles on the marks need asking for.** `stepsMarks` is `numbers` unless set, which hides every title; `full` shows titles, `titles` adds the descriptions. Above the fields, a title shows with `stepsHeading` or the field's `bfbeStepHeading`. <!-- src: src/elements/form-progress/form-progress.css:75 --> <!-- src: plugins/bfb-elements-pro/includes/class-form-progress-parts.php:236-244 --> <!-- src: src/elements/form-steps/form-steps.js:79-84 -->
- **Placement's values read backwards.** The row is reversed, so `stepsNav: "flex-end"` is Start and `"flex-start"` is End; `space-between` (the default) puts Back at the start. <!-- src: plugins/bfb-elements-pro/includes/class-form-steps.php:364-373 --> <!-- src: src/elements/form-steps/form-steps.css:91-98 -->
- **Back and Next wear the form's Field border.** Unset, their Border is Bricks' `fieldBorder`, written under the form's id, which the pack's stylesheet cannot outrank. Set `stepsNextBorder` and `stepsBackBtnBorder`; a width of 0 counts. <!-- src: docs/elements/form-steps.md (round 327, "Left unset, the Border on Back or Next") --> <!-- src: src/elements/form-steps/form-steps.js:108-121 -->
- **Send has a Size but no padding.** Back and Next copy its colour and size classes, but their own Padding never reaches it. Match them with `submitButtonSize` (all six designed forms use `xl`), or leave Next and Back unpadded. <!-- src: src/elements/form-steps/form-steps.js:109 --> <!-- src: docs/elements/form-steps.md ("Two things a designer meets on the way") -->
- **A step condition needs Form Fields switched on.** `bfbeStepWhen` reaches the page through Form Fields' script. With that feature off, the step always shows, yet the server still drops its answers when the condition fails. <!-- src: plugins/bfb-elements-pro/includes/class-form-fields.php:441-443 --> <!-- src: plugins/bfb-elements-pro/includes/class-plugin.php:152-163 --> <!-- src: plugins/bfb-elements-pro/includes/class-form-engine.php:307-325 -->
- **Switched off, the feature is gone.** With Form Steps off on the BFB Elements admin page (`form-steps` in the `bfbe_features_off` option), the form has no step controls and no steps; saved keys wait for it to come back. <!-- src: plugins/bfb-elements-pro/includes/class-plugin.php:147-154 -->
- **The canvas checks nothing.** `builderView` is `free` unless set: any mark or Next moves on with no field checked. `live` checks as the page does; `open` shows every step at once. <!-- src: plugins/bfb-elements-pro/includes/class-form-steps.php:672-678 --> <!-- src: src/elements/form-wizard/form-wizard.js:53 -->
- **Nothing still keeps its panel.** With `stepsMarks: "none"` beside the fields, the steps panel keeps its width (`stepsPanelWidth`, 260px unless set) and stays empty unless the count shows. The designed restaurant form sets `stepsPosition: "3"` with it. <!-- src: src/elements/form-steps/form-steps.css:48-53 --> <!-- src: plugins/bfb-elements-pro/includes/class-form-progress-parts.php:230-248 --> <!-- src: dev/fixtures/form-steps-designed.php:596-604 -->
- **The summary and the missing list read the labels.** Without `showLabels` Bricks prints no field labels: summary rows lose their names and the missing list leaves those fields out. A radio or checkbox group is named by its first option instead. <!-- src: src/elements/form-summary/form-summary.js:65-68 --> <!-- src: src/elements/form-steps/form-steps.js:133-138 -->
- **The words need their `%s`.** A `stepsMissingText` without `%s` is ignored, and the default "Still needed:" sentence shows instead. <!-- src: plugins/bfb-elements-pro/includes/class-form-steps.php:664-667 -->

## Never do

- Do not leave the form's first field without `bfbeStep: true`.
- Do not put Form Steps keys on `bfbe-form`; build its steps from Form Step elements.
- Do not write `stepsNav: "flex-end"` for End; End is `"flex-start"`.
- Do not set `bfbeStepWhen` on a site with Form Fields switched off.
- Do not leave `stepsNextBorder` and `stepsBackBtnBorder` unset on a form with a `fieldBorder`.
- Do not turn `showLabels` off on a form with `stepsSummary` or `stepsSayMissing`.
- Do not judge the steps in the canvas; read the page, or set `builderView: "live"`.
- Do not hide `.bfbe-fs__head` or the count with CSS to lose an empty panel; set `stepsPosition: "3"`, so the count's live region stays.
