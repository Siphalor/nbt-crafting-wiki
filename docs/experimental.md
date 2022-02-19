# Experimental Features :fa-flask:
## Wrapped recipes
You might be aware of the mess that KubeJS is doing to recipes.
That mess effectively circumvents Nbt Crafting's modifications.

Since KubeJS leaves officially modded recipe types alone, there's the `nbtcrafing:wrapped` recipe type.
As the name implies, it's nothing more but a simple wrapper over the normal recipes.

It looks only for a single key, `recipe`. That field can contain any other recipe that you actually want to use.

### Example

```json
{
   "type": "nbtcrafting:wrapped",
    "recipe": {
        "type": "minecraft:crafting_shapeless",
        "ingredients": [
            {
                "item": "minecraft:gravel"
            }
        ],
        "result": {
            "item": "minecraft:flint",
            "data": {
                "display": {
                   "Name": "{\"text\":\"Pointy Stone\"}"
                }
            }
        }
    }
}
```

### Why is this experimental?
At the time of writing, this is still pretty new and I'm not sure if I like and there's no better alternative.

Also, I don't really like the name of the type, if you know a better one, let me know.

## Dynamic item stack count
First of:

- Yes, you heard right - you can dynamically set the output amount of a [remainder](../recipe-parts/ingredients/remainders) or [recipe result](../recipe-parts/results).
- **But** although this sounds like a cool idea, it has a lot of caveats. So please read carefully.

You can set the special `nbtcrafting:count` value on any remainder or result stack nbt tag. Yes, you need to specify it *in the `data` section*.

The value of this expression is expected to be a full-blown [dollar expression](../dynamic-data/dollars) beginning with a dollar sign.

So let's talk about the problems and why this is in the experimental section:

- I didn't do a lot of testing on that so even if I say that it might work it could actually be completely broken
- A lot of the vanilla code, modded code and even my own code (in *Mouse Wheelie* for example) is based on the idea that a recipe has a constant output. This means that this kind of code will query the result count for one stack and then multiply it with the amount of items to get the maximum crafts. The concept of a recipe that can be crafted infinitely (using remainders) and produces dynamicly set result counts is too much for this code.
- Remainders are in many situations highly problematic. This is why I usually advice to only use them on non-stackable items. If you keep to that I can give you at least a little guarantee that dynamic stack counts might work with them.

## `stat_changed` Advancement Trigger

There's now a `nbt_crafting:stat_changed` advancement trigger. It requires the `stat` condition which is takes the identifier of a player stat. 

By default it will trigger on every update of that stat.

Optionally you can specify a `range` property that works the same like number ranges work in command selectors (e. g. `8..10` for a value inclusively between eight and ten).
