# Hints for modders

Hello fellow modder, here's a quick overview of what you probably wanna know about working with Nbt Crafting:

## Setting up Nbt Crafting
To use Nbt Crafting you'll need to include it in your development environment. I publish the mod artifacts on my maven. To use it you need to add it to the `repositories` in your `build.gradle` file. The result should like this:

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

You can see the latest maven releases here:
[![latest 1.15](https://img.shields.io/maven-metadata/v?label=latest%201.15&metadataUrl=https%3A%2F%2Fmaven.siphalor.de%2Fde%2Fsiphalor%2Fnbtcrafting-1.15%2Fmaven-metadata.xml){: .x-img-badge }](https://maven.siphalor.de/de/siphalor/nbtcrafting-1.15/)
[![latest 1.16](https://img.shields.io/maven-metadata/v?label=latest%201.16&metadataUrl=https%3A%2F%2Fmaven.siphalor.de%2Fde%2Fsiphalor%2Fnbtcrafting-1.16%2Fmaven-metadata.xml){: .x-img-badge }](https://maven.siphalor.de/de/siphalor/nbtcrafting-1.16/)
[![latest 1.17](https://img.shields.io/maven-metadata/v?label=latest%201.17&metadataUrl=https%3A%2F%2Fmaven.siphalor.de%2Fde%2Fsiphalor%2Fnbtcrafting-1.17%2Fmaven-metadata.xml){: .x-img-badge }](https://maven.siphalor.de/de/siphalor/nbtcrafting-1.17/)

Finally tell you're users that they'll need to download Nbt Crafting alongside this mod and add a `"nbtcrafting": "*"` entry to the `depends` list in your `fabric.mod.json` file.

## Custom `RecipeType`s
If you're adding custom `RecipeType`s you should consider following these [guidelines](recipe-types/modded.md#guidelines-for-mod-authors) to ensure compatibility 🎉.
