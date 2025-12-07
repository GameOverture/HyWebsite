## Child Nodes

Entity nodes on their own are empty husks. Their true power comes from grouping other scene nodes together to represent objects or ideas. Other scene nodes that are set as children of an entity will have their transforms (position, rotation, scale) be relative to the entity's transform. Other entities can also be children, allowing for complex hierarchies of objects.  

Beyond transformations, other things like visibility, display order, and loading/unloading of assets are also managed hierarchically. For example, changing an entity's visibility will affect all its child nodes. Similarly, loading or unloading an entity will load or unload all its children.

### Setting Display Order

When an entity's display order is set, all its child nodes will have their display order offset by the entity's display order. This allows for easy layering of complex objects within the scene.


## Collision Fixtures

They can also detect input, collisions, and apply physics.

### Mouse Input

## Physics

## Custom Entities

Custom classes derived from `HyEntity2d` to implement their own logic.  

``` mermaid
classDiagram
  HyEntity2d <|-- CustomEntity
  class HyEntity2d{
    -HyAnimVec2 pos
    -HyAnimFloat rot
    -HyAnimVec2 scale
    ...
    +HyEntity2d()
    ~HyEntity2d()
    +Load() bool
    +Unload() void
    +IsLoaded() bool
    +Update(float deltaTime) void
  }
  class CustomEntity{
    ...
    +CustomEntity()
    ~CustomEntity()
    +Update(float deltaTime) void
  }
```
