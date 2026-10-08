---
name: bfbe-update
description: "Use when the user asks to check for or install BFB Elements skills updates, or when bfbe-schemas finds the site's plugin newer than the bundle. Compares the pack's verifiedUpTo with the plugin version on the site and, only on request, moves the checkout to the latest release."
allowed-tools: Bash, Read
---

# BFB Elements: check for skills updates

Prerequisite: the skills were installed from `https://github.com/builtforbricks/bfb-elements-skills` (a git checkout,
by default at `~/.bfb-elements/skills/bfb-elements-skills`, with each skill folder symlinked into the client's skills
directory).

## What it does

Says whether this pack describes the plugin on the connected site, and, when asked, updates the pack. The plugin and
the pack are released together, so a mismatch means one of them moved and the other did not.

## Steps

1. **The pack's version.** Read `verifiedUpTo` in `../bfbe-schemas/references/index.json`. Ignore `version` (the
   pack's own number) and `VERSION` at the repository root for this comparison.
2. **The site's version.** Call `bricks/get-system-information` and read `version` of the `plugins` entry named
   "BFB Elements for Bricks Builder" (or "BFB Elements Pro"). With no site connection, say one is needed to compare
   and offer the pack-side check alone (step 4).
3. **Compare as versions.** Major, minor, patch left to right; a pre-release suffix sorts below the release.
   - Equal: current; say so, nothing to do.
   - Site newer: the pack is behind and may lack settings; recommend the update and wait for the word.
   - Site older: the pack is ahead; usually harmless, and it explains a setting the site ignores.
4. **The latest release**, without changing anything: `scripts/bfbe-skills-upgrade --check` from the repository root
   prints `BFBE_SKILLS_INSTALLED`, `BFBE_SKILLS_LATEST` and either `BFBE_SKILLS_ALREADY_CURRENT` or
   `BFBE_SKILLS_UPDATE_AVAILABLE <old> <new>`.

## Updating, only when the user asks

- `scripts/bfbe-skills-upgrade` moves the checkout to the latest release tag (prints `BFBE_SKILLS_UPDATED <old> <new>
  <tag>`), stashing local changes first and saying so. `scripts/bfbe-skills-upgrade <tag>` moves to a named tag.
- If the checkout does not exist, clone it as the README says, then link the skills.
- The symlinks keep pointing at the same folders, so nothing else moves. **Start a new chat or session** afterwards:
  most clients load skills once, at start.

## Never do

- Update without being asked. Report the mismatch and let the user decide.
- Treat a mismatch as blocking: read the element live (`bricks/get-element-schema`) and carry on, saying so.
- Edit files under the checkout to "fix" a mismatch: the plugin's release writes them.
