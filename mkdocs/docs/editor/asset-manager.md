---
title: "Asset Manager"
---

## Overview

<figure>
  <img src="../img/editor/asset-manager.png" alt="Asset Manager Dock Window">
  <figcaption>Your source code is also considered assets! Along with textures and audio. </figcaption>
</figure>

1. Each tab along the top independently manages a different type of asset:
    - **Code:** Your C++ source code files, including auto-generated [entity](./items/entity.md) classes
    - **Atlases:** Imported and generated image files combined into texture atlases
    - **Audio:** Sound files, including music and sound effects
2. Banks are used to group assets that are likely to be used together. Examples would be grouping assets by game level, or by type (e.g., UI sounds vs. gameplay sounds).
> Code assets do not use banks. They instead make **builds**, which are entirely different and explained in the [Build Settings](#build-settings) section.

3. Along the bottom are the tool buttons that allow you to manage your assets:
    - ![New Filter](../img/editor/Filter-New.png): Create new filter, which is essentially a folder to organize your assets within a bank.
    - ![Import](../img/editor/AtlasFrame.png): Import specified assets from a single directory.
    - ![Import Dir](../img/editor/AtlasFrame-Open.png): Import all assets from a directory and its subdirectories.
    - ![Replace](../img/editor/atlas-replaceFrame.png): Replace selected assets by selecting the same number of new assets.
    - ![Delete](../img/editor/edit-delete.png): Delete selected assets
> These actions do not use an undo/redo system

4. The filters and assets are shown in a tree view:
    - You can multi-select and drag 'n drop them to new locations.  
    - Double-clicking an asset will preview it in the **Asset Inspector**, located in the Auxiliary window.  
    - Right-clicking an asset will open a context menu with additional options, such as renaming, moving to a different bank, or setting [Asset Properties](#asset-properties).

<figure>
  <img src="../img/editor/asset-manager-context-menu.png" alt="Asset item context menu">
  <figcaption>Right-click context menu for an asset</figcaption>
</figure>


## Asset Properties

Right-clicking an asset and selecting **Properties...** will open the **Asset Properties** dialog.


