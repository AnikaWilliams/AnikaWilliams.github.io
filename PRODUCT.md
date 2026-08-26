# Anika Williams — portfolio

## What this is

Portfolio site for Anika Williams, an industrial and computational designer.
The work is material-led: folded sheet metal, auxetic structures, living hinges,
textile formwork, cast cement, wave-bent aluminium. Design IS the product here,
so the register is **brand**, not app UI.

## Who it's for

Design hiring managers and recruiters at industrial, product, and
design-engineering studios. They arrive from a link, scan the work grid for
30–60 seconds, and decide whether to open a project. The site's single job is
to survive that scan and make one project worth clicking.

## Current surface

`work-page/` — a faithful recreation of the work-index composition at
heinrichzaunschirm.com/work, built to measured specification.

## Constraint that overrides house style

The user's explicit brief: reproduce the reference composition **exactly** —
same type, colour, and grid — and do not restyle it into her own visual
language. This outranks generic anti-template guidance. Specifically, these are
deliberate and must not be "fixed":

- A uniform three-column grid of identically-sized tiles.
- A centred, symmetrical header band.
- A near-monochrome palette with no accent colour.

Craft rules still apply in full: contrast, semantics, focus states, reduced
motion, responsive behaviour, real alt text.

## Measured reference spec (at 1440px)

| Property | Value |
| --- | --- |
| Header band | 180px tall, `#F7F7F7`, full-bleed |
| Wordmark | 23px, weight 200, tracking 2.4px, uppercase, `#020202` |
| Nav | 15px, weight 200; `#727272` idle, `#020202` active |
| Grid | 3 columns; tiles 442 × 315 (ratio 1.403:1) |
| Spacing system | 30px gutter, row gap, and band-to-grid gap; 20px outer margin |
| Tile count | 12 |
| Typeface | `neue-haas-unica` (Adobe Fonts), Inter 200 substituted |
| Hover | veil fades in; title + category rise from +30px over 0.3s |

## Stack

Static HTML + vanilla CSS. No framework, no build step. Served locally with
`python -m http.server`.
