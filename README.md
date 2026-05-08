# INU GTA SA Asset Library

A ready-to-use Blender Asset Library with **12,884+ models** extracted from
GTA San Andreas, fully categorized, with auto-generated thumbnails and
embedded IDE metadata. Drag-and-drop any model into your scene — textures,
draw distance and model_id come along for the ride.

Built for video previews, animated cinematics, and custom map development
in Blender.

![preview screenshot](docs/preview.png) <!-- replace with real screenshot -->

---

## What you get

| Catalog                       | Models | Notes                                      |
| ----------------------------- | -----: | ------------------------------------------ |
| Vehicles                      |    208 | Cars, bikes, planes, boats with armatures  |
| Peds                          |    264 | Civilians, gang members, cops              |
| Weapons                       |     50 | Firearms, melee, grenades                  |
| Cutscene                      |      5 | Cutscene-only hierarchy models             |
| LOD                           |  4,351 | Low-poly LOD twins of map objects          |
| Map Objects / Los Santos      |  1,760 | Buildings, props, vegetation               |
| Map Objects / San Fierro      |  1,348 | "                                          |
| Map Objects / Las Venturas    |  1,483 | "                                          |
| Map Objects / Country         |  1,899 | Bone County, Tierra Robada, Whetstone      |
| Map Objects / Generic         |  1,461 | Shared / generic                           |
| Map Objects / Interiors       |     55 | Interior decorations                       |

Each asset is a Blender **Collection** with:
- Mesh + materials + (where applicable) armature
- Pre-resolved texture references via `//textures/<name>.png`
- Embedded IDE metadata on every mesh:
  - `obj.inu.model_id` — original GTA SA model ID
  - `obj.inu.txd_name` — texture dictionary name
  - `obj.inu.draw_distance` — IDE-defined draw distance
  - `obj.inu.ide_flags` — IDE flags (timed, breakable, etc.)
- Auto-rendered 128×128 thumbnail at iso 3/4 angle

---

## Installation

1. Go to [Releases](../../releases/latest) and download all archive parts.
2. Extract everything to a single folder (e.g. `D:\Blender_Libraries\INU_GTA_SA\`).
   The folder must contain `blender_assets.cats.txt` and `textures/` at its root.
3. Open Blender → **Edit → Preferences → File Paths → Asset Libraries → +**
4. Add the extracted folder. Name it `GTA SA`.
5. Open an Asset Browser editor, pick `GTA SA` from the dropdown — done.

Drag-and-drop any model into the 3D View. Textures resolve automatically.

**Requirements:** Blender 4.2 or newer. No additional add-ons needed for
browsing/dragging. To re-export modified models back to game format, install
[INU Tools](https://github.com/INU-ez/INU_Tools-GTA-sa-).

---

## Build it yourself

If you have a heavily modded GTA SA install (extra cars, weapons, custom
districts), you can rebuild the library against your own files using the
[INU Tools](https://github.com/INU-ez/INU_Tools-GTA-sa-) addon plus the
`build_library.py` script in this repository.

```powershell
blender --background --python build_library.py -- `
    --cache "<path to .inu_cache>" `
    --game-root "<path to GTA SA install>" `
    --output "<destination folder>"
The script reads data/gta.dat + data/default.dat, walks every IDE,
classifies each DFF, and produces the same asset library structure for
your modded set. See --help for all flags.

Limitations:

Modloader (Junior_Djjr) virtualizes mods at runtime — files on disk look vanilla. Merge mods into real IMG archives first.
CLEO-registered models (0AAB-style) bypass IDE — won't be detected.
Disclaimer
All 3D models, textures, and metadata in this library are © Rockstar Games.
This repository redistributes them in a transformed format
(Blender .blend) for modding, educational and previsualization purposes
only. No commercial use intended. The original game files are required
to use these assets in any practical workflow.

If you are a rights holder and would like this repository taken down,
open an issue or contact the maintainer — it will be removed promptly.

Credits
Models, textures, IDE data: Rockstar Games / Rockstar North
Extraction & library build pipeline: INU Tools
Maintainer: @INU-ez