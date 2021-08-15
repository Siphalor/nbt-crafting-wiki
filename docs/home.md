# Welcome to the Nbt Crafting 2.0 wiki!

Nbt Crafting is a mod which finally introduces nbt-related recipes.

[![curseforge downloads](https://cf.way2muchnoise.eu/full_nbt-crafting_downloads.svg){: .x-img-badge }](https://minecraft.curseforge.com/projects/nbt-crafting)
[![modrinth downloads](https://img.shields.io/badge/dynamic/json?color=5da545&label=modrinth&prefix=downloads%20&query=downloads&url=https://api.modrinth.com/api/v1/mod/18ztUZP5&style=flat&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAxMSAxMSIgd2lkdGg9IjE0LjY2NyIgaGVpZ2h0PSIxNC42NjciICB4bWxuczp2PSJodHRwczovL3ZlY3RhLmlvL25hbm8iPjxkZWZzPjxjbGlwUGF0aCBpZD0iQSI+PHBhdGggZD0iTTAgMGgxMXYxMUgweiIvPjwvY2xpcFBhdGg+PC9kZWZzPjxnIGNsaXAtcGF0aD0idXJsKCNBKSI+PHBhdGggZD0iTTEuMzA5IDcuODU3YTQuNjQgNC42NCAwIDAgMS0uNDYxLTEuMDYzSDBDLjU5MSA5LjIwNiAyLjc5NiAxMSA1LjQyMiAxMWMxLjk4MSAwIDMuNzIyLTEuMDIgNC43MTEtMi41NTZoMGwtLjc1LS4zNDVjLS44NTQgMS4yNjEtMi4zMSAyLjA5Mi0zLjk2MSAyLjA5MmE0Ljc4IDQuNzggMCAwIDEtMy4wMDUtMS4wNTVsMS44MDktMS40NzQuOTg0Ljg0NyAxLjkwNS0xLjAwM0w4LjE3NCA1LjgybC0uMzg0LS43ODYtMS4xMTYuNjM1LS41MTYuNjk0LS42MjYuMjM2LS44NzMtLjM4N2gwbC0uMjEzLS45MS4zNTUtLjU2Ljc4Ny0uMzcuODQ1LS45NTktLjcwMi0uNTEtMS44NzQuNzEzLTEuMzYyIDEuNjUxLjY0NSAxLjA5OC0xLjgzMSAxLjQ5MnptOS42MTQtMS40NEE1LjQ0IDUuNDQgMCAwIDAgMTEgNS41QzExIDIuNDY0IDguNTAxIDAgNS40MjIgMCAyLjc5NiAwIC41OTEgMS43OTQgMCA0LjIwNmguODQ4QzEuNDE5IDIuMjQ1IDMuMjUyLjgwOSA1LjQyMi44MDljMi42MjYgMCA0Ljc1OCAyLjEwMiA0Ljc1OCA0LjY5MSAwIC4xOS0uMDEyLjM3Ni0uMDM0LjU2bC43NzcuMzU3aDB6IiBmaWxsLXJ1bGU9ImV2ZW5vZGQiIGZpbGw9IiM1ZGE0MjYiLz48L2c+PC9zdmc+){: .x-img-badge }](https://modrinth.com/mod/nbt-crafting)
![supported Minecraft versions: 1.15 | 1.16 | 1.17](https://img.shields.io/badge/support%20for%20MC-1.15%20%7C%201.16%20%7C%201.17-%2356AD56){: .x-img-badge }

---

If you want to get started with datapacks and recipes in Minecraft you can check out the [Resources](../tools) site.

For detailed information see [recipe results](../recipe-parts/ingredients/remainders) and [recipe ingredients](../recipe-parts/ingredients/ingredients).

!!! note
	[Click here to see notes about updating to v2](../updating)

You might also want to add [brewing](../recipe-types/brewing), [cauldron](../recipe-types/cauldron) or [anvil](../recipe-types/anvil) recipes.

Go [here](../modders) if you're a modder and want to work with Nbt Crafting.

## Example Recipe
Sometimes one Hello-World-ish example is worth a thousand words.

```json
{
	"type": "crafting_shapeless",
	"ingredients": [
		{
			"item": "minecraft:diamond_sword",
			"data": {
				"require": {
					"Damage": "$..40"
				}
			}
		},
		{ "item": "minecraft:diamond" }
	],
	"result": {
		"item": "minecraft:diamond_axe",
		"data": {
			"display": {
				"Name": "{\"text\":\"Battle Axe\"}"
			},
			"Enchantments": [
				{
					"id": "minecraft:sharpness",
					"lvl": 10
				}
			]
		}
	}
}
```
