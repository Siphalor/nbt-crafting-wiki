# Dollars

!!!warning
	As of Nbt Crafting v3, the features described here are gated behind the [`nbtcrafting3:data` recipe type](../recipe-types/data).
	This means that you have to use this recipe type for all recipes that use the features described here.

Dollars are a technology which allows you to use simple mathematical expressions when applying data.

## Introduction
In your [recipe output's](../../results) and [recipe remainder's](../../remainders) data objects you may use dollar notation on every property. 

Dollars are noted as string values on your desired attributes:

```json
"data": {
	"Damage": "$ ...",
	"other": "normal value"
}
```

A dollar is a mathematical expression with `+`, `-`, `*` and `/` operators as well as parentheses supported.

## Data Types
Since version 2.0 Dollars are data type aware.

Existing data types are:

- **String literals** are text values like `"test"`{.json} (with quotes) or `'abc'`{.json} (with apostrophes).
- **Numeric values**:
	- *Integral values*: whole numbers. Nbt Crafting will choose the **integer** type by default
		- **Byte** - holds integral values from 0 to 255
		- **Short** - holds integral values from ca. -32k to 32k
		- **Integer** - holds integral values from -2 billion to 2 billion
		- **Long** - holds bigger integral value
	- *Floating point numbers*: numbers with decimal positions. Nbt Crafting will choose the **double** type by default
		- **Float** - has fewer decimal positions
		- **Double** - is more precise
- **Booleans**: Can have two states - `true`{.json} or `false`{.json}; Note that these get converted to **bytes** for nbt data.
- **Lists**: collection of values - Even if JSON allows different data types, nbt will crash when a mixture of data types is present in a list. Uses square brackets (`[]`) in JSON.
- **Compounds**: Also called objects, maps or dictionaries in other languages. These contain "key" -> value pairs of data. Uses curly braces (`{}`) and colons (`:`).
- **Itemstacks**: Are mainly used in [functions](#functions), when using child access they are converted into their NBT data

!!! warning
	Be careful when dividing numbers in dollars. `5 / 2` would normally resolve to `2` because whole number division would be used. `5.0 / 2` would instead to resolve to the possibly wanted `2.5`.

## References
A key feature of dollars is referencing the nbt data of [ingredients](../../ingredients). This can be done by referencing the ingredient with it's _id_. The _id_ depends on the type of the recipe - a lot of the recipe types use `base` and `ingredient` for the respective ingredients. Shaped and shapeless recipes are a notable exception to this (As they have more than two ingredients, lol).

A full list of all reference ids for the recipe types can be found [here](../dollar-references).

## Operators

### Overview

All operators, ordered by precedence:

| Operator                | Description                                     | Example                              |
|-------------------------|-------------------------------------------------|--------------------------------------|
| `.` and `.?`            | [Compound child access](#compound-child-access) | `base.Damage`                        |
| `[0]`                   | [List element access](#list-element-access)     | `list[0]`                            |
| `#`                     | [Type casting](#type-casting)                   | `(5.0/2.0)#i`=2                      |
| `-` (unary)             | Negates the value                               | `-5`=-5                              |
| `+` (unary)             | Casts to number (same as `#n`)                  | `+"5"`=5                             |
| `!` (unary)             | Casts to boolean and inverts                    | `!true`=false                        |
| `/`                     | [Division](#arithmetic-operators)               | `7/2.0`=3.5                          |
| `*`                     | [Multiplication](#arithmetic-operators)         | `2*3`=6                              |
| `-`                     | [Subtraction](#arithmetic-operators)            | `2-3`=-1                             |
| `+`                     | [Addition](#arithmetic-operators)               | `2+3`=5                              |
| `==` and `!=`           | [Equality](#equality)                           | `5 == 5`, `3 != 5`                   |
| `<`, `<=`, `>` and `>=` | [Comparison](#comparison)                       | `5 < 6`, `5 <= 5`, `6 > 5`, `5 >= 5` |
| `&&`                    | Logical AND                                     | `true && false`                      |
| `||`                    | Logical OR                                      | `true || false`                      |
| `?`...`:`               | [Conditions](#conditions)                       | `1?"true":"false"`="true"            |

### Compound child access
Used to access a value with a known name. Also see the similar [list access operator](#list-element-access).

Based on the following nbt you could use `bla.bla.test` to access the value `123`:

```json
{
	"bla": {
		"bla": {
			"test": 123
		}
	}
}
```

The default operator (`.`) will throw an error if the left side is not a compound.
The coalescing operator (`.?`) will return `null` if the left side is not a compound.

Performing element access on a stack will resolve to the element on the stack's NBT data.

### List element access
Like [compound child operators](#compound-child-access) you can use square brackets to access anything in a list/object.

The typical usage is to provide a number (e.g. `[1]`) to access the elements of a list. In the following nbt you could access the string `"giraffe"` using the dollar expression `animals[0].name`:

```json
{
	"animals": [
		{ "name": "dog", "sound": "woof" },
		{ "name": "giraffe", "sound": "slurp" },
		{ "name": "pig", "sound": "oink" }
	]
}
```

You can also give it a string or even pump in an expression that evaluates to a string to access properties like with the [list access operator](#list-element-access). The important difference is that with this operator you can dynamically access values where-as the `.`-operator is based on a hard name.

Performing element access on a stack will resolve to the element on the stack's NBT data.

### Type casting

Used to convert between data types.

Usage is like `<value>#<type-id>` where `<type-id>` is one of the following:

- `b`, `B`, `c` or `C` for bytes
- `s` or `S` for shorts
- `i` or `I` for integers
- `l` or `L` for longs
- `f` or `F` for floats
- `d` or `D` for doubles
- `n` to cast to any number
- `o` for booleans
- `a` for strings

Cut decimals of number:

`(5.0 / 2.0)#i`

Convert number to string:

`(5.0)#a`

### Arithmetic operators
There is not too much to say about arithmetic operators with numbers. They basically work as you would expect. One thing to know is that concerning [data types](#data-types), they'll always chose the biggest data type provided to the operator (`3 + 4.0` = `7.0`).

Where it gets interesting is using arithmetic operators for string operations:

- `+`: Will concatenate a string with any given value
- `*`: If the second operator is a number, this operator will repeat the first string that number of times.

### Equality
When checking for equality, the following rules apply:

- Compounds must match exactly
- Lists must match exactly (order matters)
- Numbers must be equal, there is no type checking
- Anything else must match exactly

### Comparison
When comparing values, both values must be numeric.

### Conditions
Like in many programming languages, dollars support the well known and loved ternary operator.

The ternary operator, or condition operator, consists of two symbols and three expression around them.

```
A ? B : C
```

It basically checks whether `A` is `true` or anything near true (mostly anything that isn't zero or empty). Based on that the whole expression evaluates either to `B` or `C`.

## Dollar functions
There is a selection of predefined functions that can be used in dollar expressions.
There is also support for defining anonymous functions using lambdas.
These features are documented [on their own page](dollar-functions.md).

## Nbt merging/inheriting
This part was former part of this page but because I largely expanded it I decided to give it it's own page. See [Nbt merging](../nbt-merging).

## Dynamic stack count
See [experimental features](../../../experimental).

## Example
The following provides a way of slowly converting a wooden sword to sticks via dollars and [recipe remainders](../../remainders).

```json
{
	"type": "nbtcrafting3:data",
	"recipe": {
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
}
```
