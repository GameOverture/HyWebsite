---
title: "Projects"
---

## Creating a new Project

To create a new Project in the Project Explorer you can:

- Click the ![New Project Button](../img/editor/Project-New.png) button along the top tool bar
- `File > New Project` from the menu
- Press `Ctrl+Shift+N`

![New Project Dialog](../img/editor/dlg_new_project.png)

**Game Title** is the human readable name of your game, used on labels and titles.

**Code Name** will be used to create the main C++ class, and must be compliant with standard naming conventions.

The final **Project Location** (where all the project files will be dumped) is assembled by what's specified in the text field PLUS whether **Create game directory at location** is checked.
> If you want to specify a common location for multiple game projects, specify that root location the text field and keep **Create game directory at location** checked.

Within **Advanced** you can customize how the project folders (like the assets or source code) reside and what they're named. You can even specify locations outside the **Project Location**. For each entry, specify the relative path from the **Project Location**, and the name of the directory itself.

## Project Explorer

<figure>
  <img src="../img/editor/project_explorer.png" alt="Project Explorer Dock Window">
  <figcaption>Folders within <strong>Project Explorer</strong> are often referred as <em>Prefixes</em>.</figcaption>
</figure>

1. All currently open **Project**s ![Project Icon](../img/editor/Project.png) are shown in the tree view here. Nested beneath each **Project** are the prefix folders containing the **Project Items**. The currently active project is shown with the ![Project Active Icon](../img/editor/Project-Pending.png) sub-icon.
2. You can drag **Project Items** between entirely different game **Projects** to copy them. This will include importing any required assets into the target project.
3. The search box allows you to filter the visible **Project Items** in the tree view. You can also filter by item type by selecting the corresponding icon.

## Project Settings

Under Development - Dialog tool meant to edit the game's .hyproj file

## Build Settings

With the desired **Project** active, you can open the **Build Settings** in the menu `Project > Build Settings`

![Build Settings Dialog](../img/editor/dlg_build_settings.png)

**Output Name** is the name of the final executable file created when building your game.

Below that you can choose which 3rd party vendors Harmony will use if you have a preference. The **Extras** require you to manually install them in the respective `HarmonyEngine/Engine/extras/` directory. Follow the instructions in the `README.txt` file included in each extra's folder.

### Adding Additional Library Dependencies

If you need certain code libraries/dependencies to be included in your build click the ![Add Button](../img/editor/generic-add.png) **Add library dependency** button.

![Library dependency widgets](../img/editor/dlg_build_settings_dependency.png)

The library dependency must be a CMake compatible package. You must specify the following two fields:

- **CMakeLists.txt Project Name**: The library target name used within the `add_library()` command.
- **Library relative location**: Use the "Browse..." button to select the folder where the library's root `CMakeLists.txt` is located

**Options** can be left blank, but is useful if you want to override default options or inject CMake scripting code. The options are parsed (and cached) before the library is included.

> If you already have an existing compatible build, CMake may try to update the environment automatically when you try to compile. On occasion you may need to recreate your build after adding dependencies.

## Creating New Builds

With your **Build Settings** determined, you can create a new build of your game by selecting `Project > New Build` from the menu, or by pressing `Ctrl+Shift+B`.

Any existing source code is independent of your builds, so removing the **Project**'s `/build/` folder can be done freely. 
