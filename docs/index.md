# Welcome to the Nbt Crafting wiki!
[![curseforge downloads](http://cf.way2muchnoise.eu/full_nbt-crafting_downloads.svg)](https://minecraft.curseforge.com/projects/nbt-crafting)
[![curseforge mc versions](http://cf.way2muchnoise.eu/versions/nbt-crafting.svg)](https://minecraft.curseforge.com/projects/nbt-crafting)

Nbt Crafting is a mod which finally introduces nbt-related recipes.

For detailed information see [recipe results](recipe-parts/ingredients/remainders) and [Recipe Ingredients](recipe-parts/ingredients/ingredients).

You might also want to add [brewing](recipe-types/brewing), [cauldron](recipe-types/cauldron) or [anvil](recipe-types/anvil) recipes.

This is a quick example:

```json
{
	"type": "crafting_shapeless",
	"ingredients": [
		{
			"item": "minecraft:diamond_sword",
			"data": {
				"require": {
					"Damage": "$..40"
				}
			}
		},
		{ "item": "minecraft:diamond" }
	],
	"result": {
		"item": "minecraft:diamond_axe",
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
	}
}
```
