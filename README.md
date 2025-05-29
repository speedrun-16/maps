# Map Archive

This repository hosts a collection of custom maps, mainly for Speedrun Mod.
Maps are organized by type and each map includes necessary files and metadata.

## Map Types

Currently, we support the following map types:

*   [Speedrun Maps](./speedrun/README.md)
*   [Deathrun Maps](./deathrun/README.md)

## Map Structure

Each map is contained within its own folder under its respective map type directory (e.g., `speedrun/map_name/`).
Every map folder includes:

*   `manifest.json`: A JSON file containing metadata about the map (authors, difficulty, release date, etc.).
*   `<map_name>.zip`: A compressed archive containing all necessary map files (`.bsp`, `.res`, custom textures/skyboxes, etc.).
    *   **ZIP structure:**
        ```
        maps/<map_name>.bsp
        maps/<map_name>.res
        gfx/env/<skybox_up>.tga (if custom skybox)
        gfx/env/<skybox_dn>.tga
        gfx/env/<skybox_lf>.tga
        gfx/env/<skybox_rt>.tga
        gfx/env/<skybox_ft>.tga
        gfx/env/<skybox_bk>.tga
        sound/... (if custom sounds)
        sprites/... (if custom sprites)
        ... other custom assets
        ```
*   `images/`: A directory containing screenshots or promotional images for the map.

### Manifest Schema (`manifest.json`)

```ts
{
    "type": "speedrun" | "deathrun",           // map type
    "name": string,                            // map name
    "authors": [string],                       // array of author names/nicknames/steamids
    "releaseDate": "YYYY-MM-DD",               // release date
    "difficulty": "trivial" | "easy" | "medium" | "hard" | "insane",
    "length": "tiny" | "small" | "medium" | "large" | "huge",
    "file": string,                            // filename of the .zip archive (e.g., "speedrun_enbo2.zip")
    "presentationUrl": string,                 // optional: URL to a YouTube video or similar
    "images": [string],                        // array of image filenames (relative to images/ dir)
    "tags": [string],                          // optional: array of tags (see below)
    "description": string                      // optional: Longer description of the map
}
```

## Tags

| Tag Name             | Description                                                                    |
|----------------------|--------------------------------------------------------------------------------|
| `ramp`               | Map contains ramp                                                              |
| `surf`               | Refers to a surf element where players glide along angled ramps                |
| `push`               | Indicates an element that propels the player, such as a trigger_push brush     |
| `existing_map_remake`| The level is a remake or reimagining of a pre-existing map                     |
| `60fps_unsupported`  | Impossible to complete or do a proper run at 60 FPS                            |
| `100fps_unsupported` | Impossible to complete or do a proper run at 100 FPS                           |
| `legit_unsupported`  | Impossible to complete or do a proper run without bunnyhopping                 |
| `stairs`             | Contains stair structures                                                      |
| `winding`            | Features twisting pathways, resembling winding corridors                       |
| `water`              | Contains underwater sections                                                   |
| `instinct`           | No clear or obvious path—requires players to explore and find their own route  |
