## Node Hierarchy

## Basic Node Types

The basic node types you can instantiate correspond to the different types of [Project Items](../../editor/items/index.md) you can create in the HyEditor. These include:

=== "![Sprite](../../img/editor/Sprite.png) Sprite"

=== "![Tile Map](../../img/editor/TileMap.png) Tile Map"

=== "![Text](../../img/editor/Text.png) Text"

=== "![Particle Effect](../../img/editor/Particles.png) Particle Effects"

=== "![Prefab](../../img/editor/Prefab.png) Prefab"

=== "![Audio](../../img/editor/Audio.png) Audio"

## Instantiating Nodes

Constructing nodes follow a pseudo RAII (Resource Acquisition Is Initialization) pattern. You can freely allocate nodes whereever without worrying about inserting them into any type of scene graph. Construction alone does not initiate loading any of its required assets. This needs to be explicitly done by calling the node's `Load()` function (or via an entity's `Load()` function that contains the node).

You don't need to concern yourself with what assets are required to load for the node. This is done automatically, and will internally create a reference count for each required asset. Explicitly calling `Unload()`, deleting the node or having it fall out of scope will automatically decrement the reference count internally. Whenever any asset's reference count reaches zero, it will be unloaded from memory.


## Transforming Nodes
