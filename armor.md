Custom armor is now available to be implemented in modern versions of Minecraft using core shaders. With the use of core shaders, alternative render engines such as Optifine, Iris, etc. will be incompatible or may cause additional errors, so please take caution. The method covered in this guide uses a core shader created by [AncientKingg](https://github.com/Ancientkingg/fancyPants).

For a pre-made example resource pack click [here](https://jeqo.net/files/fancyPants-master.zip).

## Information

Each armor set (if adding multiple especially) must be contained within a 64x32 canvas (default for 16 bit resolution armors)

### Armor Identification

Each armor set will consist of two files, one for each layer, and within those texture files each armor will have 3 "settings pixels". These 3 pixels are:

* (0,0) = Color ID; this assigns the color to the armor (for usage in-game).

* (0,1) = Animation; this contains rgb(amount of frames, speed, interpolation). Speed by default is 24 seconds per frame, and interpolation is a Boolean value (can be set to true (> 0) or false (0).

* (0,2) = Additional armor settings; this contains rgb(emissivity, tint, N/A). Color tinting disabled by default and can be toggled. Emissivity can be set to 1 for partial emissivity and > 1 for full emissivity. For partial emissivity armors, the armor texture to the right will be used as an emissivity map; the alpha of the pixel will act as the emissivity level.

### Restrictions

#### Texture Resolutions

Different armor texture resolutions are supported, though they must be specified within the shader. To change the resolution value from the default, 16, to something else, go to `\assets\minecraft\shaders\core\` and in the `rendertype_armor_cutout_no_cull.fsh` file adjust line 6 (TEX_RES).

```
#define TEX_RES 16
```

#### Layer Overlays

You must always have a leather_layer_1_overlay.png and leather_layer_2_overlay.png file, and both must remain completely transparent at all times, otherwise you will encounter errors.

## Creating Custom Armor
### Step 1. Creating Your Armor Layer Files

First, you need to understand that the layer 1 and layer 2 of your armor will be separated into two different textures. You can begin by creating a 32x64 sprite for layer 1 of your armor. Do the same for layer 2.

![leather_armor_layer_1.png](/images/guides/armor/armor-1.jpg)
*leather_armor_layer_1.png*

### Step 2. Assigning a Color ID

Before adding a color ID to your armor set, you will need to add a white (#ffffff) pixel at 0,1; this must be a white pixel at all times.

Note: This white pixel ONLY has to be placed for the very first armor texture; it is not required for every armor texture.

![White pixel placement](/images/guides/armor/armor-2.jpg)
*White pixel is placed at 0,1 on leather_armor_layer_1.png*

Once your white pixel is added, we can assign this armor set with a specific color ID. This will be placed above the white pixel (0,0) and can be set to any color, but if this is your first time setting up custom armors, I recommend setting it to something simple like red (rgb(255,0,0)).

![Color ID assignment](/images/guides/armor/armor-3.jpg)
*Color ID is set to red using a pixel at 0,0 on leather_armor_layer_1.png*

If your armor has no animation or emissivity, you're done! Now do the same for your layer_2 and make sure you use the exact same color for the color ID. Once you have both layers complete, they should look like the examples below. If you do not have animated armor or emissivity, skip to step 5.

![Color ID assignment](/images/guides/armor/armor-3.jpg)![Both layers complete](/images/guides/armor/armor-4.jpg)
*Both leather_armor_layer_1.png and leather_armor_layer_2.png have the same color ID at 0,0 and the same white pixel at 0,1.*

### Step 3. Animation (Optional)

If you have an animated armor set and want to animate it, first you need to do is add as many frames as your armor has below the corresponding armor texture. You will also need to add a "settings pixel" for the animation at (0,1). This pixel contains rgb(amount of frames, speed, interpolation).

The example to the right would allow for the leather overlay pieces to switch color every 'x' ticks that we set in our "settings pixel."

![Animation frames](/images/guides/armor/armor-5.jpg)
*leather_armor_layer_1.png expanded vertically to add animation frames.*

### Step 4. Emissivity (Optional)

If you want to have your armor set, or portions of it, emissive (glow in the dark essentially; similar to glow squids), you will have to create a copy of your armor texture to the right. This will be treated as an emissivity map; the opacity of the pixel will contribute to the emissivity level (black = no emissivity, white = full emissivity).

![Emissivity mapping](/images/guides/armor/armor-6.jpg)
*leather_armor_layer_1.png expanded horizontally with no color ID identifier for the second one. This allows an emissive map to take place.*

Emissivity also works with animated armor textures, just make sure you create an emissivity map for each frame.

### Step 5. Adding Multiple Armor Sets (Optional)

If you want to add multiple armor sets, you can do so by adding them horizontally to the right as shown in the example below. The only thing you must note, you cannot have the same color ID "settings pixel" for multiple armor textures; you will have to have a unique RGB value for each armor texture.

![Multiple armor sets](/images/guides/armor/armor-7.jpg)
*Example of 5 total armor sets.
The armor set with a blue color ID will have an emissive map due to the expanded emissive mapping.*

### Step 6. In-Game Usage

To get your new armor sets in-game we need to utilize the first "settings pixel." This was your color ID "setting pixel" and you will need to copy your RGB values and input them into a "RGB to decimal converter" tool like this. For example below our color ID pixel is red (255,0,0) which will have the decimal value of '16711680.'

Once converted to a decimal value, you can use the following command in-game for each piece of armor:

```
/give @s leather_helmet{display:{color:16711680}}
```

![RGB to decimal conversion](/images/guides/armor/armor-8.jpg)
*Using the color ID in 0,0 we can convert that into a decimal value for use in-game.*