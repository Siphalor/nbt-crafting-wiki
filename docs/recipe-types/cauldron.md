## About

Nbt Crafting also introduces cauldron recipes. Cauldron brewing works as right-clicking a cauldron with an item stack which then optionally consumes a bit of water and grants the player a resulting stack.

## The JSON
Cauldron recipes use the `nbtcrafting:cauldron` recipe type.

They use an [ingredient] as `input` and a [`result`][result] for the item processing. The water consuming is handled through the `levels` property which is a number specifying how many levels to consume.

[ingredient]: ../../recipe-parts/ingredients/ingredients
[result]: ../../recipe-parts/results

## Example
```json
{
	"type": "nbtcrafting:cauldron",
	"input": {
		"item": "minecraft:sand"
	},
	"result": {
		"item": "minecraft:clay"
	},
	"levels": 1
}
```
