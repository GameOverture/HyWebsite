

Sprite Items are used to display textured quads in 2D or 3D space. They can show single images or animated spritesheets. When you create or open a Sprite Item, it will appear in the Project Tab Bar. You can then edit its properties in the Project Item Properties panel and see a live preview in the Middle Render Window. Below are the key properties and features of Sprite Items:

## Sprite Properties

<!--
<div class="grid" markdown>

![Sprite Item Properties](../../img/editor/widgets-sprite.png) 

<div class="grid cards" markdown>

- :material-numeric-1-circle:{.hyindicator}ㅤ**Project Explorer**  
    Open Projects will show up here. You may have multiple Projects open and browsable at once, but only one Project may be 'active' at a given time. All the details are provided in the [Projects](projects.md) section.
- :material-numeric-2-circle:{.hyindicator}ㅤ**Asset Manager**  
    The currently active Project's Asset Manager. Each tab along the top are the major asset types handled independently from each other. All the details are provided in the [Asset Manager](asset-manager.md) section.
- :material-numeric-3-circle:{.hyindicator}ㅤ**Project Tab Bar**  
    All currently open [Project Items](items/index.md) from the active Project are shown here. You can cycle between them with ++ctrl+tab++ and each item has its own Undo/Redo stack.

</div>
</div>

-->

## Workflow

To get started with sprites, you need to have imported images into the **Atlases** section of the [Asset Manager](../asset-manager.md). Once you have your images ready your can them as frames to the current state of the Sprite Item. Single frame sprites and animated sprites are created and used the same way. If this is an animated sprite with multiple frames, you can preview the animation using ++space++ which will play/pause the animation starting from the currently selected frame in the properties table. 

At this point you can adjust the frame rate the animation plays, and the origin of each frame (aka the pivot point). These properties affect only the currently selected state, so you can have different animations with different frame rates and origins within the same Sprite Item. You can add more states to the sprite using the state controls at the top of the properties panel.

