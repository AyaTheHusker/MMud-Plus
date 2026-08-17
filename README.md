## MMud+ for MegaMMUD 2.1 — official plugin (current)

**MMud+ now ships as an official MegaMMUD 2.1 plugin** — one file,
`Plugins\MMudPlus\MMudPlus.dll`, loaded through MegaMMUD's own plugin API.
Thanks to Syntax for adding the official plugin ABI: the old system was a
reverse-engineered overlay that had to be rebuilt against every MegaMMUD
update; the plugin integrates naturally and survives host updates.

**Latest: [MMud+ 1.010](https://github.com/AyaTheHusker/MMud-Plus/releases/latest)** —
extract the zip into your MegaMUD folder and launch. Each release page carries
its full changelog, and the plugin checks for updates on its own (hourly + at
launch).

**Still on MegaMMUD 2.0.5?** The final overlay-era build is
**[MMud+ 1.15](https://github.com/AyaTheHusker/MMud-Plus/releases/tag/v1.15)** —
it fixes bugs serious enough that you should not run anything older (including
cases where a character could sit defenseless while resting on a dynamic loop).
The 2.0.5 line receives no further features.

---

# MMud+

**MMud+ is a modular in-game suite for MegaMMUD by Syntax** — an official
plugin that adds a modern in-game experience without modifying the
MegaMUD client itself. It layers on top of an existing MegaMUD install and can be
removed at any time by deleting the files it adds.

> MMud+ is **not** MegaMUD and is not affiliated with or endorsed by the makers
> of MegaMUD or MajorMUD. You must already own and install MegaMUD separately.
> MMud+ only adds files alongside it.

## What it adds

- **BFS-driven smart pathing** — full world-graph pathfinding: click a room and
  it figures out how to get there (doors, keys, hazards, boats and all)
- **Instant loop creation** — lasso a set of rooms and go; the loop builds itself
- **Event chain system** — timed detours and command bursts for smart boss
  farming (boss activations, key turns, multi-leg circuits)
- **Destination captures** — records exactly what happened at each boss room so
  you can check what you got, straight from the overlay
- **Realmwalker+** — a live, zoomable GPU map walker with animated loop tiles,
  combat FX, pathfinding and a full loop/config editor
- **Convo+** — a rich conversations window that mirrors every chat line 1:1 with
  channel colors, inline emoji and media
- **MadWiz** — an in-game oracle: reads your character live and answers sims,
  gear rankings, spell picks, drop/lair lookups, and more, plus built-in
  HD-ANSI door games (autobattler, trivia, ANSI Annihilation)
- **Android connectivity** (in development) — control your mega from your phone
  via a local relay server
- Quality-of-life overlays: backscroll, loop recorder, party window, and more

![Realmwalker+ map](screens/realmwalker_map.png)

![Event chain editor](screens/event_chains.png)

## Install

1. Install MegaMMUD 2.1 normally (you provide your own copy).
2. Download the latest `MMudPlus-X.XXX.zip` from the [Releases](../../releases)
   page.
3. Extract it **into your MegaMUD folder** (the one with `megamud.exe`). It
   drops `Plugins\MMudPlus\MMudPlus.dll` in the right place and touches none
   of MegaMUD's own files.
4. Launch MegaMUD as usual — the plugin loads itself. Updating from any earlier
   version works the same way (or let the in-app updater fetch it).

To uninstall, delete the `Plugins\MMudPlus\` folder.

## Releases

Builds only. See [Releases](../../releases) for each version + its changelog.
This repository contains **no source code** — MMud+ ships as builds only. The
auto-generated "Source code" links on each release are just this readme.

## License

Free to use, modify, and share. See [LICENSE](LICENSE). The only ask: don't pass
MMud+ (or a version based on it) off as your own — keep credit to the original
author. Provided as-is, no warranty.
