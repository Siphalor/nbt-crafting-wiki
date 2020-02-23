# Welcome to the Nbt Crafting 2.0 wiki!

Nbt Crafting is a mod which finally introduces nbt-related recipes.

[![curseforge downloads](https://cf.way2muchnoise.eu/full_nbt-crafting_downloads.svg){: .x-img-badge }](https://minecraft.curseforge.com/projects/nbt-crafting)
[![curseforge mc versions](https://cf.way2muchnoise.eu/versions/nbt-crafting.svg){: .x-img-badge }](https://minecraft.curseforge.com/projects/nbt-crafting)

---

For detailed information see [recipe results](recipe-parts/ingredients/remainders) and [recipe ingredients](recipe-parts/ingredients/ingredients).

You might also want to add [brewing](recipe-types/brewing), [cauldron](recipe-types/cauldron) or [anvil](recipe-types/anvil) recipes.

Go [here](modders.md) if you're a modder and want to work with Nbt Crafting.

## Example Recipe
Sometimes one Hello-World-ish example is worth a thousand words.

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
