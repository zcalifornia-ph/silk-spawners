# Version 0.0.1 Docs

## Quick Diagnostic Read

v0.0.1 is an initial public scaffold for Silk Spawners. It is not a playable datapack release yet.

## One-Sentence Objective

Establish the public repository baseline for a Minecraft Java Edition Silk Touch spawner datapack before gameplay functions, loot tables, and validation worlds are added.

## What Changed

- Added public-facing repository documentation for project purpose, installation expectations, contribution process, conduct, security reporting, and third-party notices.
- Added the MIT license for this repository's original work.
- Added a branded project image under `repo/images/project_screen.png`.
- Added minimal datapack metadata at `silk-spawners/pack.mcmeta`.
- Clarified that the current release is a scaffold and does not yet include playable Silk Touch spawner behavior.

## Current Behavior

The repository contains enough metadata and documentation to describe the project and establish its public baseline. The datapack directory does not yet include gameplay functions, loot tables, predicates, scoreboards, or validation artifacts.

## Planned Behavior

The planned datapack will let players break monster spawners with Silk Touch, preserve the original mob type on the dropped item, and restore that mob type when the spawner is placed again.

## Compatibility Notes

The scaffold uses Minecraft Java Edition data pack version 88.0 metadata. Minecraft's Java Edition 1.21.9 release notes describe data pack version 88.0 and the newer `min_format` / `max_format` metadata fields for `pack.mcmeta`.

## Attribution Notes

The project records third-party notice context for a related public "Silk Touch Spawners" listing on Modrinth. The referenced listing is licensed ARR, so this repository must not copy or redistribute that code, assets, or files. The implementation work should remain independently authored.

## Validation

- Reviewed the staged repository scope before writing the commit documentation.
- Checked the public documentation for internal workflow wording and removed it where it appeared.
- Validated that `silk-spawners/pack.mcmeta` is JSON-shaped metadata for the scaffold.
- No Minecraft world behavior validation was run because v0.0.1 does not include gameplay implementation yet.

## External References

- Modrinth Silk Touch Spawners version page: <https://modrinth.com/datapack/silk-touch-spawners/version/1.4%2Bmod>
- Minecraft Java Edition 1.21.9 release notes: <https://www.minecraft.net/en-us/article/minecraft-java-edition-1-21-9>
