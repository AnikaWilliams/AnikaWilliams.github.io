# Working notes for AI tools

Read this before changing anything. It is the shared source of truth for every
assistant on this project — Claude Code, Codex/ChatGPT, Copilot, or a human.
`CLAUDE.md` points here rather than duplicating it, so there is one file to keep
current.

## What this repo holds

| Directory | What it is | Status |
| --- | --- | --- |
| `work-page/` | Anika's actual portfolio. Real content. | The deliverable |
| `replica/` | A measured reconstruction of another designer's site, built to study its layout system. Placeholder text and generated art only. | Reference exercise |
| `mock/` | An early abandoned build. | Safe to delete |

Never move content between `work-page/` and `replica/`. They exist for opposite
reasons: one carries real work, the other deliberately carries none.

## Running it

```bash
python -m http.server 5173 --directory work-page   # the portfolio
python -m http.server 5200 --directory replica     # the replica
```

No build step, no dependencies, no framework. `work-page/` ships zero
JavaScript except a small progressive-enhancement block on `project.html`;
keep it that way unless there is a reason that survives review.

## Conventions that are load-bearing

- **Geometry comes from measurement, not estimation.** Sizes and spacings in
  the CSS trace to numbers taken from a live page. Comments record the source.
  Change one and the comment stops being true — update both.
- **Placeholder art is generated, and must stay unique.** Duplicate tiles read
  as unfinished. The generators assert uniqueness and exit non-zero on a
  collision; do not remove that check.
- **Contrast is not decorative.** Several values sit at a deliberate floor with
  the ratio recorded in a comment. Lightening them silently breaks WCAG AA.
- **Accessibility fixes are intentional**, even where they diverge from the
  reference. `work-page/` favours the accessible choice; `replica/` favours
  fidelity. Do not "correct" one to match the other.

## Verification gotcha — read before measuring anything

`devicePixelRatio` is **not stable** in headless browsers here. Across one
session it was observed at 0.8, 1.0, 2.0 and 2.5, and it can differ per origin.
`setViewportSize(1440)` may yield `innerWidth` of 1800, 1440 or 917.

**Always assert `window.innerWidth` after every resize AND every navigation,
and abort if it is not the target.** Measurements taken at an unverified width
are worthless, and they look completely plausible. Several wrong conclusions in
this project's history came from exactly that.

Also: measure the *rendered ink*, not the element box. A centred box can hold an
off-centre graphic. Rasterise to canvas and scan pixels when position matters.

## Multi-tool protocol

1. **Commit before handing off.** Each tool should start from a clean tree.
   `git status` should be empty before another assistant begins.
2. **One tool per file at a time.** Two assistants editing the same file
   concurrently will clobber each other; there is no merge sense in either.
3. **Split by lane, not by line** — e.g. one on `replica/`, one on `work-page/`,
   or one on CSS and one on copy. Overlapping lanes cause silent conflicts.
4. **Branch for anything speculative**: `git switch -c try/<thing>`. Cheap to
   throw away, and it keeps `main` reviewable.
5. **Write findings here, not in chat.** Chat context does not survive to the
   next tool. This file does.

## Open items

- `work-page/` needs real photography; every image is generated placeholder art.
- No `og:image` exists anywhere — needs a real 1200x630 raster before sharing.
- `about.html` carries visible `.todo` placeholder rows for Education and
  Recognition. Fill or delete them before this is shown to anyone hiring.
- `neue-haas-unica` is first in the replica's font stack and never loads; it
  needs an Adobe Fonts kit or the stack should stop naming it.
