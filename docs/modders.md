# Hints for modders

Hello fellow modder, here's a quick overview of what you probably wanna know about working with Nbt Crafting:

## Setting up Nbt Crafting
To use Nbt Crafting you'll need to include it in your development environment. I currently recommend using [jitpack.io](https://jitpack.io) as I don't have an own maven server yet.

To make use of the Jitpack repository you'll need to add it **to the bottom of the `repositories` section** in your `build.gradle` file. The result should like this:

```gradle
repositories {
	// Here go other maven servers
	maven {
		name "Siphalor's Maven"
		url "https://maven.siphalor.de"
	}
}
```

!!! note "Attention!"
	The here mentioned `repositories` section is different from the equally-named section in the `publishing` region. If you have a new project then you will most likely have to create the `repositories` section yourself. It's usually put above the `dependencies` section.

Then you'll need to tell Gradle which dependencies you need. I personally recommend adding Nbt Crafting as a `modImplementation` dependency:

```gradle
dependencies {
	// Here are other dependencies like the minecraft and yarn version

	modImplementation "de.siphalor:nbtcrafting-1.15:2+"
}
```

*Change it to `nbtcrafting-1.16:2+` instead if you want to develop for 1.16.*

Finally tell you're users that they'll need to download Nbt Crafting alongside this mod and add a `"nbtcrafting": "*"` entry to the `depends` list in your `fabric.mod.json` file.

## Custom `RecipeType`s
If you're adding custom `RecipeType`s you should consider following these [guidelines](recipe-types/modded.md#guidelines-for-mod-authors) to ensure compatibility 🎉.
