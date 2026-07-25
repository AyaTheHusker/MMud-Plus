# MMud+

**MMud+** is a closed-source enhancement overlay for MegaMUD — a proxy + plugin
suite that adds a modern in-game experience without modifying the MegaMUD client
itself. It layers on top of an existing MegaMUD install and can be removed at any
time by deleting the files it adds.

> MMud+ is **not** MegaMUD and is not affiliated with or endorsed by the makers
> of MegaMUD or MajorMUD. You must already own and install MegaMUD separately.
> MMud+ only adds files alongside it.

## What it adds

- **Realmwalker+** — a live, zoomable GPU map walker with pathfinding, loops,
  and destination captures
- **Convo+** — a rich chat window with inline emoji, media, and multi-channel
  support
- **MadWiz** — an in-game oracle: reads your character live and answers sims,
  gear rankings, spell picks, drop/lair lookups, and more, plus built-in
  HD-ANSI door games (autobattler, trivia, ANSI Annihilation)
- Quality-of-life overlays: backscroll, loop recorder, party window, and more

## Install

1. Install MegaMUD normally (you provide your own copy).
2. Download the latest `MMud+ Vx.xx.zip` from the [Releases](../../releases) page.
3. Extract its contents **into your `C:\MegaMUD` folder** (it overlays — it adds
   MMud+ files and touches none of MegaMUD's own).
4. Launch MegaMUD as usual. Press **F11** in-game for the overlay.

To uninstall, delete the files the zip added (chiefly `msimg32.dll`, the
`plugins\` additions, and `rodentia.exe`).

## Releases

Builds only. See [Releases](../../releases) for each version + its changelog.
This repository contains **no source code** — MMud+ is closed source.

## License

Proprietary. All rights reserved. See [LICENSE](LICENSE). You may download and
use MMud+ for personal play; you may not decompile, modify, or redistribute it.
