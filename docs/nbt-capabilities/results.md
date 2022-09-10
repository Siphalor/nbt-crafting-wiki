# Results

!!!warning
	As of Nbt Crafting v3, the features described here are gated behind the [`nbtcrafting3:data` recipe type](../recipe-types/data).
	This means that you have to use this recipe type for all recipes that use the features described here.

Basically every recipe output is allowed to carry a `data` property:

```json
{
	"type": "nbtcrafting3:data",
	"recipe": {
		"type": "crafting_shapeless",
		"ingredients": [
			{
				"item": "minecraft:apple",
			}
		],
		"result": {
			"item": "minecraft:diamond_axe",
			"data": ...
		}
	}
}
```

The data attribute represents the item's NBT tag in JSON.
Before the conversion to NBT data happens the JSON is passed through Nbt Crafting's [JSON Preprocessor](../../json-preprocessor). Additionally [dollars](../dynamic-data/dollars) may be used for more complicated recipes that require processing the data.

It may look like this:

```json
"data": {
	"display": {
		"Name": "{\"text\":\"Battle Axe\"}"
	},
	"Enchantments": [
		{
			"id": "minecraft:sharpness",
			"lvl": 10
		}
	]
}
```
