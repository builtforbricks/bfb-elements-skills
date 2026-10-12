# Changelog

Each release of this pack names the BFB Elements version it was exported from and checked against
(`verifiedUpTo` in `skills/bfbe-schemas/references/index.json`). Skills and plugins are released
together; a pack never describes a plugin that has not shipped.

## 0.2.0, release date: with BFB Elements 1.0.0

Verified up to BFB Elements 1.0.0, the first stable release. A minor version, not a patch: one attribute an agent may read
was renamed.

- Interactive Cursor's hover selector attribute is `data-bfbe-cursor-hover` (it was `data-bfbe-hover`, Hover Effects'
  attribute); on the site the cursor lives in the browser's top layer, so a hiding or blurred header no longer shrinks it.
- Schemas exported from BFB Elements 1.0.0: Comparison Table's plan button Background says what it takes unset; Age Gate's
  Buttons sit, Price List's highlighted row, Social Share's Hover text colour and Advanced Text Reveal's Colour write where
  their fixes need them.
- Gotchas rewritten where 1.0.0 fixed what they described, and the rules that guarded them removed: Modal's click outside
  on a drag, Content Timeline's Flows set to Across, Marquee's Blocks, Age Gate's Buttons sit and clipped shadow, Price
  List's key order, Comparison Table's empty dynamic values, Social Share's brand words, Flip Box in a linked block, the
  Cursor's emptied numbers and hiding headers, and Advanced Text Reveal's Lines, unset Colour, sweep and Count.

## 0.1.1, 2026-10-12

Verified up to BFB Elements 1.0.0-beta.4, the fixes from the last check before launch.

- Schemas exported from BFB Elements 1.0.0-beta.4: Devices hides Frame colour and Bezel for the browser window, a new
  Image Accordion's starter panels carry white text, and the Quote PDF's Title says which alphabets the PDF draws.
- Gotchas rewritten where beta.4 fixed what they described: a Marquee copy's links work, Contact Button keeps messaging
  apps' links, Form Steps' step conditions work with Form Fields off, Add to Calendar reads dates of numbers in the site's
  date order, Flip Box names an icon-only trigger, a vertical Before / After lets the page pan sideways, Form Fields'
  Chosen and Hover styles win over the card's own, Advanced Text Reveal plays on page load with Play once off, and Dark
  Mode leaves a dark system to the site where the page is not painted.
- Two new gotchas for BFB Advanced Forms: a login's `redirect_to` stays on the site, and the quote PDF's alphabets.

## 0.1.0, 2026-10-08

Verified up to BFB Elements 1.0.0-beta.3, the testers' build.

- First pack: `bfbe-start-here`, `bfbe-schemas` with every element's schema, `bfbe-update`, and one skill per
  element and feature. Exported from BFB Elements 1.0.0-beta.3.
