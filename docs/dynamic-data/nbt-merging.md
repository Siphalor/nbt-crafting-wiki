# Nbt Merging
## Introduction - a brief history
Nbt merging, inheriting or copying, whatever you like to call it, was orignally just a special case of [dollars](../dollars).

It worked really simple: Dollars let you access any kind of data so why not copy it onto [results](../../recipe-parts/results) or [remainders](../recipe-parts/ingredients/remainders)?

This quickly rose the first problem: What would you do if you wanted to copy the whole data? You can't really specify the target for the dollar expression.

The solution was the special `$` key in `data` tags. It is used as a link to the current object:

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

As of version 2 we can also get rid of the additional dollar sign in merge expressions. In fact: I deprecated it.

This worked perfectly fine for quite some time and might still be anything that you need. So if you just want to statically copy some data **then stop here**.

If you're still reading this then that's apparently not enough for you. 

Like you might have noticed, this design has some builtin flaws that don't really hurt in simple scenarios but become an absolute pain in specific cases: Let's talk about this problems:

1. Obviously this system doesn't let you combine the data from multiple sources. You could only ever copy the data from one ingredient.
2. Secondly what about lists? This was the main issue that popped up with this design and the good ol' [issue #14](https://github.com/Siphalor/nbt-crafting/issues/14) accompanied me for quite some time.
3. Based on 2: What if I want to set a value *but only if it's not already present*. Ok you could just create multiple recipes but where's the fun? You could also not use [dollars](../dollars) and write thousands of "simple" nbt recipes but you don't.

So let's get to the solution:

## Multiple sources
The basic principle didn't change we're still using the dollar sign as the key in data tags.

**But** we can now specify a list of dollar expressions. Cool. Problem number one solved. If that's all that you need - I'm happy for you.

!!! note
	Examples needed!

## Merge behavior
Let's list all of the possible behaviors we could have with merging an object `B` into `A` and list them:

| Name        | Description                                                                                          |
| ----------- | ---------------------------------------------------------------------------------------------------- |
| `overwrite` | In the first scenario we want to replace `A`'s value with the one from `B` no matter what happens.   |
| `keep`      | The exact opposite: `A`'s value takes precedence if it is present. Otherwise use `B`'s.              |
| `merge`     | The default one: `overwrite` for normal values but proceed merging for anything nested.              |
| `update`    | This will only change `A` if there's a value already present. Otherwise do nothing.                  |

For lists we have one more entry:

| Name        | Description                                                                                          |
| ----------- | ---------------------------------------------------------------------------------------------------- |
| `append`    | This will put the value from `B` at the end of list `A`.                                             |

## Granularly specifying merge behavior
Like we learned in the previous section there are a lot of different ways two "merge" two JSON/NBT values.

Now I'm introducing a lot of power to you because you can use them all on different portions of one tag.

Instead of using a "simple" dollar expression for merging, you can also specify an object with the dollar expression specified in the `value` field.

In the optional `paths` object you can specify the merge behavior for as many paths as you want.

### Excursus: JSON Paths
To understand how this works you need to know what JSON paths are. I don't want to go into detail here but they're basically a way to specify a path through some JSON to the value you want. You note down every key you encounter separated by a dot.

```json
{
	"bla": {
		"bla": {
			"test": 123
		}
	}
}
```

The path to `123` would be `bla.bla.test`.

If you encounter lists you note down the index you choose in square brackets (`[index]`). If this reminds you of [dollar operators](../dollars#operators) then you're right. In fact the concept of the child access operators is taken from JavaScript.

### Back to the topic
Nbt Craftings system goes through all of the elements of the JSON data that should be merged in. For each of these elements it builds the JSON path (see above). And evaluates it against the `paths` object. 

The `paths` object specifies paths as its keys and the corresponding [merge behavior](#merge-behavior) as its values.

To allow more complex path notations you can fence your paths in slashes (these things: `/`, lol) and then they *magically* become [regular expressions](https://en.wikipedia.org/wiki/Regular_expression). I'm not gonna explain these things here but [regex101.com](https://regex101.com) is a good place to test them out. Keep in mind to escape all brackets and dots in your path with a double backslash!

An example (untested):
```json
{
	"type": "crafting_shapeless",
	"ingredients": [
		{
			"item": "minecraft:diamond_sword"
		},
		{
			"item": "minecraft:blaze_rod"
		}
	],
	"result": {
		"item": "minecraft:diamond_sword",
		"data": {
			"$": {
				"value": "$i0",
				"paths": {
					"/Enchantments\\[\\d+\\]/": "append"
				}
			},
			"Enchantments": [
				{
					"id": "minecraft:fire_aspect",
					"lvl": 1
				}
			]
		}
	}
}
```

This should let you add the *Fire Aspect* enchantment to diamond swords by combining them with a blaze rod!
