# Tutorials and Resources

Here are a list of tutorials and resources for RimWorld Modding.

## Updating to 1.0
- [Tynan's forum post for 1.0](https://ludeon.com/forums/index.php?topic=41766.0)
- [Python script to convert graphic_multi texture files to the correct extension](https://gist.github.com/spdskatr/d0cb17db9dfe23f58d8bbbeda1795845) (from *_back to *_north, *_side to *_east, and *_front to *_south)

## Getting set up

- [Picking a text editor](texteditor) - Whichever you use, use the find in files option.
- **Recommended decompilers:**
  - [dnSpy](https://github.com/0xd4d/dnSpy/releases) - feature-rich and often updated.
    - dnSpy can be used to debug Unity games that you can't usually debug. Read [here](https://github.com/0xd4d/dnSpy/wiki/Debugging-Unity-Games), remember to download the Unity-debugging-win32.zip from releases
  - [ILSpy](https://github.com/Zhentar/ILSpy/releases) - fast and simple.
  - [dotPeek](https://www.jetbrains.com/decompiler/download/) - primarily useful when transpiling because of its synchronised IL and C# view.
- [Setting up a solution for RimWorld](http://rimworldwiki.com/wiki/Modding_Tutorials/Setting_up_a_solution) or [setting up Visual Studio](http://www.thewindowsclub.com/how-to-get-started-with-visual-studio). You'll need to be able to target the .NET 3.5 framework to mod RimWorld.
- [fyarn's Rimworld Mod Development Cookiecutter](https://ludeon.com/forums/index.php?topic=39038): Set up a fully functional mod development environment in 30 seconds or less with a Visual Studio integration
- [Things you might not know](nobodyreadsthereadme)

## General

- [Modding tutorials page on the RimWorld wiki](http://rimworldwiki.com/wiki/Modding_Tutorials)
- [Mod Help section on the ludeon forums](https://ludeon.com/forums/index.php?board=14.0)
- [Roxxploxx's modding guide](https://github.com/roxxploxx/RimWorldModGuide/wiki)
- [Jecrell's step-by-step modding guide](https://ludeon.com/forums/index.php?topic=33219.msg338626#msg338626)
- [ZorbaTHut's intro to modding features](https://ludeon.com/forums/index.php?topic=32735.0)
- [KeenKrozzy's Guide to using custom textures](https://www.youtube.com/watch?v=zqXbHso6TfU)
- [GitHub repositories of modders](telephonebook)
- [RimWorld font, courtesy of Marnador](https://github.com/spdskatr/RWModdingResources/raw/master/RimWordFont.ttf)

## XML

- [Abstracts and inheritance](abstracts) - AKA "what the hell am I copy-pasting over anyway?"
- [Zhentar's Introduction to PatchOperation](https://gist.github.com/Zhentar/4a1b71cea45b9337f70b30a21d868782): using xpath to target parts of Defs.
- [RimWorld XML Auto-Documentation](https://ludeon.com/forums/index.php?topic=21440.0) - an HTML help file for modders. It contains a listing of all Core (ie. vanilla) uses of RimWorld's XML code.  It's great for learning what tags are parents or children of what.
- **Background information**
  - [W3Schools introduction to xpath](https://www.w3schools.com/xml/xpath_intro.asp) - RW does not support all features, but this teaches you a lot.
  - [W3Schools introduction to basic XML](https://www.w3schools.com/xml/) - Read up to and including the "Attributes" article.

## C&#35;

- [Learn C# from Microsoft Virtual Academy](https://mva.microsoft.com/en-us/training-courses/c-fundamentals-for-absolute-beginners-16169)
- [The Harmony Wiki](https://github.com/pardeike/Harmony/wiki/)
- [Brrainz's introduction to transpiling with Harmony](https://gist.github.com/pardeike/c02e29f9e030e6a016422ca8a89eefc9)
- [Why_is_that's guide to Mod Settings](https://github.com/AaronCRobinson/SettingsHelper/wiki)
- [Mehni's top to bottom breakdown of the Job system](https://github.com/Mehni/ExampleJob/wiki)
- [Guide to saving stuff using ExposeData](saving-guide)
- [Ideas for a first project](starterprojects)

## Graphics

- [Seraphile's Open source graphic resources & wiki](https://github.com/seraphile/rimshare/)
- [Seraphile's guide to colouring images and masks](https://github.com/seraphile/rimshare/wiki/Colouring-in-Images)
- [CannibalRechter's CompFX for animated textures](https://ludeon.com/forums/index.php?topic=35895.0)
- [Officially unofficial artstyle guide](artstyle)
