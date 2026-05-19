<!-- Adapted from Best-README-Template. Reference-style links live at the bottom of this file. -->
<a id="readme-top"></a>

<!-- PROJECT SHIELDS -->
<div align="center">

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

</div>

<!-- ABOUT THE PROJECT -->
[![Silk Spawners Screen Shot][product-screenshot]](https://github.com/zcalifornia-ph/silk-spawners)

<div align="center">
<h3 align="center">Silk Spawners</h3>

  <p align="center">
    <strong>A Minecraft Java Edition datapack scaffold for Silk Touch spawner pickup and replacement.</strong>
    <br />
    Version: v0.0.2
    <br />
    Status: Load-hook scaffold
    <br />
    <a href="https://github.com/zcalifornia-ph/silk-spawners"><strong>Explore the repository »</strong></a>
    <br />
    <br />
    <a href="https://github.com/zcalifornia-ph/silk-spawners/issues/new?labels=bug">Report Bug</a>
    &middot;
    <a href="https://github.com/zcalifornia-ph/silk-spawners/issues/new?labels=enhancement">Request Feature</a>
  </p>
</div>

<!-- TABLE OF CONTENTS -->
## Table of Contents

1. [About The Project](#about-the-project)
   - [Current Scope](#current-scope)
   - [Planned Features](#planned-features)
   - [Planned Implementation](#planned-implementation)
   - [What Silk Spawners Is Not](#what-silk-spawners-is-not)
   - [Target Stack](#target-stack)
2. [Getting Started](#getting-started)
   - [Prerequisites](#prerequisites)
   - [Installation](#installation)
3. [Usage](#usage)
4. [Roadmap](#roadmap)
5. [Contributing](#contributing)
6. [License](#license)
7. [Contact](#contact)
8. [Acknowledgments](#acknowledgments)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## About The Project

Silk Spawners is a Minecraft Java Edition datapack project for a single, focused mechanic: monster spawners should become collectible with the Silk Touch enchantment and remember the mob they were configured to spawn when placed back into the world.

The v0.0.2 baseline is a datapack scaffold, not a playable gameplay release yet. It contains the repository documentation, license and attribution files, branded project image, Minecraft Java Edition 26.1.2 datapack metadata, and a minimal load hook that can be used to confirm the pack is wired into `/reload`. Gameplay loot tables, predicates, placement behavior, and validation worlds are planned for follow-up implementation releases.

The intended implementation is vanilla datapack-only: no mods, no server plugins, and no resource pack requirement.

### Current Scope

- Root project documentation for installation expectations, contribution process, security reporting, and attribution.
- MIT license text for this repository's original work.
- Third-party and trademark notices for the related public gameplay concept and Minecraft marks.
- Branded project screenshot asset at `repo/images/project_screen.png`.
- Minimal `silk-spawners/pack.mcmeta` metadata and load hook for a Minecraft Java Edition 26.1.2 datapack scaffold.
- No playable Silk Touch spawner behavior is included in v0.0.2.

### Planned Features

- Pick up any monster spawner with a Silk Touch tool and keep its mob type.
- Place the picked-up spawner anywhere and it restores the original mob.
- Dropped spawner items are auto-renamed to "Monster Spawner" with consistent default spawn parameters (4-block range, 6 max nearby entities, 16-block player range).
- Pure vanilla datapack. No mods, plugins, or resource pack required.
- Works in singleplayer and on any vanilla-compatible server.

### Planned Implementation

- A custom loot table overrides the default spawner drop, gated on the `minecraft:silk_touch` enchantment predicate. When that condition fires, the dropped spawner item carries the original mob's entity ID in its custom data.
- A tick function scans a 9x9x11 region around any player who just used a spawner (tracked via the `minecraft.used:minecraft.spawner` statistic) and detects freshly placed empty spawners.
- When an empty spawner is found, a block function rewrites its `SpawnData.entity` field from the item's stored custom data, restoring the original mob.
- Default spawn parameters are applied so picked-up spawners behave consistently regardless of source.

### What Silk Spawners Is Not

- Not a finished gameplay release yet. The current version is a public scaffold.
- Not a mod or a server plugin. The planned implementation is a vanilla datapack only.
- Not a creative-mode item generator. Spawners must be obtained legitimately with a Silk Touch tool.
- Not a replacement for spawner-handling plugins on heavily modded servers.

### Target Stack

- Minecraft Java Edition datapack metadata (data pack format 101.1)
- Vanilla `.mcfunction` scripting for the planned gameplay logic
- Custom loot tables and predicates for the planned Silk Touch drop behavior
- Namespace map: `silk_spawners` owns pack behavior; `minecraft` is used only for vanilla integration tags and the planned `minecraft:blocks/spawner` loot-table override.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- GETTING STARTED -->
## Getting Started

### Prerequisites

- Minecraft Java Edition 1.21.9 or later for data pack version 88.0 metadata.
- A Silk Touch tool will be required once gameplay behavior is implemented.

### Installation

v0.0.2 is for repository inspection and datapack wiring checks, not gameplay use. The datapack metadata and load hook can be loaded by Minecraft, but the Silk Touch spawner mechanic is not implemented yet.

1. Clone the repository.

   ```sh
   git clone https://github.com/zcalifornia-ph/silk-spawners.git
   ```

2. Review the scaffold under `silk-spawners/`.
3. After a future gameplay release, copy the `silk-spawners/` directory into your world's `datapacks/` folder.
4. In-game, run:

   ```text
   /reload
   ```

5. Confirm the datapack is loaded:

   ```text
   /datapack list
   ```

6. For the current scaffold, `/reload` is expected to run the load hook and print a short Silk Spawners probe message.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- USAGE EXAMPLES -->
## Usage

There is no gameplay usage in v0.0.2. Planned usage after implementation:

1. Enchant a pickaxe with Silk Touch.
2. Break a monster spawner with the enchanted pickaxe.
3. Place the dropped spawner item back into the world.
4. The datapack restores the saved mob type and activates the placed spawner.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ROADMAP -->
## Roadmap

- [x] v0.0.1 - Initial public repository scaffold, governance docs, project image, and datapack metadata.
- [x] v0.0.2 - Minecraft Java Edition 26.1.2 datapack metadata and load-hook scaffold.
- [ ] v0.1.0 - First playable datapack implementation for Silk Touch spawner pickup and replacement.

See the [open issues](https://github.com/zcalifornia-ph/silk-spawners/issues) for proposed features and known gaps.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTRIBUTING -->
## Contributing

Contributions are welcome. See [CONTRIBUTING.md](CONTRIBUTING.md), [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md), and [SECURITY.md](SECURITY.md) for process, behavior, and vulnerability reporting.

1. Fork the project.
2. Create your feature branch (`git checkout -b feat/your-feature`).
3. Commit your changes (`git commit -m 'feat: add some feature'`).
4. Push to your branch (`git push origin feat/your-feature`).
5. Open a pull request.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Top contributors

<a href="https://github.com/zcalifornia-ph/silk-spawners/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=zcalifornia-ph/silk-spawners" alt="contrib.rocks image" />
</a>

<!-- LICENSE -->
## License

Distributed under the MIT License. See [LICENSE.txt](LICENSE.txt) for the full text.

Origin, attribution, and trademark notices for the upstream "Silk Touch Spawners" datapack concept and Minecraft trademarks are recorded in [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md). The MIT grant in `LICENSE.txt` applies only to this repository's own code and assets.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTACT -->
## Contact

Maintainer:

- Zildjian E. California - [@zcalifornia-ph](https://github.com/zcalifornia-ph) - <zecalifornia@up.edu.ph>

Profiles:

- LinkedIn: [zcalifornia](https://linkedin.com/in/zcalifornia)
- ORCID: [0009-0002-2357-7606](https://orcid.org/0009-0002-2357-7606)
- ResearchGate: [Zildjian-California](https://www.researchgate.net/profile/Zildjian-California)
- Twitter: [@zcalifornia_](https://twitter.com/zcalifornia_)

Project Link: [https://github.com/zcalifornia-ph/silk-spawners](https://github.com/zcalifornia-ph/silk-spawners)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

- The Minecraft Java Edition team for the vanilla datapack system that makes mod-free mechanics like this possible.
- The Minecraft community for documenting datapack format internals and loot-table conventions.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
[contributors-shield]: https://img.shields.io/github/contributors/zcalifornia-ph/silk-spawners.svg?style=for-the-badge
[contributors-url]: https://github.com/zcalifornia-ph/silk-spawners/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/zcalifornia-ph/silk-spawners.svg?style=for-the-badge
[forks-url]: https://github.com/zcalifornia-ph/silk-spawners/network/members
[stars-shield]: https://img.shields.io/github/stars/zcalifornia-ph/silk-spawners.svg?style=for-the-badge
[stars-url]: https://github.com/zcalifornia-ph/silk-spawners/stargazers
[issues-shield]: https://img.shields.io/github/issues/zcalifornia-ph/silk-spawners.svg?style=for-the-badge
[issues-url]: https://github.com/zcalifornia-ph/silk-spawners/issues
[license-shield]: https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge
[license-url]: https://github.com/zcalifornia-ph/silk-spawners/blob/main/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/zcalifornia
[product-screenshot]: repo/images/project_screen.png
