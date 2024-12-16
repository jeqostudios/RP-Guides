## Using Latest.log

To locate your latest.log, check your .minecraft directory inside of the logs folder. Additionally, you can go into your launcher settings and tick the box that says "Open output log when Minecraft starts."

```
📁.minecraft
└── 📁logs
    └── 📑log.latest
```

Don't panic; you may feel intimidated at first by the heaping mess of words in here, but all we need to find and care about is the actual error line(s) and once those are found, they tell us exactly what the issue is.

## Unable to Resolve Texture Reference

```
[Worker-Main-38/WARN]: Unable to resolve texture reference: #missing in minecraft:custom/emerald_sword
```

If a model's texture doesn't load properly, you may find yourself with this error. This might look a little confusing, but all it's saying is that it's unable to find a texture for the specified item and where it's missing from. If we wanted to resolve this error, we would need to make sure we have our emerald sword texture in the "custom" directory.

## Unable to Load Model

```
[Worker-Main-38/WARN]: Unable to load model: 'minecraft:custom/emerald_sword.json' referenced from: minecraft:diamond_sword#inventory: {}
[Worker-Main-38/WARN]: java.io.FileNotFoundException: minecraft:models/custom/emerald_sword.json
```

If a model doesn't load at all, you may find yourself with this error. This is similar to the error above; it's saying that it's unable to load the model in the specified directory and which item it was designated to. To resolve this error, we need to make sure that our emerald sword model is located in the specified directory (minecraft:custom/).

## Incompatible/Out of Date Pack

If your resource pack is unable to be loaded, ensure your pack structure and all the required files are properly placed in your pack.

## Capital Letters in File Names

Lets keep this one short and sweet; capital letters just don't work. Don't use them.

## Invalid Unicode Characters

If your custom unicode textures are appearing as rectangles, they may be too large. Ensure your texture doesn't go over the maximum size for unicode textures, which is 256x256.

## Black & Purple Textures on Client Versions 1.19.3 and Above

This is due to the nature of the 1.19.3 atlas update, which requires an atlas file. This atlas file stiches all the textures within your pack into one flat sprite sheet, allowing your client to load the resource pack quicker. More information and a full guide on atlases can be found [here](https://jeqo.net/guide/atlases).
