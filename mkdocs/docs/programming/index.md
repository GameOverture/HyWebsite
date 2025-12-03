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
    The member variables declared in your main game class encapsulate the flow or main components of the program. These are usually custom classes derived from `HyEntity2d` (1).

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

## Global Engine Utilities

The `HyEngine` base class provides public static methods to access global engine functionality and information.
``` cpp
// Above setup
static bool IsInitialized();
static const HarmonyInit &InitValues();
static std::string DateTime();

// Windows & Cameras
static uint32 NumWindows();
static HyWindow &Window(uint32 uiWindowIndex = 0);

// Scene Management
static float DeltaTime();
static double DeltaTimeD();
static void LoadingStatus(uint32 &uiNumQueuedOut, uint32&uiTotalOut);
static void PauseGame(bool bPause);

// Input Handling
static HyInput &Input();

// Audio System
static HyAudioCore &Audio();

// Diagnostics & Debugging
static HyDiagnostics &Diagnostics();

// Shaders
static HyShaderHandle DefaultShaderHandle(HyType eType);

// Direct Asset Loading
static std::string DataDir();
static HyTextureQuadHandle CreateTexture(std::string sFilePath, HyTextureInfo textureInfo);
static HyAudioHandle CreateAudio(std::string sFilePath, bool bIsStreaming = false, int32 iInstanceLimit = 0, int32 iCategoryId = 0);
```

## Next Steps
More information for the above functions and more can be found in:

→ **[Windows & Cameras](./windows-cameras.md)**  
→ **[Scene Management](./scene/index.md)**  
:material-arrow-right-bottom: [Item Nodes](./scene/item-nodes.md) | [Entities & Physics](./scene/entities.md) | [User Interface](./scene/user-interface.md)  
→ **[Input Handling](./input.md)**  
→ **[Audio System](./audio.md)**  
→ **[Diagnostics & Debugging](./diagnostics.md)**  
→ **[Shaders](./shaders.md)**  
→ **[Direct Asset Loading](./direct-assets.md)**  

