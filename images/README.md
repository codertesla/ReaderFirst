# Theme Preview Images

The Hugo Themes submission requires two preview images at the repository root `images/` folder, both at a **3:2** aspect ratio:

| File                | Dimensions  | Purpose                                  |
| ------------------- | ----------- | ---------------------------------------- |
| `screenshot.png`    | 1500 × 1000 | Full-screen theme screenshot             |
| `tn.png`            | 900 × 600   | Thumbnail shown in the themes gallery    |

This folder currently ships **SVG placeholders** (`screenshot.svg`, `tn.svg`) so the repository structure is complete. Before submitting to the Hugo Themes directory:

1. Take a real screenshot of the theme running `cd exampleSite && hugo server`.
2. Export it to `images/screenshot.png` at **1500 × 1000**.
3. Export a cropped thumbnail to `images/tn.png` at **900 × 600**.
4. Optionally remove the `.svg` placeholders once the `.png` files are in place.

> Hugo Themes only recognizes `.png` (and historically `.jpg`) files for `screenshot` and `tn`. SVG files are ignored by the gallery build, so the real exports must be raster PNGs.
