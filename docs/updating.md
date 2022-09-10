# Updating from Nbt Crafting v2

More changes will be added to this page while the update is being developed.

- Renamed everything from `nbtcrafting` to `nbtcrafting3`.
  I really mean **everything**.
  Don't forget the entry in your `fabric.mod.json`!

- The maven endpoint now also uses `de.siphalor:nbtcrafting3-<minecraft version>`.

- Nbt Crafting will no longer scan and load all recipes.
  Based on the `nbtcrafting:wrapped` recipe type from Nbt Crafting v2,
  **all recipes have to use the `nbtcrafting3:data` recipe type**.

- Since wrapping is now the default, `nbtcrafting:wrapped` has been removed.

- **Dollars**:

	- The Dollar engine has been almost completely rewritten.
	  While simple dollar expressions might still be working,
	  breakage is expected.
	
	- Merge dollars will now always be evaluated **after** normal dollars.
	  This allows for more flexibility while merging,
	  but breaks backwards compatibility,
	  as previously merge dollars were always evaluated before normal dollars.

	- To make full use of merging, you may now use a dollar expression starting with a `$` as a merge mode.
	  See the [NBT merging documentation](../nbt-capabilities/dynamic-data/nbt-merging).

	- The `merge` merge mode (default) will now act the same as `keep` for primitive values.

	- The characters for type casting have been changed to more closely resemble SNBT.  
	  Most notably `S` no longer stands for string and `B` doesn't stand for boolean anymore

	- [Dollar functions](../nbt-capabilities/dynamic-data/dollar-functions) are a thing now
