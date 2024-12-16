## Creating a Furniture Item

### Step 1. Setting the Model Display
The first thing you want to do is to setup your furniture's display via item frame. Do this this, you can open your model in Blockbech and go to the display tab (top right) and select the item frame display.

In this display, you can adjust the values to your liking or based on your model's proportions.

You can attempt to copy the settings of my wood chair, but there are no promises they will work for you.

### Step 2. Adding Your Model
Once your model and the display values are all good to go, you can add it to your pack. First, you'll need to export your model; to do so, go to File > Export > Export Block/Item Model, and save your model's `json` and `PNG` somewhere convienent.

Now you need to implement the model's `json` and `png` into your pack. In this example below I'm using very simple namespaces, however, feel free to implement however you'd like. Simply add the `json` into the models directory and the `png` into the textures directory. A full guide on implementing custom items can be found here.

```
📁assets
└── 📁minecraft
    └── 📁models
        └── 📁custom
            └── 📑wooden_chair.json
```

```
📁assets
└── 📁minecraft
    └── 📁textures
        └── 📁custom
            └── 📑wooden_chair.png
```

Now, as usual, create a new predicate under any base item of your choice.

```json
{
    "parent": "item/generated",
    "textures": {
        "layer0": "item/paper"
    },
    "overrides": [{
        "predicate": {
            "custom_model_data": 1
        },
        "model": "custom/wooden_chair"
    }]
}
```

### Step 3. Using the Model In-Game
If you require a hitbox, light source, or seats, you will need to use MythicCrucible; skip to step 4.

To place your model, you will need invisible item frames. Use the commands below to get an item frame as well as your custom model. Place down the item frame and pop your model into it!

`/give @p item_frame{EntityTag:{Invisible:1b}}`

`/give @p paper{CustomModelData:1}`

### Step 4. MythicCrucible (Optional)
MythicCrucible offers many furniture related features such as seats, hitboxes, and light sources. To get started, make sure you have [MythicCrucible](https://mythiccraft.io/index.php?resources/crucible-create-unbelievable-mythic-items.2/) and [MythicMobs](https://mythiccraft.io/index.php?resources/mythicmobs.1/).

`You will need to create a new .yml` file in 'MythicMobs/Packs/Custom/Items/' and you can use the following template on the right for each new furniture model you have. Make sure your material ID and model values match what you have when you setup your model predicate (step 2).

| Type | Must always be furniture for furniture models. |
|------|---------------------------------------------|
| Drops | The item that will be dropped when a player breaks the furniture. |
| Barriers | Where barriers will be placed to form a hitbox. |
| Seats | Where "seats" will be added, allowing players to sit. |
| Lights | Where light sources will be added; useful for torches, lamps, etc |
| Furniture Skills | Where you can add mechanics for certain events, such as when the furniture is placed, broken, damaged, etc. More mechanics can be found here. |

The values for barriers, seats, and lights are x, y, z. The fourth value for 'lights' is the light intensity and only 'seats' can be adjusted by decimal values.

```yaml
wood_chair:
    Id: PAPER
    Model: 1
    Display: 'Wood Chair'
    Type: FURNITURE
    Furniture:
        Material: PAPER
        Model: 1
        Drops:
            - wood_chair
        Barriers:
            - 0,0,0
        Seats:
            - 0,0,0
        Lights:
            - 0,0,0 15
    FurnitureSkills:
        - sound{s=entity.chicken.egg} @self ~onBlockPlace
        - sound{s=entity.zombie.attack_wooden_door} @self ~onBlockBreak
        - sound{s=entity.zombie.attack_wooden_door} @self ~onDamaged
```

Your furniture model has been implemented via MythicCrucible! Use the following command to receive your furniture.

`/mm i get <furniture_name>`
