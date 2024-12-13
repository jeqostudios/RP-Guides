# Custom Armor Guide

## Introduction
Custom armor is now available in modern versions of Minecraft using core shaders. Note that alternative render engines such as Optifine, Iris, etc. will be incompatible or may cause additional errors. This guide uses a core shader created by [AncientKingg](https://github.com/Ancientkingg/fancyPants).

[Download Example Resource Pack](https://jeqo.net/files/fancyPants-master.zip)

## Information

Each armor set must be contained within a 64x32 canvas (default for 16 bit resolution armors).

### Armor Identification
Each armor set consists of two files (one for each layer) with three "settings pixels":

1. **Color ID (0,0)**: Assigns the color to the armor for in-game usage
2. **Animation (0,1)**: Contains RGB values for:
   - Amount of frames
   - Speed (default: 24 seconds per frame)
   - Interpolation (Boolean: >0 = true, 0 = false)
3. **Additional Settings (0,2)**: Contains RGB values for:
   - Emissivity (1 = partial, >1 = full)
   - Tint (disabled by default)
   - N/A

### Restrictions

#### Texture Resolutions
Different resolutions are supported but must be specified in the shader. To change from default (16):

1. Navigate to `assets/minecraft/shaders/core/`
2. Edit `rendertype_armor_cutout_no_cull.fsh`
3. Modify line 6:
```glsl
#define TEX_RES 16
```

#### Layer Overlays
- `leather_layer_1_overlay.png` and `leather_layer_2_overlay.png` must always exist
- Both must remain completely transparent to avoid errors

## Creating Custom Armor

### Step 1: Creating Layer Files
1. Create a 32x64 sprite for layer 1
2. Create a 32x64 sprite for layer 2

![Layer Example](https://jeqo.net/data/attachments/0/143-a739c88c191ef669b53351305c012d2a.jpg)

### Step 2: Color ID Assignment
1. Add a white pixel (#ffffff) at 0,1 (required only for first armor texture)
2. Set color ID at 0,0 (e.g., red: rgb(255,0,0))

### Step 3: Animation (Optional)
1. Add frames below the armor texture
2. Set animation pixel at 0,1 with RGB values for:
   - Number of frames
   - Animation speed
   - Interpolation

### Step 4: Emissivity (Optional)
1. Create a copy of armor texture to the right
2. Use opacity for emissivity levels:
   - Black = no emissivity
   - White = full emissivity

### Step 5: Multiple Armor Sets
- Add sets horizontally to the right
- Each set must have a unique RGB color ID
- Maintain proper spacing for emissivity maps if used

### Step 6: In-Game Usage
1. Convert your color ID RGB values to decimal using an RGB to decimal converter
2. Use the following command format:
```minecraft
/give @s leather_helmet{display:{color:16711680}}
```

Note: 16711680 is the decimal value for RGB(255,0,0) (red)

## Need Help?
Join our [Discord community](https://jeqo.net/discord) for support and discussions.