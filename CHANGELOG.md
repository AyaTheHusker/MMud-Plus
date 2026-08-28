# MMud+ Changelog

Plugin era (MegaMMUD 2.1): full notes live on each
[release page](https://github.com/AyaTheHusker/MMud-Plus/releases).

## 1.018 — 2026-08-27
- Use High Mana Limit (Loop CFG, under Min monsters): a second, usually
  lower Min-monsters threshold that applies while ABSOLUTE current mana
  is at/above a configured amount — burn surplus mana on smaller piles
  instead of capping out; below the amount the normal limit applies.
  Either/or, live-evaluated; latched rooms stay latched; limit 0 = off.
- Includes the 1.017 same-day refresh: roster-gated steps (standing
  piles latch in place) + dual-count mid-move arm.

## 1.017 — 2026-08-27
- Piles latch at the Min-monsters threshold at last: followers land 1-2s
  after each step, so the threshold only ever crossed with a move in
  flight and the commit could structurally never fire mid-drag. The
  commit now follows the pile — the arrival room latches before the next
  step, and the pile pours into an already-committed fight.
- Committed fight rooms engage in under a second: the force-combat
  failsafe was a silent no-op in the plugin build (rooms wedged passive
  ~15s / 4-5 rounds until a breaker bailed them). Real API engage now.
- Idle is truly silent: the legacy render-checksum room watcher (rm
  ping-pong / prompt flicker while idle near floor loot) is retired in
  the plugin build.
- Log-flood guards on the failsafe and pickup-hold paths.

## 1.016 — 2026-08-27
- Dynpath destination arrivals actively engage combat (the old idle-safe
  restore was a silent no-op in the plugin build — you sat passive while
  mobs swung). Event chains/loops keep their own arrival combat config;
  a deliberate toolbar combat-off is always obeyed.
- Doors can no longer strand the walker: both move-cancel paths (door
  re-close rewind, "The door is closed!") clear the anti-double-move
  guard, so the post-open retry actually goes out. Door retries beat at
  600ms with an 8-try cap (the 1.015 hotfix, included).
- Loot notices captured mid-step resolve to the room they were SEEN in
  (age discriminator) — no more grabs firing in the wrong room while
  the real coins/items get walked past. No parting AoE at below-min
  piles after a finished rest.
- Committed fights are unanimous across every verdict, safety net, and
  step decision; the below-rest safety runs per-tick (engages
  mid-knockdown) with raw-count fallback; the plugin's own combat-lease
  writes can no longer be misread as user clicks (which disabled all
  safeties for a run).

## 1.015 — 2026-08-25
- Latch if HELD (Loop CFG): knocked down/entangled with enemies present =
  the room latches as a committed fight and MegaMUD engages while you're
  down; exit follows Finish-off (checked = clear the room, unchecked = kite
  stragglers after the hold breaks). One mob is enough; Min monsters never
  gates it.
- Every hold type recognized from MegaMUD's own MESSAGES.md (knockdown,
  entangle, web, chain, constriction, fear, freeze, manacles, ...): onset
  parks the walker (no refused moves), the release line resumes it
  instantly; the game's held flag strobes and is no longer trusted alone.
- Below-rest safety watches every tick (engages mid-hold), commits like a
  real latch, and can't be vetoed by count flickers or stale skip leases;
  committed rooms can no longer be stepped out of / un-latched / refused an
  engage while anything is alive. No parting AoE at below-min piles after a
  finished rest.
- Everything from 1.014 (internal, never published): overlay drag z-order +
  KDE keep-above fix, secret doors without pause, spore fumbles retried
  instantly, verified teleport retries, lair regen tooltips in minutes,
  kiting re-blesses like stock.

## 1.014 — internal build (see 1.015)

## 1.013 — 2026-08-19
- Everything from 1.012 (which was published and WITHDRAWN the same day — do
  not run it): stragglers engaged within seconds, buff re-casts never read as
  combat toggles, mid-step drop notices resolve and grab before the next move,
  in-fight position re-confirm, KDE keep-above fix.
- Stability: fixed the rare client freeze 1.012 shipped (render-thread
  cross-thread SetWindowPos deadlock in the new keep-above cleanup — now
  posted async); engagement pumping bounded to 3 per room.

## 1.012 — 2026-08-19 (WITHDRAWN — freeze; use 1.013)

## 1.011 — 2026-08-17
- Pile counts settle before every step again: 1.010's Drag-mode checkbox
  accidentally gated the mob-arrival settle hold, letting steps fire before
  walk-ins were counted (a 5-pile read 4 and never latched); the hold now
  applies on every min-monsters loop, and its enforcement gate matches.
- The skip-stall breaker re-verifies position (rm + movement hold) before its
  released step — a live escape had fired a direction the room didn't list,
  six rooms off the believed position.

## 1.010 — 2026-08-17
- Fast Lair Protection: LOOP CFG checkbox + seconds threshold — lairs
  regenerating faster than it are flee-class (never fight, never rest, sprint
  through and drag), with a flashing SKIP overlay on the map while a walk is
  live. Regen source corrected to the room's true Delay field and verified
  against live respawn timings; flee-class wins over must-kill and can't be
  re-fought by stale latches.
- SEARCH_GET rework: pack-aware batched gets ("get N item"), only gets what
  the search actually revealed, QUANTITY ALL fills to capacity, retries bound
  searches (default 10), stash-dry and server-refused stops; _REQUIRED bails
  event chains home or parks a dynloop idle when unsatisfiable.
- Committed-room fixes (live-log finds): previous-room slot counts can no
  longer phantom-commit a small room after a fast arrival; casting a
  song/spell mid-fight no longer reads as a manual combat toggle (the latched
  fight re-engages after the cast dip). "Finish off lairs" renamed "Finish
  off rooms" — it always applied to any latched room.
- MadWiz: natural gear queries with level override and class-wearability
  gates, compare-first dispatch, blur-AC recognized/displayed at your live
  encumbrance, deterministic level-range queries.

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




