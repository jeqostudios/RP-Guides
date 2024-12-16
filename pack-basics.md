## Resource Pack Structure
The three main components of a resource pack are the assets folder, `pack.mcmeta`, and `pack.png`. The general file structure of your pack will look like this example.

```
📁resource_pack
├── 📁assets
├── 📑pack.mcmeta
└── 📑pack.png
```

## Pack.mcmeta
In order for Minecraft to be able to identify that a folder is a resource pack is by adding a `pack.mcmeta` file. This file will always be required.

```json
{
      "pack": {
          "pack_format": 18,
          "description": "Tutorial Resource Pack"
     }
}
```

| Field | Description |
|-------|-------------|
| pack_format | Tells Minecraft which version our pack is designed for. For the newer versions, '9' is 1.19.x, '8' is 1.18.x, and '7' is 1.17.x. |
| description | What is displayed when viewing the pack in-game under the resource packs menu. |

| Pack Format Value | Versions | Releases |
|------------------|----------|-----------|
| 6 | 1.16.2-rc1-1.16.5 | 1.16.2-1.16.5 |
| 7 | 20w45a-21w38a | 1.17-1.17.1 |
| 8 | 21w39a-21w38a | 1.18-1.18-2 |
| 9 | 22w11a-1.19.2 | 1.19-1.19.2 |
| 11 | 22w42a | - |
| 12 | 22w45a-23w07a | 1.19.3 |
| 13 | 1.19.4-pre1-23w13a | 1.19.4 |
| 14 | 23w14a-23w16a | - |
| 15 | 23w17a-1.20.1 | 1.20-1.20.1 |
| 16 | 23w31a | - |
| 17 | 23w32a-1.20.2-pre1 | - |
| 18 | 1.20.2-pre2 | 1.20.2 |

## Pack.png
This is your pack's icon. If no icon is provided, Minecraft will generate a fancy cobblestone for you.

The only rule here is that the file must be a PNG, and for best results utilize a the space you can with a 128x128 icon!

## Adding Namespaces
First, you're probably asking when is a good time to create a new namespace? The answer depends on how complex your project is or becomes, but for best practice you should always have one new namespace in a resource pack.

To add a new namespace to our pack, we simply create two new folders with identical names in each of the "models" and "textures" folder. In this example, we are creating a new namespace named "custom." This can be replaced with your username, server name, or whatever you'd like.

```
📁resource_pack
├── 📁assets
│    └── 📁minecraft
│        ├── 📁models
│        │    └── 📁custom
│        └── 📁textures
│            └── 📁custom
├── 📑pack.mcmeta
└── 📑pack.png
```
