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
- **Dollars**: The Dollar engine has been almost completely rewritten.
  While simple dollar expressions might still be working,
  breakage is expected.

