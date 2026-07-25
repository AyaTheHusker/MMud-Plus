# MMud+ Changelog

## V1.02

MadWiz
- **MadWiz on the GL renderer** — the in-game MadWiz window now runs on the same
  OpenGL overlay path as the other windows (crisp glyphs, smooth animations, the
  animated MAD WIZARD / GAMES logos, and twemoji icons all render in-game).
- **Live character prelude** — MadWiz reads your character automatically on open
  (and on right-click Refresh, or Load Wiz File), including your actual
  spellbook via `spells` / `powers`, so "sim me vs X" fights as the real you.
- **True sims** — sims use your HP, AC, MR, stats, weapon, and spellbook, and
  commit to your strongest action (never mixing round to round); spells are
  gated by your level and what you actually know.
- **Remote asks** (`@?`) never use anyone's character — a "level 47 witchunter"
  question builds a blank level-47 witchunter.
- **Gear rankings** honor the asked class, level, and alignment, and no longer
  suggest magical weapons to Witchhunters or over-level gear.
- **WIZQUIZ+** — redesigned full-screen trivia (centered panel, fade-in answers,
  smooth transitions); questions only cover obtainable items.
- Emoji spacing fixed (no more overlapping glyphs); wizard prompt typing fixed.

Games
- **Rats To Runics Autobattler (Alpha)** and **RODENTIA (Experimental)** in the
  HD-ANSI Door Games menu.
- Groundwork for networked **ANSI Annihilation** (multiplayer over MUD chat).

Overlays
- Fixes to overlay click/drag handling so windows stop stealing clicks meant for
  the map underneath.
