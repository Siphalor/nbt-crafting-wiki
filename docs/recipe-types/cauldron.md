# Cauldron Recipes
## About

Nbt Crafting also introduces cauldron recipes. Cauldron brewing means right-clicking a cauldron with an item stack which then optionally consumes a bit of water and grants the player a resulting stack. You can also define a [remainder].

## The JSON
Cauldron recipes use the `nbtcrafting:cauldron` recipe type.

They use an [ingredient] as `input` and a [`result`][result] for the item processing. The water consuming is handled through the `levels` property which is a number specifying how many levels to consume.

### Fluids
Beginning from snapshot 20w45a vanilla Minecraft now supports different fluids in cauldrons (namely water and lava).

This extends the matching algorithm of these recipes by the `fluid` property. This property contains a string with the id of the fluid (`minecraft:water`, `minecraft:lava`, `minecraft:air`). If fluid `levels` are set then water will be assumed as default. If no `levels` are specified the default will be matching *anything in the cauldron*.

Since lava can only contain one bucket but no split parts from that, the whole lava will be taken when the `levels` are greater than zero.

[ingredient]: ../../nbt-capabilities/ingredients/ingredients
[remainder]: ../../nbt-capabilities/ingredients/remainders
[result]: ../../nbt-capabilities/results

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
