# Version 0.0.2 Docs

## Quick Diagnostic Read

v0.0.2 upgrades the public scaffold from metadata-only to a load-wired datapack scaffold for Minecraft Java Edition 26.1.2. It is still not a playable Silk Touch spawner release.

## One-Sentence Objective

Establish a correctly named, correctly formatted, reload-visible datapack foundation before adding the spawner loot and placement mechanics.

## Why This Version Matters

Minecraft datapacks are easiest to debug when the pack identity, namespace, and load hook are known-good before gameplay commands are added. This version proves the basic wiring: Minecraft can read the manifest, find the vanilla load tag, and call the Silk Spawners namespace entry point during `/reload`.

## What Changed

- `silk-spawners/pack.mcmeta` now targets data pack format `101.1` with matching minimum and maximum format values.
- The pack metadata now includes the public pack name and description.
- `data/minecraft/tags/function/load.json` registers the Silk Spawners load function with the vanilla load tag.
- `data/silk_spawners/function/load.mcfunction` provides a short visible probe for `/reload` checks.
- The root README now documents version `v0.0.2`, Minecraft Java Edition 26.1.2 targeting, the `silk_spawners` namespace, and the current scaffold-only status.

## Current Behavior

When installed into a compatible Minecraft Java Edition world as a datapack, the current scaffold is expected to load and run its load hook on `/reload`. It does not yet alter spawner drops, item data, placement behavior, spawn parameters, or refusal behavior.

## Planned Behavior

The next gameplay milestone is the Silk Touch pickup path: breaking a `minecraft:spawner` with a Silk Touch tool should drop a spawner item that carries the original mob type in Silk Spawners-owned custom data.

## Compatibility Notes

- Target runtime: Minecraft Java Edition 26.1.2.
- Target data pack format: `101.1`.
- Owned namespace: `silk_spawners`.
- Vanilla namespace usage in this version is limited to the load tag needed for datapack startup wiring.

## Validation

Static checks completed:

- Parsed `silk-spawners/pack.mcmeta` as JSON and confirmed `min_format` / `max_format` are both `101.1`.
- Parsed `data/minecraft/tags/function/load.json` as JSON and confirmed it references `silk_spawners:load`.
- Listed datapack runtime files and confirmed only the expected load hook and load tag exist.
- Checked that the current runtime files do not reference the prior third-party sample namespace, old scoreboard name, tick tag, or legacy `pack_format` key.
- Ran `git diff --check` with no whitespace errors.

Runtime validation still needed:

- Install the datapack into a Minecraft Java Edition 26.1.2 test world.
- Run `/reload`.
- Confirm the Silk Spawners load probe appears.

## Attribution Notes

The project continues to record third-party notice context for a related public "Silk Touch Spawners" listing on Modrinth. This release keeps the implementation independently authored and does not copy third-party code or assets.

## 24-72 Hour Next Steps

1. Run the `/reload` smoke check in a 26.1.2 vanilla test world.
2. Capture the observed load probe result.
3. Start the first gameplay slice by adding the Silk Touch spawner loot-table behavior.
