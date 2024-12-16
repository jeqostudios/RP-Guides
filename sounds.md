## Implementing a New Sound

### Step 1. Adding your OGG File
If you want to add new sounds or music, you will need a `.ogg` file. You can use any software or a converter online to take care of this if you have a `.mp3` file.

All you need to do is put your `.ogg` file in a sounds folder inside of the minecraft directory.

```makefile
📁resource_pack
└── 📁assets
    └── 📁minecraft
        └── 📁sounds
            └── 📁custom
                └── 📑arcade_music.ogg
```

### Step 2. Reading New Sounds
Once your `.ogg` file is in your pack, you need to make sure the pack is able to read the file. For this you will need to create a sounds.json file and place it inside of your minecraft directory.

```makefile
📁resource_pack
└── 📁assets
    └── 📁minecraft
        └── 📑sounds.json
```

Inside of your `sounds.json` you will create something like this:

```json
{
    "custom.arcade_music": {
        "sounds": [
            "custom/arcade_music"
        ]
    }
}
```

#### Breakdown
| Field | Description |
|-------|-------------|
| custom.arcade_music | The name of your sound that will display in-game. This could also be, for example, just "arcade_music" without the "custom." prefix. |
| sounds | The files for this sound. |
| custom/arcade_music | The path of our .ogg sound file. |

### Step 3. Result
Your sound is now implemented and ready to use in-game. To play your sound, use the following command:

`/playsound minecraft:custom.arcade_music master @p`

You can replace the "minecraft:custom.arcade_music" portion with whatever you specified for your sound name in the `sounds.json`.
