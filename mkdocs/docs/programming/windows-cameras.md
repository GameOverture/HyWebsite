## Initial Setup

Based on your [Project Settings](../editor/projects.md#project-settings), the number of windows (and their resolution) your game uses is determined.

Most projects begin with setting up the cameras. For each window your game uses, you will need to create a corresponding camera. To access the windows of your game, use the global static function:
`#!cpp static HyWindow &Window(uint32 uiWindowIndex = 0);`

This will return the `HyWindow` object for the specified window index. 

!!! note ""
    Most game projects only use one window, but if you need multiple windows, remember to create a camera for each window you create.

`#!cpp m_pCamera = HyEngine::Window().CreateCamera2d();`

That's all that's needed to setup the main window and a 2D camera. You can continue to the next topic, or continue to learn more advanced window and camera features below.

## Camera Viewports

By default, a newly created camera will cover the entire viewport of the window.

<!-- ![Camera Viewport](../img/programming/window-camera-viewport.png) -->

Multiple cameras can be created for each window, and each camera can be set to render to a specific portion of the window. This is how you can accomplish local split-screen multiplayer views, or picture-in-picture views.

The viewport rectangle is defined in normalized coordinates, where (0,0) is the bottom-left of the window, and (1,1) is the top-right of the window. To change the camera's viewport rectangle:

`#!cpp m_pCamera->SetViewport(0.0f, 0.0f, 0.5f, 1.0f); // Left half of the window`

### Camera Transforms

### Camera Shake
