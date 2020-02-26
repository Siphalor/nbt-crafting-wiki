# Brewing Recipes
## About
With this mod you can also add brewing recipes.

## The JSON
The three lower slots which are usually bottles are defined with the `base` [ingredient].

The top slot which provides the modifier or ingredient item is set through the [`ingredient`][ingredient].

The resulting potion/anything-that-you-want is defined through the [`result`][result].
`result` is just the output stack.

[Dollars](../../dynamic-data/dollars) are supported with the following entries:
- `ingredient`: is the ingredient's data
- `base`: is the data of the current base slot

If you're annoyed of typing out potion stacks in your brewing recipe you might wanna look at [this feature](../../utilities#potions-in-recipes).

[ingredient]: ../../recipe-parts/ingredients/ingredients
[result]: ../../recipe-parts/results

## Example
```json
{
	"type": "nbtcrafting:brewing",
	"base": {
		"item": "minecraft:stone"
	},
	"ingredient": {
		"item": "minecraft:stick"	
	},
	"result": {
		"item": "minecraft:player_head",
		"data": {
			"display": {
				"Name": "nametaginput"
			},
			"SkullOwner": "Siphalor"
		}
	}
}
```
Brew sticks into cobblestone to get some cool playerheads :P
