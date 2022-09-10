# Dollar References

!!!warning
	As of Nbt Crafting v3, the features described here are gated behind the [`nbtcrafting3:data` recipe type](../recipe-types/data).
	This means that you have to use this recipe type for all recipes that use the features described here.

Dollar references are used to copy the nbt data of [recipe ingredients](../../ingredients) completely or partially to the target of the [dollar expression](../dollars).

A reference is used by specifying the _ingredient id_ inside of an expression. To only get a part of some nbt data you can use [dollar operators](../dollars#operators) to navigate through [compounds or lists](../dollars#data-types).

The main purpose of this site is to collect all _ingredient ids_ for the various recipe types.

| Recipe Type          | Ingredients                    | _Ingredient ids_                                               |
|----------------------|--------------------------------|----------------------------------------------------------------|
| Shaped Recipe        | List of ingredients            | `iX` where `X` is the index of the ingredient in the pattern   |
| Shapeless Recipe     | List of ingredients            | `iX` where `X` is the index of the ingredient in file          |
| Cooking Recipes      | The `ingredient`               | `this`                                                         |
| Stonecutting Recipes | _^                          ^_ | _^                                                          ^_ |
| [Anvil Recipes]      | A `base` and an `ingredient`   | `base` and `ingredient` accordingly                            |
| [Brewing Recipes]    |                                |                                                                |
| [Cauldron Recipes]   |                                |                                                                |
| Smithing Recipes     | _^                          ^_ | _^                                                          ^_ |

[Anvil Recipes]: ../../../recipe-types/anvil
[Brewing Recipes]: ../../../recipe-types/brewing
[Cauldron Recipes]: ../../../recipe-types/cauldron
