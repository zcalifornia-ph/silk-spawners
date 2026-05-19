# Version 0.0.3 Docs

## Quick Diagnostic Read

v0.0.3 adds the first gameplay-facing datapack behavior: a Silk Touch-gated spawner loot table. It does not yet restore placed spawners.

## One-Sentence Objective

Create the pickup-side carrier item so a mined spawner can remember its source mob type for later placement restoration work.

## Why This Version Matters

The pickup path is the data handoff for the rest of the datapack. If the dropped item does not reliably carry the original `SpawnData.entity.id`, later placement logic has nothing trustworthy to restore.

## What Changed

- Added `silk-spawners/data/minecraft/loot_table/blocks/spawner.json`.
- The loot table emits `minecraft:spawner` only when the breaking tool has `minecraft:silk_touch` at level 1 or higher.
- The loot table copies the source block entity's `SpawnData.entity.id` into the dropped item's Silk Spawners custom data.
- The loot table sets the dropped item name to `Monster Spawner` with white, non-italic styling.
- The root README now documents version `v0.0.3`, current partial usage, and the fact that placement restoration is still pending.

## Current Behavior

The datapack now has:

- a Minecraft Java Edition 26.1.2 manifest,
- a reload-visible load hook,
- a spawner block loot-table override for Silk Touch pickup.

When the loot table runs as intended, a Silk Touch break of a seeded spawner should drop a spawner item with:

- `minecraft:custom_data` containing `silk_spawners.entity.id`,
- `minecraft:custom_name` rendering as `Monster Spawner`.

Non-Silk mining should not drop a spawner item.

## Not Included Yet

- Placing the marked item does not yet restore the spawner mob type.
- Spawn delay, spawn range, and other restored-spawner defaults are not implemented yet.
- Refusal behavior for unresolvable mob ids is not implemented yet.
- Multi-runtime smoke testing is not complete yet.

## Compatibility Notes

- Target runtime: Minecraft Java Edition 26.1.2.
- Target data pack format: `101.1`.
- Owned custom data namespace: `silk_spawners`.
- The only vanilla loot-table override in this version is `minecraft:blocks/spawner`.

## Validation

Static checks completed:

- Parsed the new spawner loot table as JSON.
- Confirmed the loot table references `minecraft:silk_touch`.
- Confirmed the copied custom data target is `silk_spawners.entity.id`.
- Confirmed the runtime datapack files do not introduce tick functions, scoreboard objectives, or placement data.
- Confirmed the only vanilla loot-table override present is the spawner block override.
- Ran `git diff --check` with no whitespace errors.

Runtime validation still needed:

- In a Minecraft Java Edition 26.1.2 test world, seed zombie, skeleton, spider, cave spider, blaze, and silverfish spawners.
- Break each seeded spawner with a Silk Touch tool.
- Inspect the nearest dropped item with `/data get entity @e[type=item,limit=1,sort=nearest] Item.components`.
- Confirm the mob id is present and correct under the Silk Spawners custom data.
- Mine a seeded spawner without Silk Touch and confirm no spawner item drops.

## Attribution Notes

The implementation remains independently authored. Third-party and trademark context remains documented in the repository notices.

## 24-72 Hour Next Steps

1. Run the pickup-path tests in a 26.1.2 vanilla test world.
2. Capture the item component output for each seeded spawner type.
3. Start the placement-restoration implementation after the pickup path is proven.
