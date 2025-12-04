**Item Nodes** are provided C++ classes to create instances of the Editor's [Project Items](../../editor/items/index.md) such as Sprites, Text, TileMaps, etc. These nodes can be thought of as components to assemble [Entities](./entities.md). Every **Item Node** is a part of the same class hierarchy. 

## Node Hierarchy

Below shows where each **Item Node** (in orange) is located in the hierarchy.

``` mermaid
---
config:
  class:
    hideEmptyMembersBox: true
  layout: elk
---
classDiagram

IHyNode <|-- IHyNode2d
IHyNode <|-- IHyNode3d
IHyNode2d <|-- HyCamera2d
IHyNode3d <|-- HyCamera3d
IHyNode2d <|-- IHyLoadable2d
IHyNode3d <|-- IHyLoadable3d
IHyLoadable2d <|-- HyAudio2d
IHyLoadable3d <|-- HyAudio3d
IHyLoadable2d <|-- IHyBody2d
IHyLoadable3d <|-- IHyBody3d
IHyBody2d <|-- HyEntity2d
IHyBody3d <|-- HyEntity3d
IHyBody2d <|-- IHyDrawable2d
IHyBody3d <|-- IHyDrawable3d
IHyDrawable2d <|-- HySprite2d
IHyDrawable2d <|-- HyText2d
IHyDrawable2d <|-- HyTileMap2d
IHyDrawable3d <|-- HySprite3d
IHyDrawable3d <|-- HyText3d
IHyDrawable3d <|-- HyTileMap3d

class HyCamera2d:::Concrete
class HyCamera3d:::Concrete
class HyAudio2d:::Concrete
class HyAudio3d:::Concrete
class HyEntity2d:::Entity
class HyEntity3d:::Entity
class HySprite2d:::Concrete
class HyText2d:::Concrete
class HyTileMap2d:::Concrete
class HySprite3d:::Concrete
class HyText3d:::Concrete
class HyTileMap3d:::Concrete

classDef Concrete :,stroke-width:2px,stroke:#FA5A0A,
classDef Entity :,stroke-width:2px,stroke:#FF3333,
```

!!! note ""
    For clarity, not all node classes are shown in the diagram above. All the ommitted **Item Nodes** derive either from `IHyDrawable2d` or `IHyDrawable3d`

For each layer in the hierarchy:

<div class="grid" markdown>

``` mermaid
classDiagram

IHyNode <|-- IHyNode2d
IHyNode2d <|-- HyCamera2d
IHyNode2d <|-- IHyLoadable2d
IHyLoadable2d <|-- HyAudio2d
IHyLoadable2d <|-- IHyBody2d
IHyBody2d <|-- HyEntity2d
IHyBody2d <|-- IHyDrawable2d
IHyDrawable2d <|-- HySprite2d
IHyDrawable2d <|-- HyText2d
IHyDrawable2d <|-- HyTileMap2d
```


Base class `IHyNode` for all scene nodes. It keeps track of its type, whether it's visible, and whether it updates during a [Game Pause](./index.md#pausing-the-game).  
2D or 3D

</div>

## Types

The basic node types you can instantiate correspond to the different types of [Project Items](../../editor/items/index.md) you can create in the HyEditor. These include:

=== "![Sprite](../../img/editor/Sprite.png) Sprite"

=== "![Tile Map](../../img/editor/TileMap.png) Tile Map"

=== "![Text](../../img/editor/Text.png) Text"

=== "![Particle Effect](../../img/editor/Particles.png) Particle Effects"

=== "![Prefab](../../img/editor/Prefab.png) Prefab"

=== "![Audio](../../img/editor/Audio.png) Audio"

## Instantiating Nodes

Constructing scene nodes follow a pseudo-RAII (Resource Acquisition Is Initialization) pattern. You can allocate nodes whereever without worrying about inserting them into the scene graph. Constructors take a `HyNodePath`(1) and optionally an Entity as the parent node.
{ .annotate }

1.  A `HyNodePath` wraps a string to identify a [Project Item](../../editor/items/index.md) made in **HyEditor**. The string is a case-insensitive path of each prefix and name, delimted with `/`s. For example: `#!cpp "RootPrefix/SubPrefix/ItemName"`

``` cpp
// Dynamically allocate a sprite node without a parent
HySprite2d *pSprite = HY_NEW HySprite2d("GameSprites/Dancer");

// Dynamically allocate a sprite node that is a child of `pEntity`
HyEntity2d *pEntity = HY_NEW HyEntity2d();
HySprite2d *pChildSprite = HY_NEW HySprite2d("GameSprites/Dancer", pEntity);
```

The [Project Item](../../editor/items/index.md) used to initialize the Item Nodes may reference assets such as textures or audio that will need to be loaded. Construction alone does not initiate any loading, and needs to be explicitly done by calling the `Load()` function (or via an entity's `Load()` function that contains the node).
``` cpp
// Load the sprite's required assets into memory
pSprite->Load();

// Or load all child nodes contained within an entity
pEntity->Load(); // This will load `pChildSprite`
```

By default all nodes have their visibility set to true.

You don't need to concern yourself with what assets are required to load for the node. This is done automatically, and will internally create a reference count for each required asset. Explicitly calling `Unload()`, deleting the node or having it fall out of scope will automatically decrement the reference count internally. Whenever any asset's reference count reaches zero, it will be unloaded from memory.


## Transforming Nodes
