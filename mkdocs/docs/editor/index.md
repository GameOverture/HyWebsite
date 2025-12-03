---
title: "Editor Manual"
---

<figure>
  <img src="../img/editor_overview.png" alt="HyEditor interface overview">
  <figcaption>HyEditor's default window layout.</figcaption>
</figure>

<div class="grid cards" markdown>

- :material-numeric-1-circle:{.hyindicator}ㅤ**Project Explorer**  
    Open Projects will show up here. You may have multiple Projects open and browsable at once, but only one Project may be 'active' at a given time. All the details are provided in the [Projects](projects.md) section.
- :material-numeric-2-circle:{.hyindicator}ㅤ**Asset Manager**  
    The currently active Project's Asset Manager. Each tab along the top are the major asset types handled independently from each other. All the details are provided in the [Asset Manager](asset-manager.md) section.
- :material-numeric-3-circle:{.hyindicator}ㅤ**Project Tab Bar**  
    All currently open [Project Items](items/index.md) from the active Project are shown here. You can cycle between them with ++ctrl+tab++ and each item has its own Undo/Redo stack.
- :material-numeric-4-circle:{.hyindicator}ㅤ**Project Item Properties**  
    Shows all the properties of the currently selected [Project Item](items/index.md) in the Project Tab Bar. The properties set here set are reflected in the middle render window.
- :material-numeric-5-circle:{.hyindicator}ㅤ**Middle Render Window**  
    The currently selected [Project Item](items/index.md) is previewed here. The renderer used here is the same renderer (HyEngine) used in your game. Previews are created by simulating the same load process as well, so it's a WYSIWYG work-flow. Pan the view with ++w++ ++a++ ++s++ ++d++ or ++middle-button++, and zoom with the Mouse Wheel :material-mouse-scroll-wheel:.
- :material-numeric-6-circle:{.hyindicator}ㅤ**Auxiliary Window**  
    The Auxiliary window is contextually used when needed. By default it'll display logs, but when an additional window is needed (like when creating [TileSets](tilesets.md)), a new tab along the bottom will appear and be shown. Its visibility can be toggled with ++ctrl+space++.

</div>

## Editor Flow

Shows how each section of HyEditor works together.

<div class="grid" markdown>

![HyEditor work flow](../img/editor_flow.png)

:material-numeric-1-circle:{.hyorange}Open a **Project Item** from **Project Explorer**...  
:material-numeric-2-circle:{.hyorange}Shows up in **Project Tab Bar**, and when selected...  
:material-numeric-3-circle:{.hyorange}It will be displayed in the **Project Item Properties** which...  
:material-numeric-4-circle:{.hyorange}May reference assets in **Asset Manager** to...  
:material-numeric-5-circle:{.hyorange}Show a preview in the **Middle Render Window**  

</div>
