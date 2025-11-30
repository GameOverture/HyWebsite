---
title: "Projects"
---

## Creating a new Project

To create a new Project in the Project Explorer you can:

- Click the ![New Project Button](../img/editor/Project-New.png) button along the top tool bar
- `File > New Project` from the menu
- Press `Ctrl+Shift+N`

<figure>
  <img src="../img/editor/dlg_new_project.png" alt="Create New Project Dialog">
  <figcaption></figcaption>
</figure>

**Game Title** is the human readable name of your game, used on labels and titles.

**Code Name** will be used to create the main C++ class, and must be compliant with standard naming conventions.

The final **Project Location** (where all the project files will be dumped) is assembled by what's specified in the text field PLUS whether **Create game directory at location** is checked.

!!! note "Example Setup"
    If you want to specify a common location for multiple game projects, specify that root location the text field and keep **Create game directory at location** checked.

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

