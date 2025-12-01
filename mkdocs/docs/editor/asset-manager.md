---
title: "Asset Manager"
---

## 🔸Overview

<figure>
  <img src="../img/editor/asset-manager.png" alt="Asset Manager Dock Window">
  <figcaption>Along with textures and audio, your source code is also considered assets! </figcaption>
</figure>

1️⃣. Each tab along the top independently manages a different type of asset:

- ![CodeIcon](../img/editor/code.png) **Code:** Your C++ source code files and builds.
- ![AtlasIcon](../img/editor/atlas-file.png) **Atlases:** Imported and generated image files combined into texture atlases.
- ![AudioIcon](../img/editor/audio-manager.png) **Audio:** Sound files, including music and sound effects.  

!!! info inline end "Code Assets"
    Code assets do not use **Banks**. They instead make **Builds**, which are entirely different and explained in the [Build Settings](#build-settings) section.  
2️⃣. Banks are used to group assets that are likely to be used together. Examples would be grouping assets by game level, or by type (e.g., UI sounds vs. gameplay sounds).

- More information can be found in the [Banks](#banks) section

3️⃣. Along the bottom are the tool buttons that allow you to manage your assets:
=== "![CodeIcon](../img/editor/code.png) Code"
    - ![New Class](../img/editor/Source-New.png): Add a new C++ class.
    - ![New Filter](../img/editor/Filter-New.png): Create new filter, which is essentially a folder to organize your images within a bank.
    - ![Import](../img/editor/Source.png): Import already existing code files from a single directory.
    - ![Import Dir](../img/editor/Source-Open.png): Import already existing code files from a directory and its subdirectories.
    - ![Replace](../img/editor/atlas-replaceFrame.png): Replace selected images by selecting the same number of new assets.
    - ![Delete](../img/editor/edit-delete.png): Delete selected images
    !!! warning
        These actions do not use an undo/redo system

=== "![AtlasIcon](../img/editor/atlas-file.png) Atlases"
    - ![New Filter](../img/editor/Filter-New.png): Create new filter, which is essentially a folder to organize your images within a bank.
    - ![Import](../img/editor/AtlasFrame.png): Import specified PNG image files from a single directory.
    - ![Import Dir](../img/editor/AtlasFrame-Open.png): Import all PNG image files from a directory and its subdirectories.
    - ![Replace](../img/editor/atlas-replaceFrame.png): Replace selected images by selecting the same number of new assets.
    - ![Delete](../img/editor/edit-delete.png): Delete selected images
    !!! warning
        These actions do not use an undo/redo system

=== "![AudioIcon](../img/editor/audio-manager.png) Audio"
    - ![New Filter](../img/editor/Filter-New.png): Create new filter, which is essentially a folder to organize your sounds within a bank.
    - ![Import](../img/editor/SoundClip.png): Import specified WAV sound files from a single directory.
    - ![Import Dir](../img/editor/SoundClip-Open.png): Import all WAV sound files from a directory and its subdirectories.
    - ![Replace](../img/editor/atlas-replaceFrame.png): Replace selected sound WAVs by selecting the same number of new assets.
    - ![Delete](../img/editor/edit-delete.png): Delete selected sounds
    !!! warning
        These actions do not use an undo/redo system

## 🔸Assets
The assets and filters are shown in the main tree view:

- You can multi-select and drag 'n drop them to new locations.  
- Double ++left-button++ an asset will preview it in the **Asset Inspector**, located in the Auxiliary window.  
- ++right-button++ an asset will open a context menu with additional options, such as renaming, moving to a different bank, or setting [Asset Properties](#asset-properties).
- ++right-button++ an asset and selecting **Asset Properties** will open the **Asset Properties** dialog.


## 🔸Banks

<figure>
  <img src="../img/editor/asset-manager-context-menu.png" alt="Asset item context menu">
  <figcaption>Right-click context menu for an asset</figcaption>
</figure>

## 🔸Code & Build Management

When you select the **Code** tab in the **Asset Manager**, you'll see a list of your game's C++ source code files. These files are organized into **Builds**, which are configurations that determine how your code is compiled and linked.

### Build Settings

With the desired **Project** active, you can open the **Build Settings** in the menu `Project > Build Settings`

![Build Settings Dialog](../img/editor/dlg_build_settings.png)

**Output Name** is the name of the final executable file created when building your game.

Below that you can choose which 3rd party vendors Harmony will use if you have a preference. The **Extras** require you to manually install them in the respective `HarmonyEngine/Engine/extras/` directory. Follow the instructions in the `README.txt` file included in each extra's folder.

### Adding Additional Library Dependencies

If you need certain code libraries/dependencies to be included in your build click the ![Add Button](../img/editor/generic-add.png) **Add library dependency** button.

<figure>
  <img src="../img/editor/dlg_build_settings_dependency.png" alt="Library dependency widgets">
  <figcaption>Example of the cURL library as a dependency</figcaption>
</figure>

The library dependency must be a CMake compatible package. You must specify the following two fields:

- **CMakeLists.txt Project Name**: The library target name used within the `add_library()` command.
- **Library relative location**: Use the "Browse..." button to select the folder where the library's root `CMakeLists.txt` is located

**Options** can be left blank, but is useful if you want to override default options or inject CMake scripting code. The options are parsed (and cached) before the library is included.

!!! note "After Adding Dependencies"
    If you already have an existing build, CMake may try to update the environment automatically after you try to compile. On occasion, CMake errors out and prints `setlocal` in the output, which may be resolved by deleting and recreating the build.

### Creating New Builds

With your **Build Settings** determined, you can create a new build of your game by selecting `Project > New Build` from the menu, or by pressing `Ctrl+Shift+B`.

Any existing source code is independent of your builds, so removing the **Project**'s `/build/` folder can be done freely. 
