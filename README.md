# BFB Elements skills

Agent skills for [BFB Elements](https://builtforbricks.com/bfb-elements/), the Bricks Builder element pack by
Built for Bricks: one skill per element and feature, the control schemas the plugin's release exports, and
examples the release checks against the plugin before they are published.

**Status: complete, awaiting its first release.** Every skill is written in full and checked against the plugins; the
first release goes out with BFB Elements 1.0.0-beta.3, and until then the schemas describe 1.0.0-beta.2 (the
`verifiedUpTo` in `references/index.json`).

## What a skill is

A folder with a `SKILL.md`: a short front matter (`name`, `description`) and Markdown an AI client loads when the
task matches. It does not talk to the site; the Bricks MCP connection does (Bricks 2.4+, through the WordPress MCP
Adapter, set up under **Bricks > AI**). The skill tells the client what the live schema cannot: which children an
element needs, which settings only act together, what the rendered DOM looks like, what fails silently, and what
never to do.

## Requirements

- BFB Elements 1.0.0-beta.3 or later (the free plugin), and BFB Elements Pro for the Pro elements.
- Bricks 2.4 or later with its abilities enabled, for an AI client that edits the site. Without it the skills
  still help a client that writes Bricks JSON for import.
- A client that loads skills: Claude Code, Codex, Cursor, GitHub Copilot, or any client that reads `SKILL.md`
  folders.

## Install

Copy the prompt from **BFB Elements > Dashboard > AI skills** in WordPress into your client, or do it by hand.

**Claude Code, as a plugin** (updates with `/plugin marketplace update bfb-elements-skills`):

```
/plugin marketplace add builtforbricks/bfb-elements-skills
/plugin install bfb-elements@bfb-elements-skills
```

**Claude Code, Codex, Cursor and others, as a checkout** (one checkout, symlinked, so an upgrade moves every skill):

```sh
git clone https://github.com/builtforbricks/bfb-elements-skills.git ~/.bfb-elements/skills/bfb-elements-skills
~/.bfb-elements/skills/bfb-elements-skills/scripts/bfbe-skills-upgrade   # pins the checkout to the latest release

# Pick the directory your client scans:
SKILLS_DIR="$HOME/.claude/skills"      # Claude Code, every project    (a project alone: .claude/skills)
# SKILLS_DIR="$HOME/.agents/skills"    # Codex and other agents         (Codex alone: ~/.codex/skills)
# SKILLS_DIR=".cursor/skills"          # Cursor, this project

mkdir -p "$SKILLS_DIR"
for skill in "$HOME"/.bfb-elements/skills/bfb-elements-skills/skills/bfbe-*; do
  ln -sfn "$skill" "$SKILLS_DIR/$(basename "$skill")"
done
```

Then start a new chat and ask: *List the loaded skills whose names start with `bfbe-`.*

## What is included

| Skill | Covers |
|---|---|
| `bfbe-start-here` | Load first: names and discovery, the rules of the engine (a hidden setting is dropped; defaults are the panel's; an element missing from the registry is turned off, not absent), workflow, never do |
| `bfbe-schemas` | Every element's controls as the plugin registers them, `references/elements/<name>.json`, with the version check against the site |
| `bfbe-update` | Compares the pack with the plugin on the site; updates on request |
| `bfbe-<element>` | One per element: what it is and is not for, cost, structure and typed children, the settings that decide a build, wiring, verified patterns, gotchas, never do, the accessibility it guarantees. Child elements (table rows and cells, slides, timeline moments, showcase steps and cards, filter items, player controls, the form's fields) ride in their parent's skill |
| `bfbe-form` | BFB Advanced Forms with its twelve parts, steps, rules, formulas, uploads, signatures, the total, payments |
| `bfbe-hover-effects`, `bfbe-advanced-header-scroll`, `bfbe-form-steps`, `bfbe-form-fields` | The four features, which add controls to other elements rather than being elements |

## How it is made, and why that matters

- The schema files and the generated block of every skill are written by the plugin's release from the plugins as
  built (`dev/skills-export.php` in the plugin repository). `verifiedUpTo` in `references/index.json` is the plugin
  version they came from, never typed.
- Before a release, a check holds the pack against the plugin: every schema equals the registered controls, every
  example tree names registered elements and known keys, sets nothing the panel would hide, and renders with
  output and no notice. A pack that fails is not released.
- The plugin and the pack are released together, the same day, the same version line. `scripts/bfbe-skills-upgrade`
  pins a checkout to the latest release; `--check` only reports.

## Updating

Ask your client to "check for BFB Elements skills updates" (the `bfbe-update` skill), or run
`~/.bfb-elements/skills/bfb-elements-skills/scripts/bfbe-skills-upgrade`. Start a new chat afterwards: most clients
load skills once, at the start of a session.

## Licence

GPL-2.0-or-later, the plugin's. Built for Bricks, https://builtforbricks.com.
