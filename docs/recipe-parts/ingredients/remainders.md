# Ingredient Remainders
Recipe remainders are those things which are left in the crafting grid when crafting.

A good example is the vanilla `minecraft:milk_bucket` in the cake recipe: The bucket stays in the grid.

Just add a `remainder` property to your [ingredient's](../ingredients) item or tag objects.

It works just like [recipe results](../../results) which surely means that you can apply a nbt tag. Additinally [Dollars](../../../dynamic-data/dollars) are supported.

*Disclaimer:* You should only use remainders on single stack items. Otherwise there might be some strange behavior 🙂

## Example

```json
{
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
```
