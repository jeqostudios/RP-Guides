# Custom Items

This guide will help you create custom items in your resource pack.

## Creating a Custom Item

### Step 1. Adding Texture and Model Files

Note: Depending on if you are using a generated model or not, the steps may vary.

If you want to use a generated model, you will need to create a new JSON file named "<item>.json" with the following.

If you will be using your item's custom model, disregard the previous. With custom models, we will be letting Blockbench handle our JSON files.

```json
{
  "parent": "item/handheld",
  "textures": {
    "layer0": "custom/item/emerald_sword"
  }
}
```

As opposed to having to create a new JSON file for each item, we can generate one with a few clicks. Load up Blockbench and open up your item. Head to 'File > Export > Export Block/Item Model'.

Once we have our texture and model files, we can implement them into our resource pack. Make sure to add the item's model file into the model directory and the texture file into the texture directory of your namespace.

```
📁resource_pack
└── 📁assets
    └── 📁minecraft
        └── 📁textures
            └── 📁custom
                └── 📑emerald_sword.png
```

```
📁resource_pack
└── 📁assets
    └── 📁minecraft
        └── 📁models
            └── 📁custom
                └── 📑emerald_sword.json
```

The first, your item's `json` in the models directory, and on the right, your item's texture `png` in the textures directory; both should be in the namespace (in our example, custom), and both files should have the exact same name.

### Step 2. Creating a Predicate

Once you have implemented your model and texture, you will need to create a new predicate on any item of your choice; this will allow us to get the item with a specified custom model data value that shows our custom item.

Note: Base items will ALWAYS go in '/assets/minecraft/models/item/'

To create a new predicate, you will need to create a new item model; for this example we will create a custom emerald sword and use the diamond sword base model.

```json
{
  "parent":"item/generated",
  "textures":{
    "layer0":"item/diamond_sword"
  },
  "overrides": [
    {"predicate":{"custom_model_data":1},"model":"custom/weapons/emerald_sword"}
  ]
}
```

#### Breakdown

| Field | Description |
|-------|-------------|
| custom_model_data | Which custom model data value to use for the model. |
| model | The path route to your model's .json file. The base of "model" will always be the default 'assets/minecraft/models/' directory. |

### Step 3. Result

You have completed implementing a custom item. You can finally launch up Minecraft to go in-game and test it out for yourself.

Once you're in-game you can use the command below to give yourself your custom item. Make sure to use the correct custom model data value that you specified in your base model.

`/give minecraft:diamond_sword{CustomModelData:1}`