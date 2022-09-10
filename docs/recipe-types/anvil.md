# Anvil Recipes
## About
Nbt Crafting gives you the *magical* ability to forge items to a different result in anvils.

!!! warning
	[Remainders](../../nbt-capabilities/ingredients/remainders) are not supported!
	
	Also the recipe will consume whole stacks of items instead of just taking one of it.

## The JSON
Anvil recipes are of the type `nbtcrafting3:anvil`. They have a `base` [ingredient] \(the left slot in the GUI) and an `ingredient` [ingredient] which is the "modifier" for the base stack.
The [result] is defined in the `result` object.

There is also an optional `levels` property defining the amount of experience levels the forging process costs the player.

[ingredient]: ../../nbt-capabilities/ingredients/ingredients
[result]: ../../nbt-capabilities/results

## Example
```json
{
	"type": "nbtcrafting3:anvil",
	"base": {
		"item": "minecraft:stone_sword"
	},
	"ingredient": {
		"item": "minecraft:cyan_dye"
	},
	"result": {
		"item": "minecraft:diamond_sword"
	},
	"levels": 10
}
```
