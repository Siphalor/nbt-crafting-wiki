# Ingredients
## Basic Usage

The `data` property of each ingredient splits into a `require` and a `deny` section.

Like the [results](../../results), these are JSON objects representing the NBT tag of the item.

All properties with their values referenced in `require` **must** be present with the exact values on the item.

All properties and values referenced in `deny` **must not** be present on the item.

There's also a `remainder` property which is described [here](../remainders).

Example:

``` json
{
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
```
This would require a diamond sword with damage 2 but which seams to be unhappy 😢

## Advanced usage

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
