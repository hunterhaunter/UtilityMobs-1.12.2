# Changelog

## 3.2.0 (1.12.2)

Community-driven release: nearly all of the open issue tracker is addressed. Big thanks to
everyone who filed detailed reports and to **@MrKoteo** for the Russian translation.

### New

- **Walkable block golems** — new `golems.block_collision` config (off by default). When on,
  block golems (chest / furnace / crafting table / anvil / jukebox) become solid so you can
  stand on and walk across them, mirroring the existing `turrets.collision` toggle.
- **Russian translation (ru_ru)** — contributed by **@MrKoteo** (PR #3). The localization
  loader now injects the *active* language from the jar with English as an automatic
  per-key fallback, so any language file dropped in works and untranslated keys read in
  English rather than showing raw `entity.*` keys.

### Fixed

- **Golem arm-swing is smooth** (issue #1.3) — the biped golems (armor, gilded, bound soul,
  stone) now interpolate their weapon swing instead of snapping between frames. The swing
  tick was running before the base update that resets `prevSwingProgress`, killing the
  interpolation; it now ticks after, matching vanilla mob cadence.
- **Lang files are respected** (issue #2) — mod translations load through the resource layer,
  so resource packs and localization mods can override any `utilitymobs.*` string, and
  shipped locales (like Russian) load from the jar.
- **Steam golem fuel slot no longer shifts / dupes** (issue #4) — fuel stays in the slot you
  place it in; the mid-slot shove that could visually duplicate items is gone.
- **Turret ammo matches shots fired** — with `turrets.require_ammo` on, a turret now consumes
  exactly as many ammo items as projectiles it fires (a shotgun/volley burns 6, not 1).
- **Furnace golem smelting progress bar** animates correctly again.
- **Help "?" button toggle now covers turrets** (extends issue #1.7) — `general.show_help_button`
  now hides the turret GUI's help button too, not just the steam golem's.

### Already shipped earlier in the 3.x line (issue tracker coverage)

- Heal-number toggle (`general.heal_numbers`) — issue #1.1
- Snow golems respect the `mobGriefing` game rule — issue #1.2
- Per-material golem hurt/death sounds; snow golem uses the new vanilla sounds — issue #1.4
- Global attack blacklist moved to config + `/umblacklist` point-and-add command — issue #1.5
- Config option to hide the steam golem's "?" help button — issue #1.7
- `fenceWood` OreDictionary support when building golems — issue #1.8

### Still open

- **Optional Patchouli** (issue #1.6) — the guide book is still a hard dependency; making it a
  soft dep is a larger refactor and is deferred.

### Not in this release (moved to a feature branch)

- Smart logistics walking golems (Smart Upgrade item + config menu) and the turret-head
  pop-off / re-attach feature were pulled from this release for further work; they live on a
  local `feature/turret-head-smart-golems` branch.
