# Nbt Recipes

Nbt Crafting v3 requires you to use the `nbtcrafting3:data` recipe type for recipes,
if you want to use the NBT capabilities of Nbt Crafting.
*This also applies to other recipe types introduced by Nbt Crafting.*

It works by specifying a `recipe` object, which contains the normal recipe type and data.

## Supported Features

The features supported are described in the "Nbt Capabilities" section: [ingredients], [remainders] and [results].

[ingredients]: ../../nbt-capabilities/ingredients/ingredients
[remainders]: ../../nbt-capabilities/ingredients/remainders
[results]: ../../nbt-capabilities/results

## Example

```json
{
	"type": "nbtcrafting3:data",
	"recipe": {
		"type": "minecraft:crafting_shapeless",
		"ingredients": [
			{
				"item": "minecraft:stone"
			}
		],
		"result": {
			"item": "minecraft:stone_sword"
		}
	}
}
```
