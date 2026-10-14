# SGS2 Structure Overview

Generated from AssetRegistry + map/blueprint dumps. Every asset lives in **chunk 0**. A mod pak only needs matching `/Game/...` paths and a later mount order.

## Registry shape (from AssetRegistry.json, 17,358 assets)

| Fact | Value |
|---|---|
| Assets | 17,358 |
| Chunk | 0 on all of them |
| Worlds (`PrimaryAssetType: Map`) | 48 |
| Each map also has | a `_C` LevelScriptActor (`BPTYPE_LevelScript`) |
| `PKG_ContainsMap` | 96 (World + its `_C`) |
| `PKG_ContainsMapData` | 4 BuiltData registries |
| Textures / static meshes | 5,051 / 3,131 |
| Blueprint + generated class | 1,991 + 2,042 |
| DataTables | 76 |
| `ShipCountedResources` | 37 (`DA_*`) |

### Largest package trees

| Path | Assets | Role |
|---|---:|---|
| `/Game/Blueprints/ShipConstruction` | 3,136 | Plates, rooms, machinery Blueprints |
| `/Game/3D/ShipsHullProto` | 2,907 | Hull meshes and materials |
| `/Game/Assets/Props` | 529 | Loose props |
| `/Game/Animations/PartsShipHull` | 497 | Hull-part anims |
| `/Game/Assets/UI` | 442 | |
| `/Game/Assets/Ships` | 389 | Shared plating (`Poszycie`, `Poszycie_M`, `PoszycieTutorial`) |
| `/Game/Assets/ModularWalls` | 203 | `SM_ModularWalls*` |
| `/Game/Assets/ConnectorProto` | 222 | Connector meshes |
| `/Game/Assets/ModularFloors` | 115 | Deck meshes |
| `/Game/Blueprints/ToolShop` | 223 | Cutter upgrades |
| `/Game/Blueprints/PlayerHouse` | 181 | Yard hut |
| `/Game/Blueprints/ContractsConfigurations` | 112 | Per-ship job Blueprints |

`/Game/3D/ShipsHullProto` is the mesh library. Largest material/mesh sets include GrafZeppelin, Ohio, Wicher, BlueMelody, Titanic, Corvete, Fuso, Kursk, Pobieda, Janssonius, Icon, I-400, Solace, Kuzniecov, etc. Plus shared Props and GridMaterials.

## Maps

Yard / logic: `BaseLevel`, `Gameplay_CityNew`, `Gameplay_Logic`, `Start_Cutscene_Props`.

Career ships (examples): Tutorial Intro, MadSea, GreenRex, Caroline, Tunacolada / Tunacolada_v2, Mermaid, AOGGosiabelle, MultiWojti, Aramano, Fuso, Humbak, Gas Goober, Pobeda, Contrabando (30day), various DLC (subs, cruise, steam, fish, war).

Test maps exist (`TestShip_*`).

## Three names for one ship

| Layer | Pattern | Example |
|---|---|---|
| Shop row | `DT_Ships` key | `Tunacolada` |
| Streamed world | `Gameplay_Ship_<SizeOrDLC>_<Hull>` | `Gameplay_Ship_Small_Tunacolada` |
| Jobs | `BP_<Hull>Ship_Contracts` | `BP_TunacoladaShip_Contracts` |
| Scrap budget | `DA_<Hull>ShipResources` | `DA_TunacoladaShipResources` |
| Plates | `BP_Hull_<Ship>_*` or shared `BP_Poszycie_*` | |
| Rooms | `BP_SCP_Inside_*` | |
| Cut mesh/mass | `Dt_PartData_*` | |

`DT_Ships` lives at `/Game/Blueprints/Data/DT_Ships` (row struct `ShipData`). `DT_ShipContracts` is a stub; real jobs are under `ContractsConfigurations`.

`DA_*` counted-resources assets exist for most career/DLC wrecks. Air carriers (Enterprise, Kuzniecow, PeterZeppelin) are `isTestShip` and lack them. Shared leftovers: `DA_SmallShipResources`, `DA_BigShipResources`, `DA_TestShipResources`.

## Construction folders (ShipConstruction)

| Prefix | Count | Meaning |
|---|---:|---|
| `BP_Hull_<Ship>_*` | 426 | Per-ship outer plates |
| `BP_Poszycie_*` | 62 | Shared skin (`BP_Poszycie_M` = medium kit) |
| `BP_BlueDM_*` | 53 | Blue Dream shells |
| `BP_BeetwnHull_*` / `BP_BTH_*` | 37 | Gaps between sections |
| `BP_SCP_*` / `BP_SCP_Inside_*` | 70 / 43 | Modular interior kit |
| `BP_Engine*`, `BP_BoilerPart_*` | 26 / 15 | Plant |
| `BP_Icon_*`, `BP_CruiseBalconyBig_*` | 33 / 25 | Cruise-only |

Pipes use color prefixes (`Orange_`, `Grey_`, `Blue_`) plus `_With_Connectors`.

Reusable contract types (not per-ship): `BP_ContractEarn`, `BP_ContractCrane`, `BP_ContractGatherCategory`, `BP_ContractGatherSpecific`, `BP_ContractSortCategory`, `BP_ContractSortSpecific`, `BP_ContractSell`, `BP_ContractFindProp`, `BP_ContractHazards`.

## How the game uses this

`LevelName` on a `DT_Ships` row streams the World. The World is an `AShipBase` grid of `AShipGridSlot` cells (`WallData`, `FloorData`, elements, decorations). `UShipLoaderComponent` loads it. Cut pieces are `ADestructableBase`. Connectors are `AConnector` / `UConnectorSpotBase`.

See also [ships.md](ships.md) and [modding.md](modding.md).
