# Cadencier

A bridge mod between **Courseplay** and **AutoDrive** for Farming Simulator 25: it automatically chains field work (mulching, grass seeding, herbicide, fertilizer, rolling, etc.) by orchestrating the farm's vehicles and implements.

Courseplay knows how to run a single work course on a field, and AutoDrive knows how to drive a vehicle from one point to another — but neither knows how to chain several different courses on the same field, or arbitrate between several fields competing for the same vehicles and implements. Cadencier adds that orchestration layer on top of both, without replacing either.

## Features

- Simultaneous management of **every field owned by the player**, each with its own course sequence and its own priority order.
- **Configurable, reorderable** course sequences, with automatic hand-off to the next course as soon as one finishes.
- **Automatic vehicle selection** for each course, based on power, availability, proximity to the implement, and wear/damage state.
- **Shared implement pool** across all fields: each implement automatically returns to a dedicated storage point after use, with fully automated hitching/unhitching.
- **Dedicated HUD**: a configuration screen for the sequences and a supervision panel listing fields that are waiting or in error.
- Automatic resolution of common incidents (e.g. refueling) when possible, otherwise the affected field is paused with the reason displayed.
- Compatible with **any map** (no hard-coded farm configuration).

## Requirements

- Farming Simulator 25
- [Courseplay_FS25](https://github.com/Courseplay/Courseplay_FS25)
- [FS25_AutoDrive](https://github.com/Stephan-S/FS25_AutoDrive)

Cadencier does not generate routes itself: it orchestrates Courseplay courses and AutoDrive routes that the player has already recorded.

## Installation

*(to be completed once the mod is packaged — standard FS25 procedure: copy the `.zip` into the game's `mods` folder, then enable all three mods from the in-game mod menu)*

## Quick start

1. Record the desired courses in Courseplay and the routes in AutoDrive, as usual.
2. Set a storage point for each implement on the farm.
3. In the Cadencier tab, build each field's course sequence (implement + associated course) and set the priority order between fields.
4. Let it run: Cadencier hitches, executes, unhitches, and stores everything automatically.

## Architecture

- **Orchestrator** — state and sequence for each field.
- **Vehicle selection engine** — power/distance/wear algorithm.
- **Implement pool manager** — locking, storage points.
- **Courseplay / AutoDrive adapters** — the only layer that calls either mod's API directly.
- **Supervision module** — incident detection, feeds the HUD.

The full specification (algorithms, error cases, test plan) lives in the project's design document.

## Known limitations (V1)

- **Single-player only** — no multiplayer sync for now.
- No route generation: courses/routes must already exist in Courseplay/AutoDrive.
- Depends on the Courseplay_FS25 and FS25_AutoDrive APIs, both of which are under active (beta) development.

## Roadmap

- Multiplayer support
- Automatic route generation
- Advanced preventive maintenance management

## Contributing

Issues and pull requests are welcome. Please check the license of Courseplay_FS25 and FS25_AutoDrive before reusing any code from those projects.

## License

To be determined.

## Acknowledgements

- The [Courseplay](https://github.com/Courseplay/Courseplay_FS25) team
- [Stephan-S](https://github.com/Stephan-S/FS25_AutoDrive) for AutoDrive
