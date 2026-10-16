# Changelog

Each release of this pack names the BFB Elements version it was exported from and checked against
(`verifiedUpTo` in `skills/bfbe-schemas/references/index.json`). Skills and plugins are released
together; a pack never describes a plugin that has not shipped.

## 0.5.0, 2026-10-16

Verified up to BFB Elements 1.3.0 and BFB Elements Pro 1.3.0. A minor version: two new skills, and three element
skills for their 1.3 abilities.

- New skills: `bfbe-page-loader` (Pro template type: a screen built from elements, shown over the page while it is
  drawn, wherever its Conditions say; the template is made in Bricks, since `bricks/create-template` does not take
  the type) and `bfbe-breakpoint-canvas` (Pro builder tool: every breakpoint side by side in the builder, its
  defaults in the option `bfbe_breakpoint_canvas`).
- `bfbe-snap-slider`: Direction (Across or Down) per breakpoint, the window's Height, what acts across only, a
  slider nested in a Down slide, the keys; a pattern from the Down fixture.
- `bfbe-charts`: a CSV address on another site, fetched by the site's server and kept an hour, the last good copy
  for up to a week; never from the visitor's link.
- `bfbe-hotspots`: each pin's Left and Top take dynamic data, so in a query loop every post places its own pins; a
  pattern with ACF fields. In a query loop: yes.
- `bfbe-start-here` names all ten features (nine Pro, one free).
- Source references in the written sections follow the 1.3 code.

## 0.4.0, 2026-10-14

Verified up to BFB Elements 1.2.0 and BFB Elements Pro 1.2.0. A minor version: two new skills.

- New skills: `bfbe-background-masks-and-patterns` (Pro feature: a shape and a pattern over the background of Bricks'
  Section, Container, Block and Div) and `bfbe-footer-reveal` (Pro feature: the footer template's reveal, with the
  page's own switch).
- `bfbe-start-here` names all eight features; the README lists the seven Pro ones.

## 0.3.1, 2026-10-13

Verified up to BFB Elements 1.1.2 and BFB Elements Pro 1.1.2. A patch: the Gotchas that described 1.1.1's faults now
describe 1.1.2, and the rules that guarded them are gone.

- `bfbe-toast`: a Display set on the toast no longer leaves the closed card in the way; a toast shown over an open modal
  dialog is lifted into it and can be closed there; BFB Dark Mode leaves it a light card; closing it from the keyboard
  sends the focus back. Its size is 0.97 KB CSS and 2.19 KB JS. Two rules removed (`_display`, a text colour under Dark
  Mode).
- `bfbe-tooltips`: a tooltip on an element inside a link or a button (a linked Icon) is reached through the link, with one
  tab stop; when it closes is said as it is (the pointer leaving unless the focus is on it, or the focus leaving). The
  rule against a linked Icon is removed.
- `bfbe-image-focal-point`: any element's own position for its pictures wins over the point (BFB Devices' Media position
  included), and the dot has a slider's values and says both directions.
- `bfbe-devices` and `bfbe-dark-mode`: a line each on the focal point and on the toast.

## 0.3.0, 2026-10-13

Verified up to BFB Elements 1.1.1 and BFB Elements Pro 1.1.1. A minor version: four new skills.

- New skills: `bfbe-blockquote` (free element), `bfbe-toast` (Pro element), `bfbe-tooltips` (Pro feature, on every element)
  and `bfbe-image-focal-point` (the free plugin's feature, set in the media library).
- Every element's schema and skill now lists the Tooltip group (`bfbeTooltip*`), which Pro 1.1 adds to every element,
  beside Hover Effects and Advanced Header Scroll.
- Each skill's **Requires** line names the version its element or feature first needs: 1.0.0 for everything 1.0 shipped,
  1.1.0 for Blockquote and Image focal point, Pro 1.1.1 for Toast and Tooltips (their keyboard and timing guarantees came
  with 1.1.1's fixes).

## 0.2.0, 2026-10-12

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
