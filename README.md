# SGS2 Modding

Reverse-engineering and modding notes for **Ship Graveyard Simulator 2** (UE4.27, single monolithic pak).

## Quick facts

- Engine: Unreal Engine 4.27
- Packaging: one big `.pak` (all assets chunk 0)
- Mod approach: later-mounted `_P.pak` that overrides `/Game/...` paths (no new chunk IDs required)
- Useful tools: UE4SS, FModel / UAssetGUI + `Mappings.usmap`, UnrealPak

## Documentation

- [Structure overview](docs/structure.md) — asset registry shape, maps, construction kits, how the game loads ships
- [Ship catalog](docs/ships.md) — all `DT_Ships` rows, naming layers, sizes, prices, LevelNames
- [Modding guide](docs/modding.md) — minimum viable mod (duplicate a ship row)
- [Key classes](docs/classes.md) — native / blueprint-relevant types from UE4SS dump

## Project files

- [ShipGraveyard2.uproject](docs/ShipGraveyard2.json) — engine association, modules, plugins

## Notes

Raw multi-megabyte FModel JSON dumps and the full AssetRegistry have been cleaned from the local workspace to save space. The analysis above was generated from them. Full dumps can be re-extracted from the game pak with FModel if needed.

Minimum test ship donors: Tunacolada / Tunacolada_v2.
