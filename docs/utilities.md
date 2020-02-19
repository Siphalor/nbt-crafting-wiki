# Utilities

## Potions in recipes
Potions are annoying to clarify especially when working with [brewing recipes](../recipe-types/brewing). Therefore Nbt Crafting introduces a special shorthand for it.

You can now use `potion` instead of the `item` key in all ingredients, remainders and results. An example brewing recipe using this feature could look like this:

```json
{
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
```

## Global datapacks
If you're creating a mod pack you're probably want to use your datapacks in all your worlds. The [Cotton](https://minecraft.curseforge.com/projects/cotton) mod provides you with a global datapack directory in your minecraft folder where you can chuck them in.

## Graphical
Due to enabling some nbt rendering in recipe books, they will now also display the amount of items a recipe produces.
