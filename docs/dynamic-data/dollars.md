# Dollars
Dollars are a technology which allows you to use simple mathematical expressions when applying data.

## Usage
In your [recipe output's](../../recipe-parts/results) and [recipe remainder's](../../recipe-parts/ingredients/remainders) data objects you may use dollar notation on every property which is not (recursively) contained in a list.

Dollars are noted as string values on your desired attributes:

```json
"data": {
	"Damage": "$ ...",
	"other": "normal value"
}
```

A dollar is a mathemathical expression with `+`, `-`, `*` and `/` operators as well as parentheses supported.
_**Operator precedence is not supported yet.**_

```json
"data": {
	"Damage": "$ 3 + 5",
	"other": "normal value"
}
```

You can refer to nbt data of items used in the recipe by using path notation.

### Path Notation
Path notation is used to pull data from used items roughly equal to json path notation.

The parent element is an identifier which item to use.

* Crafting recipes use the `iX` notation where `X` is a number beginning at `i0`. For shaped recipes the number refers to the crafting grid used in `pattern`. For shapeless recipes the number refers to the position of the ingredient in the `ingredients` list.
* Other recipe types just use `this` to refer to the current ingredient. Referencing other ingredients is not possible for these recipes.

### Nbt merging/inheriting
You can also merge/copy nbt data from existing items.

Therefore specify a string with the `$` key in the result's data object and use the desired path.
These dollar keys will always target the nbt object that they are defined in.

#### Example
This will add a recipe to modify a diamond_sword with a diamond but keep the name and the damage of the original sword.

```json
{
	"type": "crafting_shapeless",
	"ingredients": [
		{
			"item": "minecraft:diamond"
		},
		{
			"item": "minecraft:diamond_sword"
		}
	],
	"result": {
		"item": "minecraft:diamond_sword",
		"data": {
			"$": "$ i1",
			"some_custom_tag": true
		}
	}
}
```

### Example
The following provides a way of slowly converting a wooden sword to sticks:

```json
{
	"type": "crafting_shapeless",
	"ingredients": [
		{
			"item": "minecraft:wooden_sword",
			"remainder": {
				"item": "minecraft:wooden_sword",
				"data": {
					"Damage": "$ i0.Damage + 2"
				}
			}
		}
	],
	"result": { "item": "minecraft:stick" }
}
```
