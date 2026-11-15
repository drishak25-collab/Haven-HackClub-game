# Trashlight — Hack Club game

The complete Godot 4.5.1 project is in **[Trashlight-Public-Source.zip](Trashlight-Public-Source.zip)**. Download and extract it, then import the extracted `project.godot` in Godot. The archive includes all scripts, scenes, levels, sprites, audio, and third-party licenses.

# Trashlight

![Trashlight title](screenshots/Trashlight-title.png)

**Made with Godot 4.5.1 · Keyboard controls · Easy and Hard modes**

A 2D industrial platformer built with Godot 4.5.1. Cross The Drain, The Scrapyard, The Smokestack and Flood Shaft, collecting a power cell in each area, then face the Foreman. Original code and effects were made with Codex assistance. Downloaded artwork and fonts are credited in CREDITS.md.

## Play

Play the web build on the itch.io release page, or download the Mac build when available. Open Trashlight.app for the Mac release. Select Easy or Hard, then New Shift. Continue resumes the final-boss checkpoint if reached; otherwise it starts a fresh adventure. Boss Practice runs the final fight independently of campaign saves.

- A/D or arrows: move.
- Space/W/Up: jump. Hold for height, release for a short hop.
- Shift/C: dash, briefly passing through attacks. Cooldown applies.
- X/E: lantern pulse, revealing ghost platforms, stunning enemies, clearing nearby spikes and hitting an exposed boss fuse.
- Escape/P: pause. M toggles sound in the boss arena.

## Death and the only checkpoint

Losing all hearts before reaching the final boss restarts the entire adventure at level one. All scrap, power cells and collected items are cleared. Falling into a pit or the rising sludge also ends the run immediately, even with hearts remaining. Ordinary nonfatal hits still cost a heart.

Lamps are decoration only: they no longer heal, save or move the respawn point. There are no level, lamp or Flood Shaft recovery checkpoints. Quitting/returning to title before the boss does not create a mid-run checkpoint; Continue starts at the beginning.

Reaching the Foreman is the only checkpoint. Once reached, death retries the final fight without replaying the adventure. Every boss retry starts at its first phase with all fuses restored, in both difficulties. There are no checkpoints between boss phases. This checkpoint persists across app restarts. Old intermediate adventure saves resume at level one; old boss-arrival saves still resume the boss from its beginning.

## Hazards and difficulty

The original three stages have tall, timed steam geysers, enemies and orange bombers that mark explosion zones. Five scrap pickups restore one heart. X reveals ghost platforms temporarily. Flood Shaft has an accelerating rising flood, requiring continuous climbing.

Easy keeps the previous adventure balance and five boss hearts. Hard has faster enemies and projectiles, shorter warnings, larger/more frequent bomber blasts, shorter ghost-platform duration, longer dash cooldown and three boss hearts. Its flood rises at 80–98 pixels/second, versus Easy's 50–63.

## The Foreman

Dodge straight, full-height orbital strikes, dense animated steel-spike rain, blackout combinations and reactor explosions. After an attack cycle, jump near the exposed gold fuse and press X. Destroy three fuses, then climb the emergency stairs and pulse the red shutoff. The boss HUD is limited to small bottom readouts. Neither difficulty has a mid-fight checkpoint.

## Edit in Godot

Import project.godot and press F5 to play. The levels, menus, enemies, platforms and collision shapes are real scene nodes editable with the 2D editor and Inspector.

- scenes/main.tscn: native Control menus and adventure HUD.
- levels/forest.tscn, village.tscn, beacon.tscn, sludge.tscn: adventure stages.
- levels/foreman.tscn: final boss arena and small status labels.
- scenes/orbital_laser.tscn: editable AnimatedSprite2D orbital strike.
- scenes/sprite_fx.tscn and art/fx/*.tres: frame animations for explosions, steam, smoke, impacts and beams.
- scripts/player.gd: movement, dash and adventure death handling.
- scripts/session.gd: run state and final-boss-only persistence.
- scripts/game.gd: menus, stage loading, run restart and boss entry.

The game uses individual PNG frames for its pixel effects. Warning markers remain separate from animated art and collisions. The night title illustration is original; Tales of Orbis was a visual reference for GUI style. No claim of human authorship is made.

## Checks and distribution

Run Godot with `--headless --path <project-folder> -- --death-test` to check full-run resets from every level, cleared collectibles, decorative lamps, fatal falls, save behavior and boss-only retries. `--route-test`, `--spike-test`, `--orbital-test`, `--sprite-test` and `--effects-test` cover their respective features. Checks restore the existing save file. Automated behavior checks are not a complete human difficulty playtest.

The Mac release bundles the official universal Godot executable and game pack. It is locally signed, not notarized for public distribution. To produce a smaller release, install Godot's export templates and use the included macOS preset. Nothing has been published or submitted to Hack Club.
