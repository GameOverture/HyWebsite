---
title: "Programming Manual"
hide: toc
---

How your game application works with HyEngine. All new projects are generated with this basic structure.

<div class="grid" markdown>

``` mermaid
classDiagram
  HyEngine <|-- YourGame
  class HyEngine{
    -HyInit initStruct
    -HyComponent engineComponent
    ...
    +HyEngine(HyInit)
    ~HyEngine()
    +RunGame() int32
    #virtual OnUpdate() bool
  }
  class YourGame{
    -HyCamera2d * pCamera
    -MainMenu mainMenu
    -ILevel * pCurrentLevel
    -LevelOne LevelOne
    ...
    +YourGame(HyInit)
    ~YourGame()
    #override OnUpdate() bool
  }
```

<div markdown>

:fontawesome-solid-file-alt:`main.cpp`

1. Initializes a `HyInit` structure  

2. Instantiate `YourGame` class, which derives from `HyEngine`  

3. Invoke `YourGame::RunGame()` to start the main game loop

---

Use `YourGame` class constructor to initialize your game.  

Override `OnUpdate()` to implement your game's main logic, such as updating the current level or handling menu navigation. `OnUpdate()` is invoked within Harmony's main game loop whenever a frame of game logic needs to happen.

Simple programs might only need to declare a few scene nodes and can implement all logic directly in `OnUpdate()`. More complex games will likely want to create separate classes to encapsulate different game states or levels.  

</div>

</div>

!!! note annotate
    The member variables declared in your main game class encapsulate the flow or main components of the program. These are usually custom classes derived from `HyEntity2d`. (1)

1. `HyEntity2d` is a special scene node that can contain other scene nodes like sprites, text, and audio. It also serves as a way to logically group and update objects within the game world.  
``` mermaid
classDiagram
    HyEntity2d <|-- MainMenu
    HyEntity2d <|-- ILevel
    ILevel <|-- LevelOne
    class HyEntity2d{
    +HyEntity2d()
    ~HyEntity2d()
    #virtual OnUpdate() void
    }
    class MainMenu{
    -HySprite2d background
    -HyText2d menuText
    ...
    +MainMenu()
    ~MainMenu()
    #override OnUpdate() void
    }
    class ILevel{
    -MainCharacter * pMainCharacter
    -LevelStuff levelStuff
    ...
    +ILevel()
    ~ILevel()
    #override OnUpdate() void
    }
```

## Engine Utilities

The `HyEngine` class (1) provides public static methods to easily access engine functionality and information.
{ .annotate }

1.  `HyEngine` public static methods:
``` cpp
class HyEngine
{
    static HyEngine * sm_pInstance;
    ...

public:
    HyEngine(const HyInit &initStruct);
    ~HyEngine();
    ...
    static bool IsInitialized();
    static const HyInit &InitValues();
    static std::string DateTime();
    static uint32 NumWindows();
    static HyWindow &Window(uint32 uiWindowIndex = 0);
    static float DeltaTime();
    static double DeltaTimeD();
    static void LoadingStatus(uint32 &uiNumQueuedOut, uint32 &uiTotalOut);
    static void PauseGame(bool bPause);
    static HyInput &Input();
    static HyAudioCore &Audio();
    static HyDiagnostics &Diagnostics();
    static HyShaderHandle DefaultShaderHandle(HyType eType);
    static std::string DataDir();
    static HyTextureQuadHandle CreateTexture(std::string sFilePath, HyTextureInfo textureInfo);
    static HyAudioHandle CreateAudio(std::string sFilePath, bool bIsStreaming = false, int32 iInstanceLimit = 0, int32 iCategoryId = 0);
};
```

<div class="grid cards" markdown>

-   [:fontawesome-solid-video-camera:{.hyindicator}ㅤ**Windows & Cameras**](./windows-cameras.md)  
    How to manage your camera viewports and render windows.
    ``` cpp
    // Windows & Cameras
    static uint32 NumWindows();
    static HyWindow &Window(uint32 uiWindowIndex = 0);
    ```

-   [:material-graph-outline:{.hyindicator}ㅤ**Scene Management**](./scene/index.md)  
    Where you make the game. [Item Nodes](./scene/item-nodes.md) | [Entities & Physics](./scene/entities.md) | [User Interface](./scene/user-interface.md)
    ``` cpp
    // Scene Management
    static float DeltaTime();
    static double DeltaTimeD();
    static void LoadingStatus(uint32 &uiNumQueuedOut, uint32&uiTotalOut);
    static void PauseGame(bool bPause);
    ```

-   [:material-controller:{.hyindicator}ㅤ**Input Handling**](./input.md)  
    Utilize Input Maps and get player input from various devices.
    ``` cpp
    // Input Handling
    static HyInput &Input();
    ```

-   [:material-volume-high:{.hyindicator}ㅤ**Audio System**](./audio.md)  
    Manage how `HyAudio2d` audio cues are played back, categories, and settings.
    ``` cpp
    // Audio System
    static HyAudioCore &Audio();
    ```

-   [:material-bug-outline:{.hyindicator}ㅤ**Diagnostics & Debugging**](./diagnostics.md)  
    
    ``` cpp
    // Diagnostics & Debugging
    static HyDiagnostics &Diagnostics();
    ```

-   [:material-shape-outline:{.hyindicator}ㅤ**Shaders**](./shaders.md)  
    
    ``` cpp
    // Shaders
    static HyShaderHandle DefaultShaderHandle(HyType eType);
    ```

-   [:material-database-outline:{.hyindicator}ㅤ**Direct Asset Loading**](./direct-assets.md)  
    
    ``` cpp
    // Direct Asset Loading
    static std::string DataDir();
    static HyTextureQuadHandle CreateTexture(std::string sFilePath, HyTextureInfo textureInfo);
    static HyAudioHandle CreateAudio(std::string sFilePath, bool bIsStreaming = false, int32 iInstanceLimit = 0, int32 iCategoryId = 0);
    ```

</div>

