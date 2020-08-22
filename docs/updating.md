# Updating from v1

!!! warning "Important note for mod pack authors"
	Updating to v2 breaks compatibility to v1. v1 players won't be able to join on v2 servers and the other way around.

More changes will be added to this page while working one the update.

## JSON changes

- **Dollars** in general:
	- Dollars now support operator precedence (e.g. `3+1*2` now returns 5 instead of 6)
	- Dollars now have more data types:
		- This means that `5 / 2` = 2 but `5.0 / 2` = 2.5
		- More about this coming soon™ in the [dollar documentation](../dynamic-data/dollars)
- **Anvil recipes**
	- **Dollars** now use `base` instead of `i0` and `ingredient` instead of `i1`
- **Brewing recipes**
	- **Dollars** now use `ingredient` and `base` accordingly instead of just `this`
- **Cauldron recipes**
	- **Dollars** now use `ingredient` instead of `i0`
- **Cooking recipes**
	- Cooking recipes' ingredients now work the same as all other ingredients


## Java changes

Most notably dollars changed completely and has also been moved to the `de.siphalor.nbtcrafting.dollar` package
### API

- `RecipeUtil` now expects `Map<String, Object>` instead of `Map<String, CompoundTag` - you can now put in `Number`s and `String`s too - have fun 😉
- `ServerRecipe` has been moved into the new `de.siphalor.nbtcrafting.api` package
- **`NbtHelper`**
	- This, `NbtNumberRange` and `NbtException` can now be found in `de.siphalor.nbtcrafting.api.nbt`
	- JSON paths have mostly been updated to `String[]`
	- `iterateTags` has been moved to `NbtIterator`


### Other stuff

- The `Core` class is now called `NbtCrafting` - accordingly `ClientCore` became `NbtCraftingClient`
- Also `MODID` gained an underscore so it's now `MOD_ID`
- Duck interfaces have been moved into their own package

