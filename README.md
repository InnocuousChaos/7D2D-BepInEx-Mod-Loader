# 7D2D-BepInEx-Mod-Loader

### What Is This?
This is a WIP combination of tools to load 7D2D through BepInex, which means no need to recompile the game dll.



## Quick Start for Mod Users:
### Installation Instructions
Download and extract https://github.com/InnocuousChaos/7D2D-BepInEx-Mod-Loader/releases/download/1.0/7D2D-BepInEx-Mod-Loader.zip (or grab the contents of the 7Day to Die folder from the source) into your 7 Days to Die root directory.
### Installing Mods
Correctly formatted mods should be downloaded and placed into the Mods folder, exactly the same way as pure modlets.
### Running the Game
##### For Windows Users
- 7DaysToDie.exe (Works when launching through Steam as well.)
##### For Linux Users
- run_bepinex.sh



## Advanced Information for Modders
### What does it actually do?
#### BepInEx
This is a library built on top of UnityDoorstop, that allows us to jump in and run code before the game starts. Unlike DMT, there's no need to recompile the games DLL at all.

There are two categories of BepinEx plugins:
Patchers are the BepInEx replacement for the old PatchScripts; they work by modifying the DLL in memory before it actually loads, allowing you to make changes Harmony can't.
Plugins are the BepInEx method for applying Harmony interfaces. Note that BepInEx is built on top of HarmonyX instead of Harmony2. The 2 are mostly interchangeable, but there are a couple notable differences, check the wiki on their git link below.

Typically, BepInEx loads mods from BepInEx\patchers and BepInex\plugins; indeed this is where you can install various useful plugins for dev work. For releasing Mods I've included the following BepInExPlugins:

#### MultiFolderLauncher
This is a BepInEx patcher that allows us to load patchers and plugins from a folder specified by the doorstop_config.ini file. This location is defaulted to "C:\Program Files (x86)\Steam\steamapps\common\7 Days To Die\Mods" for the typical Steam install, but if you wish to load mods from a different folder, or have 7D2D instlaled in a different location, you can change that here. Specifically, it looks for DLLs inside of a patchers folder, and DLLs inside a plugins folder.

#### DMTBridgeLoader
This will scan the Mods folder for mods, which it recognizes by looking for a ModInfo.xml inside the mod folder. Then it checks Harmony folders for dlls that implement the DMTs IHarmony interface, and loads them into the game. Note that currently this doesn't support compiling cs files the way DMT used to, it only checks for DLLs.

#### Warning
DMT support is included for legacy mods but considered Deprecated. Future development should be done with the BepInEx Patchers and Plugins, and DMT Harmony mods should be migrated to BepInEx implementations.



### Credits/Source:
#### BepInEx:
- https://github.com/BepInEx/BepInEx
#### HarmonyX
- https://github.com/BepInEx/HarmonyX
#### DMTBridgeLoader:
- https://github.com/InnocuousChaos/DMTBridgeLoaderPlugin forked from SphereII
#### MultiFolderLoader:
- https://github.com/BepInEx/BepInEx.MultiFolderLoader
