---
title: "🔶Scene Management"
---

Programming the game logic, or implementing the "scene management" of your game is ultimately up to you. The main concepts you should be familiar with are how the following scene nodes work together.

<div class="grid cards" markdown>

-   [:simple-dwavesystems:{.hyindicator}ㅤ**Item Nodes**](./item-nodes.md)

    ---

    These nodes are the components that can be assembled to create more complex objects or used independently. The [Project Items](../../editor/items/index.md) made the in the **HyEditor** are used to initialize these nodes. Each node type have similar construction and usage patterns, but are specialized for different tasks.

-   [:simple-codeblocks:{.hyindicator}ㅤ**Entities & Physics**](./entities.md)

    ---

    Special scene nodes that are able to group multiple **Item Nodes** together to represent objects or ideas. Only these nodes are able to detect input or collisions, and apply physics. Custom classes are derived from `HyEntity2d` to implement their own logic.

-   [:material-widgets:{.hyindicator}ㅤ**User Interface**](./user-interface.md)

    ---

    A suite of nodes specifically built to accomplish user interface tasks. UI widgets like labels, buttons, meters, and more are constructed with **Item Nodes** and able to be arranged and sized within flexible layouts. The entire UI suite is built from `HyEntity2d` scene nodes.

</div>

## Pausing the Game

Harmony provides an easy way to facilitate pausing and unpausing the game.  

``` cpp
HyEngine::PauseGame(true);  // Pause the game
HyEngine::PauseGame(false); // Unpause the game
```

All **Item Nodes** and **Entity Nodes** have their `Update()` function automatically called within HyEngine's main game loop. This update function is responsible for handling all game logic, animations, and other time-dependent behaviors. However, when the game is paused, these functions will not be called, which effectively freezes the game in place.

Every node has the following API:

``` cpp
bool IsPauseUpdate() const;
virtual void SetPauseUpdate(bool bUpdateWhenPaused);
```

By default a node's "pause update" is disabled so all nodes will freeze when the game is paused. When enabled, the node's `Update()` function will continue to be called even when the game is paused. This is useful for nodes that need to maintain certain behaviors during a pause, such as game menus or UI elements.
