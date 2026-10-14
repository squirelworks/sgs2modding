# Modding Guide

## Minimum viable mod

1. Extract or open `DT_Ships` with UAssetGUI (UE 4.27 + `Mappings.usmap`).
2. Duplicate one existing row (best donors: **Tunacolada** or **Tunacolada_v2**).
3. Change the key, display name, price, etc. Keep `LevelName` pointing at an existing map so the world still streams.
4. Pak the modified data table (and any new assets) as a later `_P.pak` that mounts after the main game pak.
5. The game will see the new shop row; clicking it loads the referenced map.

No new chunk ID is required — everything is already chunk 0. Path matching + mount order is enough.

## Useful tools

- **UE4SS** — object dumps, live inspection, CXX header generation
- **FModel** — export maps / Blueprints / data tables as JSON
- **UAssetGUI** + `Mappings.usmap` — edit uassets / data tables
- **UnrealPak** (or equivalent) — build the `_P.pak`

## Key systems

- `AShipBase` + `AShipGridSlot` grid (walls, floors, elements, decorations)
- `UShipLoaderComponent` streams the wreck
- Cut pieces: `ADestructableBase`
- Connectors: `AConnector` / `UConnectorSpotBase` / `BP_Connector`
- Crane parts: `ABP_CraneAblePart_C` and related
- Computer UI (`ABP_Computer_C` + ship panel widgets) drives the shop

## Practical notes

- Shared plating kits (`BP_Poszycie_*`, `BP_Poszycie_M`) and modular interiors (`BP_SCP_*`) can be reused across ships.
- Per-ship hull plates live under `BP_Hull_<Ship>_*`.
- Contract logic is mostly in `ContractsConfigurations` Blueprints, not a single big data table.
- Counted scrap budgets are `DA_*ShipResources` data assets.

For deeper structure see [structure.md](structure.md) and the ship list in [ships.md](ships.md).
