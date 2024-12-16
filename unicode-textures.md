## Overview
Unicode textures allow you to add custom symbols and characters that can be used in text. This is commonly used for creating custom icons in chat messages, signs, or anywhere text can be displayed.

## Implementation

### Step 1: Creating the Texture
First, create your texture file. This should be a PNG image where each character is 16x16 pixels. Multiple characters can be arranged in a grid format.

Place your texture file in:

```makefile
📁resource_pack
└── 📁assets
    └── 📁minecraft
        └── 📁textures
            └── 📁font
                └── 📑custom_icons.png
```

### Step 2: Creating the Font Provider
Create a JSON file that defines how your texture should be interpreted as Unicode characters. Place it in:

```makefile
📁resource_pack
└── 📁assets
    └── 📁minecraft
        └── 📁font
            └── 📑default.json
```

The JSON file should look like this:

```json
{
    "providers": [
        {
            "type": "bitmap",
            "file": "minecraft:font/custom_icons.png",
            "ascent": 8,
            "height": 16,
            "chars": [
                "\uE000"
            ]
        }
    ]
}
```

### Parameters Explained
| Parameter | Description |
|-----------|-------------|
| type | The type of font provider. Use "bitmap" for image-based characters |
| file | Path to your texture file |
| ascent | Vertical offset of the character (usually half of height) |
| height | Height of each character in pixels |
| chars | Array of Unicode characters to map to your textures |

### Using Unicode Characters
To use your custom characters in-game, you can copy and paste the Unicode character (e.g. \uE000) into chat messages, signs, or use them in translation files.

## Tips
- Each Unicode character from \uE000 to \uF8FF is available for custom use
- Characters are mapped left-to-right, top-to-bottom in your texture file
- Make sure your texture dimensions are multiples of 16x16 pixels
