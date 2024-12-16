## Information

### Default Translation Files
Below you can download a specific version's `en_us.json` file. For use in a pack, remove the version number from the beginning of the file name (`1.19_en_us.json` -> `en_us.json`).

[1.19](https://jeqo.net/files/mc_jsons/1.19_en_us.json) - [1.19.1](https://jeqo.net/files/mc_jsons/1.19.1_en_us.json) - [1.19.2](https://jeqo.net/files/mc_jsons/1.19.2_en_us.json) - [1.19.3](https://jeqo.net/files/mc_jsons/1.19.3_en_us.json)  
[1.18](https://jeqo.net/files/mc_jsons/1.18_en_us.json) - [1.18.1](https://jeqo.net/files/mc_jsons/1.18.1_en_us.json) - [1.18.2](https://jeqo.net/files/mc_jsons/1.18.2_en_us.json)  
[1.17](https://jeqo.net/files/mc_jsons/1.17_en_us.json) - [1.17.1](https://jeqo.net/files/mc_jsons/1.17.1_en_us.json)  
[1.16](https://jeqo.net/files/mc_jsons/1.16_en_us.json) - [1.16.1](https://jeqo.net/files/mc_jsons/1.16.1_en_us.json) - [1.16.2](https://jeqo.net/files/mc_jsons/1.16.2_en_us.json) - [1.16.3](https://jeqo.net/files/mc_jsons/1.16.3_en_us.json) - [1.16.4](https://jeqo.net/files/mc_jsons/1.16.4_en_us.json) - [1.16.5](https://jeqo.net/files/mc_jsons/1.16.5_en_us.json)

## Creating a New Translation File

### Step 1. Adding a Translation File
For each language, a translation file is used. Luckily, you can just focus on one translation file and then duplicate it and rename each to however many other languages you wish. In this guide, we will be covering the main English translation file, `en_us.json`.

Inside of `/assets/minecraft/lang/` you will need to create a new file named `en_us.json`.

```makefile
📁resource_pack
└── 📁assets
    └── 📁minecraft
        └── 📁lang
            └── 📑en_us.json
```

### Step 2. Defining Translations
There are thousands of translations available for each version. These can be found by extracting them from their respective version jar; the latest versions can be found at the top of the page under "Default Translation Files."

Each translation will be on its own line with an entry and its value, like below.

```json
{
    "language.name": "English"
}
```
*En_us.json with a single value.*

To add multiple translation entries, simply add a trailing comma to the previous entry. Note, do not add a comma after the last entry or your file will break!

```json
{
    "language.name": "English",
    "language.region": "United States",
    "language.code": "en_us"
}
```
*En_us.json with multiple values.*

## Customizing Sound Subtitles
If you've ever come across a custom sound, it appears as its raw name in the subtitles. Translations can help in that case!