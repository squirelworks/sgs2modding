# Ship Catalog (`DT_Ships`)

Source: `/Game/Blueprints/Data/DT_Ships` (row struct `ShipData`). 44 rows.

## Naming layers

| Layer | Pattern | Example |
|---|---|---|
| Shop / table key | `DT_Ships` key | `Tunacolada` |
| Streamed map | `Gameplay_Ship_*` | `Gameplay_Ship_Small_Tunacolada` |
| Contracts | `BP_*Ship_Contracts` | `BP_TunacoladaShip_Contracts` |
| Resources | `DA_*ShipResources` | `DA_TunacoladaShipResources` |

## Ship list (selected fields)

| Key | Display Name | Size | Price | LevelName | Test? |
|---|---|---:|---:|---|---|
| Tutorial | First Steps | 0 | 0 | Gameplay_Ship_Tutorial_Intro | |
| MadSea | MadSea | 0 | 1000 | Gameplay_Ship_MadSea | |
| GreenRex | Green-Rex | 0 | 2000 | Gameplay_Ship_Small_GreenRex | |
| Small_Caroline | Caroline | 0 | 5000 | Gameplay_Ship_Small_Caroline | |
| Snopkowich | Snopkowich | 0 | 7500 | Gameplay_Ship_Small_Caroline_v2 | |
| SlipperyHerring | Slippery Herring | 0 | 12000 | Gameplay_Ship_Small_CrazyOne | |
| GiekusMagikus | Chilling-Turtle | 1 | 20000 | Gameplay_Ship_Small_Tunacolada_v2 | |
| MaroonLagoon | Maroon Lagoon | 1 | 25000 | Gameplay_Ship_Tutorial_Short | |
| Mariner | Mariner | 1 | 30000 | Gameplay_Ship_Prolog | |
| Tunacolada | Tunacolada | 1 | 40000 | Gameplay_Ship_Small_Tunacolada | |
| Mermaid | Heavy Mermaid | 2 | 120000 | Gameplay_Ship_Medium_Mermaid | |
| Medium_GosiaBelle | AOG-Gosiabelle | 2 | 150000 | Gameplay_Ship_Medium_AOGGosiabelle | |
| MultiWojti | MultiWojti | 2 | 175000 | Gameplay_Ship_Medium_MultiWojti | |
| AramanoAdrianii | Aramano Adrianii | 2 | 200000 | Gameplay_Ship_Medium_AramanoAdrianii | |
| WarDLCsmall_1 | Chevy | 0 | 75000 | Gameplay_Ship_DLC_Small_UNFuso | |
| WarDLCmid_1 | Wicher | 1 | 160000 | Gameplay_Ship_DLCMedium_ORP_WICHER | |
| WarDLCmid_2 | Fuso | 2 | 400000 | Gameplay_Ship_DLC_Medium_UNFuso | |
| gasgoober | Gas Goober | 3 | 400000 | Gameplay_Ship_Big_GasGoober | |
| Humbak | Humbak | 3 | 500000 | Gameplay_Ship_Big_Humbak | |
| big | Big Chung | 3 | 600000 | Gameplay_Ship_Milestone5 | |
| GiantDLCPobieda | Pobeda | 3 | 750000 | Gameplay_Ship_DLC_Big_Pobeda | |
| Giant_30day | Contrabando | 3 | 950000 | Gameplay_Ship_DLC_Giant_30Day | |
| Submarine_I400 | I-400 | 1 | 92000 | Gameplay_Ship_DLC_Submarine_I-400 | |
| Submarine_Kursk | Kursk | 2 | 195000 | Gameplay_Ship_DLC_Submarine_Kursk | |
| Submarine_Ohio | OhioClass | 2 | 350000 | Gameplay_Ship_DLC_Submarine_OhioClass | |
| Submarine_Uboat | U-boat Type VII | 0 | 80000 | Gameplay_Ship_DLC_Submarine_Uboat | |
| Cruise_MVJans | MVJanssonius | 2 | 1000000 | Gameplay_Ship_DLC_Cruise_MVJanssonius | |
| Cruise_MVBlueDream | MV Blue Dream | 3 | 1500000 | Gameplay_Ship_DLC_Cruise_MVBlueDreamMelody | |
| Cruise_Icon | MV Symbol of the Ocean | 3 | 1500000 | Gameplay_Ship_DLC_Cruise_IconOfTheSea | |
| Steam_Solace | Solace | 1 | 350000 | Gameplay_Ship_DLC_Steam_Solace | |
| Steam_GrafZeppelin | Zeppelin | 2 | 600000 | Gameplay_Ship_DLC_Steam_GrafZeppelin | |
| Steam_Titanic | Titan | 2 | 750000 | Gameplay_Ship_DLC_Steam_Titanic | |
| Fish_Arc | Arc | 1 | 310000 | Gameplay_Ship_DLC_Fish_Arc | |
| Fish_SeaHunter | Sea Hunter | 1 | 365000 | Gameplay_Ship_DLC_Fish_SeaHunter | |
| Fish_Mono-Brew | Mono-Brew | 2 | 540000 | Gameplay_Ship_DLC_Fish_MonoBrew | |
| Fish_RichKali | Richi-Kali | 3 | 660000 | Gameplay_Ship_DLC_Fish_RichiKali | |
| testmap | testshipKP | 0 | 1 | TestShip_ForBuildTestShip_01 | yes |
| TestShipElementsNew_DevRoom | DevRoom | 0 | 1 | TestShip_WallElements | yes |
| TestShipElementsNew_CruiseSciany | Modularne Sciany | 0 | 1 | TestShip_WallElementsNew | yes |
| TestCustomGridElements | Grid elementy | 0 | 1 | TestShip_CustomGridElements_1 | yes |

(Additional DLC / test rows exist; full table has 44 entries.)

## ShipData fields (observed)

`visibleInComputer`, `isTestShip`, `Image`, `Name`, `Description`, `Price`, `Size`, `Difficulty`, `Contracts`, `LevelName`, `maxResources`, `PotentialResourceValue`, `ConnectorHPMultiplier`, `AchievementName`, `RequiredDLC`

`LevelName` is what gets streamed. Keep it pointing at an existing cooked map for a simple override mod.
