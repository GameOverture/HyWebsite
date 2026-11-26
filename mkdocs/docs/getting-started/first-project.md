Our goal here is to speedrun a simple game to cover some of Harmony Engine's major features. It assumes you have already done the steps in the [Installation & Setup](install.md) section.

## 1. Create Project

With HyEditor open go to `File > New Project` from the main menu which opens the **New Project** dialog.

<div class="grid" markdown>
<figure>
  <img src="../img/getting-started/flappy-new-project.png">
  <figcaption> See <a href="../editor/projects.html#creating-a-new-project">Projects</a> section for more information</figcaption>
</figure>

- Type the **Game Title** that you want, in this example it's "Flappy". The **Code Name** will update automatically to match, and will be used to name the main C++ class.
- Specify where you want this to game reside on your PC using **Project Location** and leave the rest default.
- Press OK
</div>

The ![Flappy Project Icon](../img/editor/Project.png) Flappy project should now appear in the [Project Explorer](../editor/projects.md#project-explorer) window. Click the project to activate it ![Activated Flappy Project Icon](../img/editor/Project-Pending.png).

---
<center><h3>Generate a build<h3></center>

With your project activated the [Asset Manager](../editor/asset-manager.md) (and everything else) will now be linked to this project. Click the ![Code Icon](../img/editor/code.png) Code tab within it.

Press the ![New Build](../img/editor/Build-New.png) button to generate a new build. If you are using Visual Studio, it should detect your version. Use the other default values and press OK.

![Build Log](../img/getting-started/flappy-new-build.png)

In the background HyEditor will generate the build within your **Project Location**, but all configuration for it can be done within HyEditor.
Once the build has fully generated you can click ![Open Build](../img/editor/Build-Open.png) to launch Visual Studio (or whatever else you configured). We'll begin coding later on, but it should build and run an empty window at this point.

!!! warning "Don't use Visual Studio (or any external tool) to modify the build settings"
    Adding or Removing files, creating folders, modifying code dependencies or other build settings should all be done within HyEditor. When changes are made in HyEditor it informs and updates CMake. Visual Studio will detect the change upon `Build Solution` and refresh.


## 2. Import Assets

Download the following free asset packs that will be used in this example:
<div class="grid cards" markdown>

-   [:material-palette-outline:{.hyindicator}ㅤ**Flappy Bird Assets**](https://megacrash.itch.io/flappy-bird-assets)  
    Pixel Art by MegaCrash on itch.io<br>
    [![Art Download Preview](../img/getting-started/flappy-art-download.png)](https://megacrash.itch.io/flappy-bird-assets)

-   [:material-volume-high:{.hyindicator}ㅤ**Impact Sounds!**](https://nvthicprod.itch.io/impact-sfx)  
    Sound Effects by Nvthic Sounds on itch.io<br>
    [![Sfx Download Preview](../img/getting-started/flappy-sfx-download.png)](https://nvthicprod.itch.io/impact-sfx)

-   [:material-format-font:{.hyindicator}ㅤ**MANAspace font**](https://www.zone38.net/font/#mana)  
    TrueType font by codeman38 on zone38.net<br>
    [![Font Download Preview](../img/getting-started/flappy-font-download.png)](https://www.zone38.net/font/#mana)
</div>

You can extract the zip files anywhere on your PC. The assets will be copied into the project when importing below (no longer referencing the original location).

---
<center><h3>Player Assets</h3></center>

Continuing with the [Asset Manager](../editor/asset-manager.md), click the ![Atlas Icon](../img/editor/atlas-file.png) Atlases tab within it.

Press the ![Import Sprite Sheet Icon](../img/editor/slice-sprite-sheet.png) button at the bottom to **Import a Sprite Sheet**

<div class="grid" markdown>
<figure>
  <img src="../img/getting-started/flappy-import-player.png">
  <figcaption></figcaption>
</figure>

- Click `Browse..` and locate the extracted `Flappy Bird Assets/Player` directory and choose from either style, selecting either `AllBird1.png` or `AllBird2.png`
- Rename "Filter name" to `Player`
- Change the Tile Size X and Y to be `16`
- Rename "Frames' base name" to be `Player`
- You can zoom/pan the preview window with ++w++ ++a++ ++s++ ++d++ and ++middle-button++ :material-mouse-scroll-wheel:
- Press OK, and confirm importing 28 assets.
</div>

You should now have a new filter in the tree view called `Player` that contains the 28 sliced images.

!!! tip annotate "Specify where new assets and filters get placed into"
    In the Asset Manager, what you have selected determines where new items are placed into. To place new items to the root (and not within the `Player` filter) make sure to deselect all items by clicking an empty region in the Atlas Manager's tree view. (1)

1. ![Import Clear Tip](../img/getting-started/flappy-import-cleartip.gif)

---
<center><h3>Pipe Assets</h3></center>

Within the [Asset Manager](../editor/asset-manager.md), right-Click :material-mouse-right-click: an empty region in the tree view and select "![Create Filter](../img/editor/Filter-New.png) Add Filter" in the context menu. Name it `Pipes`, press OK, then select the newly created filter by clicking it.

Press the ![Import Sprite Sheet Icon](../img/editor/slice-sprite-sheet.png) button again, but this time we'll need to adjust the slicing options. Starting with slicing the **Tops**.

<div class="grid" markdown>
<figure>
  <img src="../img/getting-started/flappy-import-pipetops.gif">
  <figcaption></figcaption>
</figure>

- Click `Browse..` and locate the extracted `Flappy Bird Assets/Tiles` directory and choose a style, selecting either `PipeStyle1.png`, or `PipeStyle2.png`, etc.
- Rename "Filter name" and "Frames' base name" to be `Tops`
- Depending on which style you choose your slicing options will vary.

!!! tip "Setting Slicing Options"
    You can use your mouse wheel :material-mouse-scroll-wheel: to change slicing option values and preview the changes quickly.
</div>

Select the `Pipes` filter you created earlier and repeat the ![Import Sprite Sheet Icon](../img/editor/slice-sprite-sheet.png) process for the **Bodies** and then **Bottoms**. For `PipeStyle1.png`, the slicing options values are shown here:
<div class="grid" markdown>
![Import Sprite Sheet Icon](../img/getting-started/flappy-import-pipebodies.png)

![Import Sprite Sheet Icon](../img/getting-started/flappy-import-pipebottoms.png)
</div>

---
<center><h3>Ground Assets</h3></center>

Within the [Asset Manager](../editor/asset-manager.md), right-Click :material-mouse-right-click: an empty region in the tree view and select "![Import Sprite Sheet Icon](../img/editor/slice-sprite-sheet.png) Import Sprite Sheet(s)" in the context menu.

<div class="grid" markdown>
<figure>
  <img src="../img/getting-started/flappy-import-ground.png">
  <figcaption></figcaption>
</figure>

- Click `Browse..` and locate the extracted `Flappy Bird Assets/Tiles` directory and choose a style, selecting either `SimpleStyle1.png`, or `SimpleStyle2.png`, etc.
- Rename "Filter name" and "Frames' base name" to be `Ground`
- Depending on which style you choose your slicing options will vary.
</div>

---
<center><h3>Background Assets</h3></center>

<div class="grid" markdown>
Within the [Asset Manager](../editor/asset-manager.md), right-Click :material-mouse-right-click: an empty region in the tree view and select "![Create Filter](../img/editor/Filter-New.png) Add Filter" in the context menu. Name it `Backgrounds`, press OK, then select the newly created filter by clicking it.
<br><br>
The backgrounds are individual images so we can simply press the ![Import Images](../img/editor/AtlasFrame.png) button, browse to the extracted `Flappy Bird Assets\Background` directory and select 1 or more background images that you want.
<br><br>
This example is going to cycle day and nights as a run progresses using images: `Background1.png`, `Background2.png`, `Background3.png`, `Background4.png`, `Background5.png`, and `Background6.png`

<figure>
  <img src="../img/getting-started/flappy-assets.png">
  <figcaption>Your <a href="../editor/asset-manager.html">Asset Manager</a> should look something like this</figcaption>
</figure>
</div>

## 3. Setup Prefabs

Prefabs are used to initalize components like sprites and text when programming the game. They are created and arranged into *prefixes*(1) in the [Project Explorer](../editor/projects.md#project-explorer) window.
{ .annotate }

1. Prefixes are a folder hierarchy that can be used to organize [Prefabs](../editor/prefabs/index.md) and [Entities](../editor/entities.md) into logical groups and help avoid name clashing. The full path includes the prefix and name, creating a string that is case-insensitive, delimited with `/` For example: "RootPrefix/SubPrefix/PrefabName"

<!-- ------------------------------------------------------------------------------------------------------------------------------- -->
---
<center><h3>Player Prefab</h3></center>

<div class="grid" markdown>

- Right-click :material-mouse-right-click: on your active project ![Active Project Icon](../img/editor/Project-Pending.png) **Flappy**
- Select **New Item**→![New Sprite Icon](../img/editor/Sprite-New.png) **New Sprite** in the context menu
- Set the "Sprite Name" to be `Player`, and leave the rest default
- Press OK

<figure>
  <img src="../img/getting-started/flappy-new-sprite.png">
  <figcaption>Not setting a prefix will place it in the root, and its path is just the name "Player"</figcaption>
</figure>

</div>

<div class="grid" markdown>

- Choose a color among the imported player frames within the [Asset Manager](../editor/asset-manager.md)
- The ![Sprite Icon](../img/editor/Sprite.png) **Player** sprite is going to have three states: `Idle`, `Flap`, and `Bonk`

<figure>
  <img src="../img/getting-started/flappy-player-state.png">
  <figcaption>Begin by renaming state '0' to `Idle`</figcaption>
</figure>

</div>

<figure>
  <img src="../img/getting-started/flappy-player-idle.gif">
  <figcaption>Drag the first 2 player frames from the chosen color into the main window</figcaption>
</figure>

<figure>
  <img src="../img/getting-started/flappy-player-idlesettings.gif">
  <figcaption>Check the <b>Looping</b> checkbox, and set the Frame Rate to <code>0.250sec</code></figcaption>
</figure>

<figure>
  <img src="../img/getting-started/flappy-player-flap.gif">
  <figcaption>Create the <code>Flap</code> state, drag all 4 frames into the main window, check the <b>Bounce</b> checkbox, and set the Frame Rate to <code>0.050sec</code></figcaption>
</figure>

<figure>
  <img src="../img/getting-started/flappy-player-bonk.gif">
  <figcaption>Finally create the <code>Bonk</code> state, drag all 4 frames into the main window again, check the <b>Looping</b> checkbox, and crank up the Frame Rate</figcaption>
</figure>

!!! tip "Save your work"
    Be sure to **File**→![Save Icon](../img/editor/file-save.png) **Save** or press ++ctrl++ + ++s++ when you make changes to Prefabs

<!-- ------------------------------------------------------------------------------------------------------------------------------- -->
---
<center><h3>Pipe Prefabs</h3></center>

Creating the pipe Prefabs will be a little different. Pipes will be assembled between three Prefabs `Top`, `Body`, and `Bottom`, where each state will correspond to a color.

- Right-click :material-mouse-right-click: on your active project ![Active Project Icon](../img/editor/Project-Pending.png) Flappy
- Select **New Item**→![New Prefix Icon](../img/editor/Prefix-New.png) **New Prefix** in the context menu
- Set the "Prefix Name" to be `Pipes`, and leave the rest default, and press OK

<br>

<div class="grid" markdown>

- Now right-click :material-mouse-right-click: on the newly created ![Prefix Icon](../img/editor/Prefix.png) **Pipes** prefix
    - Select **New Item**→![New Sprite Icon](../img/editor/Sprite-New.png) **New Sprite** in the context menu
- Set the "Sprite Name" (`Top`, `Body`, or `Bottom`), the Prefix will already have `Pipes` set since our context menu was invoked from it
- Press OK

<figure>
  <img src="../img/getting-started/flappy-pipe-prefabs.png">
  <figcaption></figcaption>
</figure>
</div>

<div class="grid" markdown>

- Within [Asset Manager](../editor/asset-manager.md)'s tree view, the ![Filter Icon](../img/editor/Filter.png) **Pipes** filter has a sub-filter for each pipe Prefab `Top`, `Body`, and `Bottom`
- Drag a single corresponding pipe frame into the main view and then create a new state, repeating for each color
    - Should be 8 states total (0-7)
    - Make sure to keep the state/color order between the three pipe Prefabs the same

<figure>
  <img src="../img/getting-started/flappy-pipe-creation.gif">
  <figcaption>Repeat this process three times in the Pipes prefix creating <b>Body</b>, <b>Bottom</b> and <b>Top</b></figcaption>
</figure>

</div>

<!-- ------------------------------------------------------------------------------------------------------------------------------- -->
---
<center><h3>Background & Ground Prefab</h3></center>

Create a Sprite Prefab for the `Background`. Just like one of the pipe parts, make a state for each background image.

Additionally, set the offset for each state to be anchored at the bottom left (`0, 0`) by pressing the ![Align Left](../img/editor/sprite-alignLeft.png) and ![Align Bottom Icon](../img/editor/sprite-alignBottom.png) buttons.

<figure>
  <img src="../img/getting-started/flappy-backgrounds.png">
  <figcaption>There's 6 total states (0-5) for the <code>Background</code> Prefab in this example</figcaption>
</figure>

Also Create a Sprite Prefab for the `Ground`. Offset each state to be anchored at the bottom left (`0, 0`). It will be have 2 states for each ground piece we sliced.

<figure>
  <img src="../img/getting-started/flappy-ground-prefab.png">
  <figcaption>There's 2 total states (0-1) for the <code>Ground</code> Prefab in this example</figcaption>
</figure>


<!-- ------------------------------------------------------------------------------------------------------------------------------- -->
---
<center><h3>Text Prefab</h3></center>

HyEditor will scan your OS's standard location for available fonts. Creating Text Prefabs requires choosing a font file, and by default **System-wide** fonts installed on your PC and fonts found in the `<Project Location>/meta/Fonts` directory.  

Compatible fonts are **.ttf** (TrueType Fonts) and most **.otf** (OpenType Fonts).
!!! note "User-specific installed fonts will not be found"
    Only system-wide fonts that are accessible to all user accounts will be available to choose from. If you want to use a downloaded font, be sure to "Install for all users", or manually place the font in the `<Project Location>/meta/Fonts` directory.

<div class="grid" markdown>
<figure>
  <img src="../img/getting-started/flappy-new-text.png">
  <figcaption>Not setting a prefix will place it in the root, and its path is just the name "Menu"</figcaption>
</figure>

- Right-click :material-mouse-right-click: on your active project ![Active Project Icon](../img/editor/Project-Pending.png) Flappy
- Select **New Item**→![New Text Icon](../img/editor/Text-New.png) **New Text** in the context menu
- Set the "Text Name" to be `Menu`, and leave the rest default
- Press OK
</div>

![Text Prefab Creation](../img/getting-started/flappy-text.png)

## 4. Setup Entities

When programming, you can create one or many Node instances of the Prefabs that you just made. Entities (`HyEntity`) are a way you can logically combine these Nodes to represent more complex objects, entire levels, etc. By extending your own class from `HyEntity` you can implement your own logic on how it controls its child Nodes.

When you create an entity in HyEditor you can visually preview what the class will look like after being loaded, and its members initialized.

Right-click :material-mouse-right-click: on your active project ![Active Project Icon](../img/editor/Project-Pending.png) Flappy and **New Item**→![New Prefix Icon](../img/editor/Prefix-New.png) **New Prefix** called `Scenes`

<div class="grid" markdown>

- Within the ![Prefix Icon](../img/editor/Prefix.png) **Scenes** prefix, create a ![New Entity Icon](../img/editor/Entity-New.png) **New Entity** called `Gameplay`
- Within the [Project Explorer](../editor//projects.md#project-explorer) drag and drop ![Sprite Icon](../img/editor/Sprite.png) **Background** into the main view to create a Node of that Prefab called `m_Background`
- ㅤ:material-numeric-1-circle:{.hyindicator}ㅤWith `m_Background` Node selected, change the **Sprite**→**State** to `1` (the noon-daylight background)
- ㅤ:material-numeric-2-circle:{.hyindicator}ㅤChange the **Sprite**→**Texture Tiling** to be `2 x 1`
- ㅤ:material-numeric-3-circle:{.hyindicator}ㅤAfter tiling <code>m_Background</code> you will notice a seam where it wraps

<figure>
  <img src="../img/getting-started/flappy-entity-seam.png">
  <figcaption></figcaption>
</figure>
</div>

---
<center><h3>Resolving the seams</h3></center>

The seams in a tiling Sprite are due to texture filtering and atlas packing settings. By default assets are assigned `Bilinear` filtering, which samples the four nearest texels and calculates a weighted average to create a smooth gradient. The seams you are seeing on the edges are sampling the nearby transparent texels around the actual image (as it sits on the texture atlas).

<figure>
  <img src="../img/getting-started/texture-filters.png">
  <figcaption>Filtering difference if you were to zoom into a texture's texels</figcaption>
 </figure>

To fix this we can set an **extrude** value on the atlas packing settings. This duplicates the outermost texels of each atlas frame into the surrounding padding area to prevent texture bleeding. In our case it will prevent `Bilinear` filtering from sampling transparent texels when tiling.

<div class="grid" markdown>

- ![Save Icon](../img/editor/file-save.png) **Save** all open items
- Within the [Asset Manager](../editor/asset-manager.md) in the **Bank** groupbox, change the ![Settings Icon](../img/editor/generic-settings.png) **Atlas Bank Settings** → **Packing Options** → **Extrude Amount** to `1`
- Regenerate the Atlas Bank
- Optionally change all the assets' properties to use `Nearest` filtering

<div class="grid cards" markdown>
-   <h1>:material-check-bold:{.hyindicator}ㅤChange assets to **Nearest filtering** (recommended)</h1> 
    This filtering results in sharp, blocky, pixelated visuals which matches the intended art style. 
    - Within the [Asset Manager](../editor/asset-manager.md) in the tree view area, select all items (click in tree view then press ++ctrl++ + ++a++)
    - Right-click :material-mouse-right-click: on the selected items and choose ![Asset Properties Icon](../img/editor/AtlasFrame-Settings.png) **Asset Properties**
    - Change **Filtering** to `Nearest` and press OK
    - Repack the assets
</div>
</div>

!!! tip "When using Nearest filtering"
    Having the assets use `nearest` filtering naturally avoids the seam problem all together if the camera's position is snapped to whole pixels. However even with `nearest` filtering there are a few sub-pixel coordinates that can still cause a seam to be seen. So it's a good idea to set the **extrude** amount in the ![Settings Icon](../img/editor/generic-settings.png) **Atlas Bank Settings** regardless of which texture filtering you choose.
---

...continuing with our entity ![Entity Icon](../img/editor/Entity.png) **Gameplay**

- Within the [Project Explorer](../editor//projects.md#project-explorer) drag and drop ![Sprite Icon](../img/editor/Sprite.png) **Ground** into the main view to create a Node of that Prefab called `m_Ground`
- Change **Sprite** → **Texture Tiling**: `8 x 1`

## 5. Programming the Game

