# Nimbekit — Exterior Small Summer Fantasy Builder Pack
## 600 assets · 16×16 pixels · Version 1.0

Build sunny villages, cottage gardens, orchards, workshops and enchanted groves with one coordinated set of building pieces, scenery props, plants and terrain.

Every individual asset PNG is exactly 16×16 pixels. The 600 count includes individual surface tiles, building components, objects and structural/color variants. It does not mean 600 complete buildings. Buildings in the example maps are assembled from multiple tiles. The vegetation includes compact trees and saplings that fit a single tile.

## Start here

1. Open `Examples/01-Summer-Village.tmx` in a TMX-compatible editor, or inspect its native PNG.
2. Import `Assets/Atlases/All-600-16x16.png` using a 16×16 grid, zero margin and zero spacing.
3. Use nearest-neighbor / point filtering, no texture compression, and integer display scales.
4. Place terrain first, architecture above it, and props/vegetation on separate layers.
5. Find any tile by its stable numeric ID in `Data/Asset-Index.csv` or the six visual catalogs in `Docs`.

## Included assets

| IDs | Category | Count |
| --- | --- | ---: |
| 001–100 | Walls, floors and foundations | 100 |
| 101–200 | Roofs, doors, windows, trim, fences and steps | 100 |
| 201–300 | Village, market, farm, workshop and household props | 100 |
| 301–400 | Treasure, alchemy, magic, ruins, camp and festival props | 100 |
| 401–500 | Trees, shrubs, flowers, crops, mushrooms and water plants | 100 |
| 501–600 | Grass, soil, paving, water, shorelines, ledges and crossings | 100 |
| | Total | 600 |

## Files

- `Assets/Individual/`: 600 named, individual PNG files, grouped into six folders.
- `Assets/Atlases/`: one complete atlas, one padded complete atlas, and six category atlases.
- `Data/`: CSV index, JSON atlas manifest, and shared 256-entry GPL color palette.
- `Tiled/`: standard and padded TSX tilesets with asset names and IDs.
- `Examples/`: three editable maps in TMX and TMJ, CSV layers, and native-size PNG renders.
- `Docs/`: six numbered visual catalogs, technical notes and a short building guide.
- `LICENSE.txt`: permissions for using and modifying the assets in projects.

## Example maps

All three maps use only the 600 included assets and contain five tile layers: Ground, Paths, Architecture, Details, Vegetation. Each is 40×25 tiles / 640×400 pixels.

- Summer Village: six modular houses, a central well, market goods and street furniture.
- Orchard and Garden: a cottage, fruit trees, crop beds, a pond and crossing.
- Enchanted Grove: a forest shrine, crystals, ruins and a small campsite.

These are editable scene examples, not playable games. They contain no actors, scripts, collision shapes, navigation meshes or automatic terrain rules. The pack contains static graphics; it does not include animation, characters, audio or native Unity/Godot project files.

## Display and placement

Use the complete atlas or category atlases with zero spacing. The padded atlas has 2-pixel outer margins and 4-pixel spacing; the padding is transparent, not color-extruded. Keep point filtering enabled. Avoid resampling the assets with bilinear filtering.

Surface tiles are opaque. Object sprites have binary transparency. Place small objects over a ground tile. Choose matching corner/edge tiles manually when building paths, shorelines and walls; this is not an exhaustive automatic Wang/autotile set. No seam-free guarantee is made for arbitrary combinations of unrelated variants.

The PNG files are engine-neutral. The TSX/TMX/TMJ files have been checked for valid tile counts, IDs and local file references; engine runtime integration and editor-specific import settings remain project-specific.

See `Docs/Technical-Guide.md` and `Docs/Building-Recipes.md` for layouts and IDs.
