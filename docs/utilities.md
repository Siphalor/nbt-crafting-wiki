# Utilities

## Global datapacks
If you're creating a mod pack you're probably want to use your datapacks in all your worlds. The [Cotton](https://minecraft.curseforge.com/projects/cotton) mod provides you with a global datapack directory in your minecraft folder where you can chuck them in.

## Json Preprocessor
Before the JSON data that you specify in [ingredients], [remainders] or [results] gets converted to nbt data, Nbt Crafting applies the JSON Preprocessor to it. This helps with a couple of scenarios which are ugly to write or hard to convert without additional information:

### Stringification
Minecraft's handling of texts for example in item names is often a bit annoying as you have to specify the text as JSON converted and escaped to text. This is how this usually looks:

```json
"display": {
	"Name": "[{\"text\":\"Silky \",\"italic\":true},{\"text\":\"Pick\",\"color\":\"blue\"}]"
}
```

Nbt Crafting grants you the ability to write this part of the data as normal json and let this mod handle the conversion:

```json
"display": {
	"Name": [
		{ "text": "Silky ", "italic": true },
		{ "text": "Pick", "color": "blue" },
		"nbtcrafting:stringify"
	]
}
```

You can do the same for JSON Objects. You then use `"nbtcrafting:stringify"` as key and use `true` as the value:

```json
"display": {
	"Name": {
		"text": "Neither Gold Nore or!",
		"nbtcrafting:stringify": true
	}
}
```

### Array types
Another problem is that in contrast to NBT, JSON doesn't know explicit types for arrays. When generating your nbt data with some online tools you might see arrays like this: `[I;1,2,3,4]`; which would specify an integer array.

In a lot of cases you will not need to do anything as Minecraft often doesn't really care about the type of the arrays and the implicit conversion works correct in a lot of the cases.

If you still need to explicitly (attribute modifiers need this I was told), there's a way to do this with Nbt Crafting:

```json
"some_value": [
	1,
	2,
	3,
	4,
	"nbtcrafting:array_type=i"
]
```

In the place of the `i` you can specify the type with the same characters as when performing [type casting in dollars](../dynamic-data/dollars#type-casting).

## Graphical
Due to enabling the display of NBT data in recipe books, there will also be displayed the number of outputs a recipe produces.

[ingredients]: ../recipe-parts/ingredients/ingredients
[remainders]: ../recipe-parts/ingredients/remainders
[results]: ../recipe-parts/results

