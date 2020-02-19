# Modded Recipes

Modded recipe types might work with the features of Nbt Crafting. *Only dollars and remainders won't work as they need to be handled specially.*

## Notes for mod authors

If you want your mod to be compatible with Nbt Crafting's features pay attention to the following guidelines:
- For recipe ingredients you should use `Ingredient.fromJson()`. That should be the way to go anyway.
- To deserialize recipe results use `ShapedRecipe.getItemStack()`: this method is patched to include nbt data.
- If you want dollars to be usable in the result you will need to use Nbt Crafting's `RecipeUtil`
