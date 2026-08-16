# MMud+ Changelog

Plugin era (MegaMMUD 2.1): full notes live on each
[release page](https://github.com/AyaTheHusker/MMud-Plus/releases).

## 1.009 — 2026-08-16
- Drag mode: explicit LOOP CFG checkbox with a per-room delay that actually
  paces every room of the loop (armed on arrival from every position source;
  fight commits and bails can no longer wipe it) — set it near your lairs'
  regen and dead laps disappear. The mob-arrival settle hold is behind the
  same checkbox; plain walk-to paths never pace.
- Split-spawn lairs (stitched zombies etc.): step decisions wait for a roster
  parsed after the last kill, so a generation dying can't slip the room latch
  before its spawns appear. Must-kill rooms stay latched through the split tree.
- Teleport / text-command exits (go path, NPC asks) no longer stall the walker;
  "Fight in lairs only" is honored by the instant-of-arrival verdict; phantom
  cross-room fight commits (old room's pile peak marrying the next room's
  roster) eliminated.
- Settings that stick: every LOOP CFG edit saves instantly, sub-window close and
  shutdown save, manual SAVE button on the mapwalker bar; the profile-reload
  revert ghost is fixed at the root.
- SEARCH_GET stops when the pack can't fit one more of the item (weight vs live
  encumbrance) instead of retrying into "You cannot carry that much!";
  an already-satisfied SEARCH_GET_REQUIRED still passes instantly.
- STOP/pause, CLEAR and New/Cancel now abort a running smart-command chain.
- QoL: round timer counts tenths below 2s on a steady bar; the loop recorder
  header shows the saved loop's name; rest thresholds re-read your Health
  settings the moment Save Character writes them.

## 1.008 — 2026-08-14
- Walker safety hardening: wall bumps = instant freeze + re-verify + replan,
  with a permanent `wallbumps.log` record; hazard-exit and duplicate-move
  vetoes on every direction send (Black Moat class eliminated).
- Puzzle mazes: complete lever tours in MDB order (destination gate modeled
  first, shared levers deduped); gated directions fire only when the server
  lists the exit open; no lever re-pulls.
- Single room display per step incl. meditating walks (glued prompt+cluster
  consumed); idle combat toggle never touched; debug logging persists;
  step cap 1500.

## 1.007 — 2026-08-14
- The walker's per-step room query (`Location:` / `Regen Time:` / `Room Illu:`
  lines) is hidden from the terminal again — a 1.006-era regression let it spam
  every step. While pathing, every such cluster is consumed; your own hand-typed
  `rm` always shows.
- Step commands restored to the proven single-queue routing (direction →
  after-step commands → room query, one ordered channel) — the configuration
  that ran clean for days. No wall-bumps: RM `Location:` data is the only
  position truth, never room-identity guessing.
- Diagnostic logging for the room-line hider (debug menu) so any future report
  names its own cause.

## 1.006 — 2026-08-14
- Critical pathing fix: step bursts travel one ordered channel so the walker can
  never fire a direction from the wrong room; mana-rest disabled now means mana
  appears nowhere in rest decisions.

## 1.005 — 2026-08-14
- Dynpath faster than legacy pathing; single room display per step; clickable
  splash; hourly update checks; party `@wait`/`@ok`; MadWiz shift-drag copy.

## 1.004 — 2026-08-13
- Walker reliability (confusion/fear fumble push-through, post-fight stall fix,
  exact exp meter, sneak button untouched) + party `@wait`.

## 1.003 — 2026-08-11
- Resting-safety fix (meditate-before-rest no longer skips resting HP) +
  Windows XP–11 compatibility.

## 1.002 — 2026-08-11
- Loads on Windows XP–11 (compatibility fix).

---

Overlay era (MegaMMUD 2.0.5, final: 1.15):

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
