---
title: "🔶Scene Management"
---

Programming the game logic, or implementing the "scene management" of your game is ultimately up to you. The main concepts you should be familiar with are how nodes and entities work together.

## Item Nodes

The [Project Items](../../editor/items/index.md) that have been created the in the **HyEditor** can be used to declare 'node' instances to populate your scene. Each node type have similar construction and usage patterns, but are specialized for different tasks.

Learn more about these basic nodes in the [Item Nodes](./item-nodes.md) section.

## Entities

Entities are special nodes that are able to combine multiple **Item Nodes** together, and implement custom logic, apply physics, and more. This is typically done by declaring your own custom classes that inherit from `HyEntity2d`. 

Learn more about entities and physics in the [Entities & Physics](./entities.md) section.

## Pausing the Game

Harmony provides an easy way to facilitate pausing and unpausing the game. All instantiated nodes will have their internal `Update()` function automatically called within HyEngine's main game loop. This update function is responsible for handling all game logic, animations, and other time-dependent behaviors. However, when the game is paused, these functions will not be called, which effectively freezes the game in place.

Every node has the following API:

``` cpp
bool IsPauseUpdate() const;
virtual void SetPauseUpdate(bool bUpdateWhenPaused);
```

By default a node's "pause update" is disabled so all nodes will freeze when the game is paused. When enabled, the node's `Update()` function will continue to be called even when the game is paused. This is useful for nodes that need to maintain certain behaviors during a pause, such as game menus or UI elements.
