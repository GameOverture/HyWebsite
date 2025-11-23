---
title: "Editor Manual"
---

<figure>
  <img src="/docs/img/editor_overview.png" alt="HyEditor interface overview">
  <figcaption>HyEditor's default window layout.</figcaption>
</figure>

### 1️⃣. Project Explorer

Open **Project**'s will show up here. You may have multiple **Project**'s open and browsable at once, but only one **Project** may be 'active' at a given time. All the details are provided in the [Project Explorer](project_explorer.md) section.

### 2️⃣. Asset Manager

The currently active **Project**'s **Asset Manager**. Each tab along the top are the major asset types handled independantly from each other. All the details are provided in the [Asset Manager](asset_manager.md) section.

### 3️⃣. Project Tab Bar

All currently open **Project Item**'s from the active **Project** are shown here. You can cycle between them with `Ctrl+Tab` and each item has its own Undo/Redo stack.

### 4️⃣. Project Item Properties

Shows all the properties of the currently selected **Project Item** in the **Project Tab Bar**. The properties set here set are reflected in the **middle render window**.

### 5️⃣. Middle Render Window

The currently selected **Project Item** is previewed here. The renderer used here is the same renderer used in your game, **HyEngine**. Previews are created by simulating the same load process as well, so it's a WYSIWYG work-flow. Pan the view with `WASD` or `Middle Mouse`, and zoom with the `Mouse Wheel`.

### 6️⃣. Auxiliary Window

The Auxiliary window is contextually used when needed. By default it'll display logs, but when an additional window is needed by the **Asset Manager** or the **Project Item Properties**, a new tab along the bottom will appear and be shown. Its visibility can be toggled with `Ctrl+Space`

## ▶️Editor Flow

<figure>
  <img src="/docs/img/editor_flow.png" alt="HyEditor work flow">
  <figcaption>Shows how each section of HyEditor works together.</figcaption>
</figure>

1. Open a **Project Item** from **Project Explorer**...
2. Shows up in **Project Tab Bar**, and when selected...
3. It will be displayed in the **Project Item Properties** which...
4. May reference assets in **Asset Manager** to...
5. Show a preview in the **Middle Render Window**