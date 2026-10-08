---
name: bfbe-start-here
description: "Load first in any session that builds, edits or styles with BFB Elements (the bfbe-* elements and features of the Bricks Builder pack by Built for Bricks): names and discovery, the rules of its engine that no schema shows, when to read a schema, the workflow and the never-do list. Requires Bricks 2.4+ for MCP."
---

# BFB Elements: start here

BFB Elements is an element pack for Bricks Builder: a free plugin and a Pro add-on that are one product, one set of
rules, one category. Load Bricks' own `bricks-start-here` first when it exists; this skill covers only what the pack
adds. Every per-element skill (`bfbe-modal`, `bfbe-table`, `bfbe-form`, ...) assumes you have read this one.

## Names and discovery

- Elements are named `bfbe-<thing>`: `bfbe-modal`, `bfbe-table`, `bfbe-lottie`, `bfbe-form`. The category is
  `bfb-elements`, so `bricks/list-element-types` with `category: "bfb-elements"` lists what the site has.
- Some elements only live inside a parent and have no skill of their own; their parent's skill covers them:
  `bfbe-table-row` and `bfbe-table-cell` (Table), `bfbe-snap-slide` (Snap Slider), `bfbe-timeline-item` (Content
  Timeline), `bfbe-showcase-step` and `bfbe-showcase-card` (Sticky Showcase), `bfbe-filter-item` (Filter Grid),
  `bfbe-video-control` and `bfbe-playlist-item` (Video Player), and the form's twelve parts (`bfbe-form-text`,
  `bfbe-form-choice`, `bfbe-form-number`, `bfbe-form-date`, `bfbe-form-upload`, `bfbe-form-signature`,
  `bfbe-form-repeater`, `bfbe-form-step`, `bfbe-form-progress`, `bfbe-form-summary`, `bfbe-form-total`,
  `bfbe-form-button`), all in `bfbe-form`.
- Four things are features, not elements: Hover Effects (controls on every element, Bricks' own included), Advanced
  Header Scroll (the header template and every element in it), Form Steps and Form Fields (both on Bricks' own form
  element). Each has a skill: `bfbe-hover-effects`, `bfbe-advanced-header-scroll`, `bfbe-form-steps`,
  `bfbe-form-fields`.
- **An element missing from the list is turned off, not absent.** Every element has a switch on the pack's Elements
  page (WordPress menu BFB Elements, Elements), and an element turned off leaves Bricks' registry entirely; a Pro
  element is also missing when Pro is not installed. Say which it is and stop. Never conclude the pack lacks the
  element, and never build a stand-in from other elements without saying so.

## The rules of the engine

1. **A hidden setting is dropped.** Before an element renders, the engine reads every stored setting through its
   control's `required` condition and its group's, exactly as the builder panel decides what to show, and drops any
   value whose condition is unmet. Nothing is reported. So `drawerSide: "left"` without `position: "drawer"` does
   nothing, and `url` without `source: "url"` does nothing. Write the switch and the value together, exactly as the
   panel would store them. The schema file carries every `required` clause; the per-element skill spells the
   important ones out in words.
2. **Defaults are the panel's, not the data's.** An unset select reads as its placeholder's option (the skills mark it
   "(default)"); an unset checkbox is off. Raw JSON stores nothing for a default, so write a default explicitly when the
   build depends on it, and never assume a value the schema shows as `placeholder` is stored.
3. **Bricks' universals are Bricks'.** Keys that start with `_` (`_typography`, `_padding`, `_cssClasses`,
   `_cssId`, `_cssCustom`, responsive `:tablet_portrait` suffixes, pseudo `:hover`) behave as on any Bricks element and
   are documented by Bricks' own skills; the pack's schema files leave them out.
4. **Elements are nestable where the skill says so, and children are typed.** A Table takes Table Rows, which take
   Table Cells; a Snap Slider takes Snap Slides; a form takes its own fields and steps. Pass children in one
   `bricks/add-element` call in the `{name, settings, children}` shape; the per-element skill shows the tree the
   builder itself inserts. Element ids are six characters; omit them and Bricks makes them.
5. **Target other elements by class where a selector is asked for, never by `_cssId`.** Where an element takes a
   selector (the Cursor's targets, `data-bfbe-modal-open` at a modal, Copy to Clipboard's source), use a class you set
   through `_cssClasses`, because component instances share ids. Where an element finds its partner by position (a
   Slider Controls element takes the nearest Bricks slider, a Player Control the nearest player, a Form Total its own
   form), leave the id field empty and place it next to its partner; the element's skill says which it is.
6. **Accessibility and motion are built in; leave them alone.** Every element keeps keyboard access, names its
   controls, and honours `prefers-reduced-motion`. Do not add `tabindex`, `role` or `aria-*` to an element's own
   parts, do not hide a close button, do not add a script that animates against the user's preference. The
   per-element skill lists what the element guarantees.
7. **Each element costs only the pages that use it.** Its CSS and JS load where it renders, nowhere else. The
   per-element skill states the gzipped cost; when two elements could do, weigh it.

## Read a schema before you write

- Prefer the bundled schema: `bfbe-schemas` tells you how to find `references/elements/<name>.json` and how to check
  that the bundle matches the plugin on the site (`verifiedUpTo` against `bricks/get-system-information`).
- Live: `bricks/get-element-schema` with `elementName` and, for a few settings, `controlKeys`. The two are the same
  data; the bundle saves the call.
- A control's `options` gives the stored values (the keys) and their labels; `required` is the condition; `css` says
  the control writes CSS onto the named part; `hasDynamicData` says a `{tag}` is accepted.

## Workflow

1. Confirm the element is on the site (`bricks/list-element-types`, category `bfb-elements`), and which pack it needs.
2. Load the element's skill; read the schema file for the controls you will set.
3. Build the tree from the skill's structure section; set switches and their values together; write defaults you rely on.
4. Write it (`bricks/add-element` or the page-level abilities), then read it back and verify on the frontend.
5. Where the skill names a gotcha, check it in the rendered page before you report done.

## Never do

- Write a setting without its switch (rule 1).
- Guess a control key or an option value: read the schema file.
- Conclude an element does not exist because the registry lacks it (it is off, or Pro is absent); build a stand-in silently.
- Target an element by `_cssId`.
- Put a child element outside its parent, or a non-child inside a typed parent (a `block` as a Table's row).
- Undo an element's accessibility or motion behaviour with your own attributes or scripts.
- Edit the generated block of a skill or anything under `references/`: the plugin's release writes them.
