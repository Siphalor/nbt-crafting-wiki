# Results
Basically every recipe output has an additional `data` property:

```json
{
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
```

The data attribute represents the items nbt tag in JSON. Before the conversion to nbt data happens the JSON is passed through Nbt Crafting's [JSON Preprocessor](../../utilities#json-preprocessor). Additionally [dollars](../../dynamic-data/dollars) may be used for more complicated recipes that require processing the data.

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
