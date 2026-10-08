---
name: bfbe-schemas
description: "Consult before writing settings for any BFB Elements element or feature (bfbe-*): the bundled, release-exported control schemas, how to check the bundle against the plugin version on the site, and how to read a schema file. Saves the live bricks/get-element-schema call when the bundle is current."
---

# BFB Elements: the bundled schemas

`references/index.json` and `references/elements/*.json` (plus `references/features/*.json`) are every BFB
element's controls as the plugin registers them, exported by the plugin's own release from the plugins as built:
the same data the live `bricks/get-element-schema` ability returns for that element, minus Bricks' universal `_`
controls. They are never edited by hand.

## Workflow

1. **Check the version.** Read `verifiedUpTo` in `references/index.json` (not `version`, which is this pack's own
   release number). Read the plugin version on the site: `bricks/get-system-information`, then in its `plugins`
   array the entry named **"BFB Elements for Bricks Builder"** (the free plugin; **"BFB Elements Pro"** for Pro, same
   version when both are current). Compare as versions, not strings: major, minor, patch left to right, and a
   pre-release suffix (`1.0.0-beta.3`) sorts below the same version without one (`1.0.0`).
   - Equal: the bundle describes the plugin exactly. Use it.
   - Site newer than `verifiedUpTo`: the bundle may lack settings. Read the element live with
     `bricks/get-element-schema` and tell the user the skills can be updated (`bfbe-update`).
   - Site older: the bundle may name a setting the site does not have yet. Use the bundle, but if a write seems
     ignored, read the element live.
2. **Find the element.** In `index.json`, `elements[]` has `name`, `label`, `pack` (`free` or `pro`), `nestable`,
   `parent` (set for a child element), `skill` (the skill that covers it) and `schemaPath`. `features[]` lists the
   four features the same way. Read the file at `schemaPath`.
3. **Element not in the index.** It is not a BFB element (check Bricks' own skills), or the pack is newer than the
   bundle (step 1). Say which; do not invent a schema.

## A schema file

```
name, label, pack, skill, docs          what it is and where its skill and documentation are
nestable, children, childrenDefault     typed children by element name, and the tree the builder inserts
parent                                  for a child element: the element it lives in
cost                                    CSS and JS gzipped, dependencies, from the measured cost manifest
controlGroups                           group key -> { title, tab, required? }
controls                                control key -> the control as registered
```

Each control is the array the plugin registers, which is what the builder panel draws from:

- `type`: `select`, `checkbox`, `text`, `number`, `color`, `typography`, `border`, `dimensions`, `repeater`,
  `icon`, `image`, `file`, `info`, `separator`, and the rest of Bricks' control types. `separator` and `info` store
  nothing.
- `label`, `description`, `placeholder`: the panel's words. A select's `placeholder` names the option the element
  reads when nothing is stored, its effective default.
- `options`: for a select, the stored values are the **keys**, the labels are the values.
- `default`: a stored default where the plugin declares one (rare; most defaults are the placeholder's option).
- `required`: the condition the panel shows the control under, `[key, operator, value]` or a list of such clauses
  (all must hold). Operators are `=` and `!=`; the value may be a list (any of). `value` `""` with `!=` means "is
  set". **The engine applies the same condition before rendering and drops a value whose condition is unmet**, so a
  write must satisfy it.
- `css`: the control writes CSS; each entry names a `property` and, often, a `selector` under the element's root,
  which also tells you which part of the DOM a control styles.
- `hasDynamicData`: a `{dynamic_tag}` is accepted.
- `units`, `min`, `max`, `step`, `inline`, `small`, `tab`, `group`, `rerender`: as in Bricks.

A control key may be written with a breakpoint or pseudo-class suffix exactly as on any Bricks element
(`width:tablet_portrait`, `color:hover`).

## Never do

- Use the bundle without the version check: a stale shape fails silently.
- Treat a per-element SKILL.md as the schema: it names the settings that decide a build; the schema file has them all.
- Write a value the `required` condition does not admit, or guess an option value: the keys of `options` are the only
  stored values.
- Edit anything under `references/`: the plugin's `dev/skills-export.php` writes it on every release, and the
  release refuses a bundle that does not equal the registered controls.
