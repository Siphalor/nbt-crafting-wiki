# Hints for modders

Hello fellow modder, here's a quick overview of what you probably wanna know about working with Nbt Crafting:

## Setting up Nbt Crafting
To use Nbt Crafting you'll need to include it in your development environment. I currently recommend using [jitpack.io](https://jitpack.io) as I don't have an own maven server yet.

To make use of the Jitpack repository you'll need to add it **to the bottom of the `repositories` section** in your `build.gradle` file. The result should like this:

```gradle
repositories {
	// Here go other maven servers
	maven {
		name "jitpack"
		url "https://jitpack.io"
	}
}
```

Then you'll need Gradle which dependency you need. I personally recommend adding Nbt Crafting as a `modImplementation` dependency:

```gradle
dependencies {
	// Here are other dependencies like the minecraft and yarn version

	modImplementation "com.github.siphalor:nbt-crafting:1.15-2.0-SNAPSHOT"
}
```

*Change it to `1.16-2.0-SNAPSHOT` instead if you want to develop for 1.16*

!!! warning "Problems with pulling the dependency"
	Since I currently rely on JitPack as maven, it may take a few minutes for JitPack to build new commits. This usually results in time-out issues in Gradle. Just wait a while and check again. If it remains stuck then message me.

Finally tell you're users that they'll need to download Nbt Crafting alongside this mod and add a `"nbtcrafting": "*"` entry to the `depends` list in your `fabric.mod.json` file.

## Custom `RecipeType`s
If you're adding custom `RecipeType`s you should consider following these [guidelines](recipe-types/modded.md#guidelines-for-mod-authors) to ensure compatibility 🎉.
