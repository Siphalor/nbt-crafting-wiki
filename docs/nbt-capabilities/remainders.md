# Ingredient Remainders

!!!warning
	As of Nbt Crafting v3, the features described here are gated behind the [`nbtcrafting3:data` recipe type](../recipe-types/data).
	This means that you have to use this recipe type for all recipes that use the features described here.

Recipe remainders are those things which are left in the crafting grid when crafting.

A good example is the vanilla `minecraft:milk_bucket` in the cake recipe: The bucket stays in the grid.

Just add a `remainder` property to your [ingredient's](ingredients) item or tag objects.

It works just like [recipe results](../results) which surely means that you can apply a nbt tag. Additinally [dollars](../dynamic-data/dollars) are supported.

*Disclaimer:* You should only use remainders on single stack items. Otherwise there might be some strange behavior 🙂

## Example

```json
{
	"type": "nbtcrafting3:data",
	"recipe": {
		"type": "crafting_shapeless",
		"ingredients": [
			{
				"item": "minecraft:lava_bucket",
				"remainder": { "item": "minecraft:milk_bucket" }
			},
			{
				"item": "minecraft:water_bucket",
				"remainder": { "item": "minecraft:iron_ingot" }
			}
		],
		"result": {
			"item": "minecraft:obsidian"
		}
	}
}
```
