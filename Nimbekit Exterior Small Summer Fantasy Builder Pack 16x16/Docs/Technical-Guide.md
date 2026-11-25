# Technical guide

## Image layouts

| File | Pixels | Columns × rows | Tile size | Margin | Spacing |
| --- | --- | --- | --- | ---: | ---: |
| All-600-16x16.png | 400×384 | 25×24 | 16×16 | 0 | 0 |
| All-600-16x16-Padded.png | 500×480 | 25×24 | 16×16 | 2 | 4 |
| Each category atlas | 160×160 | 10×10 | 16×16 | 0 | 0 |
| Each individual asset | 16×16 | 1×1 | 16×16 | 0 | 0 |

All PNG exports use RGBA. Alpha is either 0 or 255. Source pixels use one shared palette with up to 256 opaque colors. The GPL palette can be imported into compatible image editors; it is not a license file.

There are eight atlases in total. Atlas copies are alternate layouts of the same 600 assets and are not counted as additional assets.

## IDs and coordinates

The filename ID and manifest `id` are one-based, from 1 to 600. Tiled local tile IDs and manifest `atlas_index` are zero-based, from 0 to 599. Map GIDs use firstgid=1: 0 is an empty cell, 1–600 refer to pack assets.

For asset ID N, on the regular complete atlas:

    index = N - 1
    x = (index % 25) * 16
    y = floor(index / 25) * 16
    width = height = 16

For the padded atlas:

    x = 2 + (index % 25) * 20
    y = 2 + floor(index / 25) * 20

The JSON manifest contains the standard atlas rectangles and an individual PNG path for every asset. File paths under each asset are relative to the pack root. The top-level atlas file path is relative to the Data folder.

## Recommended import approach

Import the PNG as a 2D sprite or tileset texture, disable lossy texture compression, select nearest-neighbor/point filtering, and use 16×16 slices. Use integer camera zooms or integer scaling when possible. For isolated objects, use a consistent bottom-center origin; for tiles, align to your map grid. Add collisions and navigation according to your own gameplay.

The examples reference `../Tiled/Exterior-Small-Summer-Fantasy-600.tsx`, and that tileset references `../Assets/Atlases/All-600-16x16.png`. Keep the folders together after extraction. Use the padded tileset only when importing the padded image.

TMX and TMJ are two representations of the same maps; CSV files provide the five layers separately. CSVs contain decimal IDs, with 0 for empty cells. They do not carry image paths or layer rendering rules.

## Validation

The release checks verify 600 individual files, 16×16 dimensions, nonempty alpha, distinct pixel hashes, correct atlas rectangles, binary alpha, unique IDs/names, and valid map references. Example PNGs are also compared with renders reconstructed from the saved map data. This verifies the exported data, not a particular engine runtime.

## Scope

Static art only. No automatic terrain transitions, collisions, character controllers, gameplay code, audio, animation, layered art source files or native engine scenes are included. Construction examples use manual placement. Full-size trees can be built or drawn as larger assets in your project; the supplied trees are compact single-cell vegetation.

Format reference: https://doc.mapeditor.org/en/stable/reference/tmx-map-format/
JSON reference: https://doc.mapeditor.org/en/stable/reference/json-map-format/
