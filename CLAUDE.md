# CLAUDE.md

See **[AGENTS.md](AGENTS.md)** — it is the shared source of truth for every
assistant on this project, and is deliberately not duplicated here.

Two things worth repeating because getting them wrong is expensive:

- **Assert `window.innerWidth` after every resize and every navigation** before
  trusting any measurement. `devicePixelRatio` is unstable here and wrong-width
  numbers look entirely plausible.
- **`work-page/` is the real portfolio; `replica/` deliberately contains no real
  content.** Do not move material between them.
