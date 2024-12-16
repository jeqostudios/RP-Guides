# Atlases

In snapshot 22w46a, a new directory atlases has been introduced for resource packs. Atlases stitch all your textures into one large sprite sheet to help with pack stability, load times, and performance.

## Information

Each armor set (if adding multiple especially) must be contained within a 64x32 canvas (default for 16 bit resolution armors)

### Valid Entries

| Entry | Description |
|-------|-------------|
| blocks | Textures used by block and item models. |
| banner_patterns, beds, chests, shield_patterns, shulker_boxes, signs | Used to render special-case models. |
| mob_effects | Textures used for effect icons in the UI. |
| paintings | Textures used for paintings. |
| particles | Textures used for particles. |

For most resource packs with minimal additional assets, the blocks entry will cover a majority of your pack.

### Types of Sources

| Type | Description |
|------|-------------|
| directory:<br>- source - directory in the pack (relative to /textures/)<br>- prefix - string added to the sprite name when loaded | Adds all files in a directory and its subdirectories (across all namespaces). |
| single:<br>- resource - location of a resource (relative to /textures/)<br>- sprite - sprite name (optional; if not supplied, it will default to resource) | Adds a single file. |
| filter:<br>- namespace, path - patterns (regular expressions) of IDs to be removed | Removes sprites matching the given pattern. |
| unstitch:<br>- resource - location of a resource (relative to /textures/; .png implied)<br>- divisor_x, divisor_y - determines the units used by regions<br>- regions - list of regions to copy from the source image | Copies rectangular regions from other images. |

## Creating an Atlas Configuration

### Step 1. Creating a New Directory

Navigate within your resource pack to `/assets/minecraft/` and create a new directory named `atlases`. Now your resource pack, if used in versions 1.19.3 or above, will be able to use and read any atlas configurations placed within this directory.

### Step 2. Adding a Directory

For the most part, a block atlas entry will cover a majority of the resource pack's textures. If you encounter other issues, or know that you'll need to setup another entry, refer to the entries table above. Create a new file named `blocks.json` within the new directory you just made.

Inside of our `blocks.json`, add the following code:

```json
{
    "sources": [
        {   "type": "single",
            "source": "custom/swords/",
            "sprite": "ruby-sword"
        }
    ]
}
```

### Step 3. Adding Singles (Optional)

To add a single file, add the following code to your atlas:

```json
{
    "sources": [
        {   "type": "single",
            "source": "custom/swords/",
            "sprite": "ruby-sword"
        }
    ]
}
```
*Adds a single texture from a specific given path.*

### Step 4. Filtering (Optional)

To filter, or remove, a certain directory or single, add the following code to your atlas:

```json
{
    "sources": [
        {   "namespace": "custom"
        }
    ]
}
```
*Filters out the entire custom namespace and all the textures within every subdirectory.*

```json
{
    "sources": [
        {   "path": "custom/swords/dungeon/gem/ruby-sword.png"
        }
    ]
}
```
*Filters out the ruby sword located deep within our custom namespace.*

### Step 5. Unstitching (Optional)

Not too much is known about this yet... tune back in soon.

## Example Atlas Configurations

### Multiple Entries

```json
{
    "sources": [
        {   "type": "directory",
            "source": "entity",
            "prefix": "entity/"
        },
        {   "type": "directory",
            "source": "custom",
            "prefix": "custom/"
        },
        {   "type": "single",
            "source": "custom/swords/",
            "sprite": "ruby-sword"
        }
    ]
}
```
*When adding multiple entries, you'll need to add a trailing comma except for the last entry.*

### ModelEngine

```json
{
    "sources": [
        {   "type": "directory",
            "source": "entity",
            "prefix": "entity/"
        }
    ]
}
```