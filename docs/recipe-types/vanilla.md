# Vanilla Recipes

Vanilla recipes work as described for [ingredients], [remainders] and [results].

This includes shapeless and shaped crafting recipes, stonecutting and cooking recipes.

A special case are smithing recipes (using the smithing table): Nbt Crafting had support for json smithing recipes before vanilla had them, also vanilla recipes do nbt copying on there own.

Therefore if you just want to copy nbt data in a vanillish fashion use the `minecraft:smithing` recipe type. *This won't support adding nbt nor dollars!* If you need to use [dollars](../../dynamic-data/dollars) you can use the recipe type `nbtcrafting:smithing`. This won't do any nbt magic on it's own but has full support for nbt crafting's normal features. The recipe format works similar to [anvil recipes](../anvil).

[ingredients]: ../../recipe-parts/ingredients/ingredients
[remainders]: ../../recipe-parts/ingredients/remainders
[results]: ../../recipe-parts/results
