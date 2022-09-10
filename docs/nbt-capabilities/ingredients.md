# Ingredients

!!!warning
	As of Nbt Crafting v3, the features described here are gated behind the [`nbtcrafting3:data` recipe type](../recipe-types/data).
	This means that you have to use this recipe type for all recipes that use the features described here.

## Basic Usage

The `data` property of each ingredient splits into a `require` and a `deny` section.

Like the [results](../results), these are JSON objects representing the NBT tag of the item. As always the json data is passed through the [JSON Preprocessor](../../json-preprocessor).

All properties with their values referenced in `require` **must** be present with the exact values on the item.

All properties and values referenced in `deny` **must not** be present on the item.

There's also a `remainder` property which is described [here](../remainders).

Example:

``` json
{
	"type": "nbtcrafting3:data",
	"recipe": {
		"type": "crafting_shapeless",
		"ingredients": [
			{
				"item": "minecraft:diamond_sword",
				"data": {
					"require": {
						"Damage": 2
					},
					"deny": {
						"happy": "yes"
					}
				}
			}
		],
		...
	}
}
```
This would require a diamond sword with damage 2 which seams to be unhappy 😢

## Advanced Matching

### Wildcards

If you use an empty string (`""`) as a value this is a wildcard and will match all possible values.
So this means requiring/denying will match if the given property even exists.

### Number ranges
If you want to apply a recipe if a numeric nbt value is in a specific range, you can do this by using a value of the form `"$a..b"`. Where a is the lower value and b the upper value. You can leave out either of it if you'd like to use infinity at its position.

Example:
```json
"require": {
	"Damage": "$..40"
}
```
This will match all items with a `Damage` value of 40 or less.

## Potions
Potions are annoying to clarify especially when working with [brewing recipes](../../recipe-types/brewing). Therefore Nbt Crafting introduces a special shorthand for it.

You can now use `potion` instead of the `item` key in all ingredients, remainders and results. An example brewing recipe using this feature could look like this:

```json
{
	"type": "nbtcrafting3:data",
	"recipe": {
		"type": "nbtcrafting:brewing",
		"base": {
			"potion": "minecraft:regeneration"
		},
		"ingredient": {
			"item": "minecraft:stick"	
		},
		"result": {
			"potion": "minecraft:swiftness"
		}
	}
}
```
