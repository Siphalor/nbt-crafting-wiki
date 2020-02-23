# Experimental Features :fa-flask:
## `stat_changed` Advancement Trigger

There's now a `nbt_crafting:stat_changed` advancement trigger. It requires the `stat` condition which is takes the identifier of a player stat. 

By default it will trigger on every update of that stat.

Optionally you can specify a `range` property that works the same like number ranges work in command selectors (e. g. `8..10` for a value inclusively between eight and ten).
