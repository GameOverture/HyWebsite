Welcome to the official documentation for **HyEngine** — a fully-featured, cross-platform 2D game engine and editor designed for developers who want **total control** over their game code while still benefiting from a powerful WYSIWYG editor for asset management, animation workflows, entities, UI, and build automation.

HyEngine is built for **programmer-focused game development**, combining:
- A robust C++ runtime engine (HyEngine)
- A powerful GUI editor and asset pipeline (HyEditor)
- A fully automated CMake-based build system
- Optional WebAssembly targets via Emscripten

---

## 🚀 What is HyEngine?

HyEngine is a modern, scalable 2D engine designed for studios or solo developers who want:

- **Direct control over code** — no “black box” systems  
- **A true offline asset pipeline** — Atlases, fonts, audio cues, tilesets  
- **Editor-built Entities** that auto-generate clean C++ classes  
- **Deterministic simulation**, physics through Box2D  
- **Custom rendering pipelines** with OpenGL/WebGL  
- **Cross-platform builds** managed by CMake under the hood  
- **Instant iteration** by regenerating assets and project files in HyEditor

HyEditor and HyEngine work together to handle the annoying parts:
- Importing and organizing assets  
- Creating atlases and sub-atlases  
- Managing C++ source files  
- Visual layout and animation timelines  
- Generating Entity classes  
- Handling Spine animation data  
- Managing builds for Windows / Linux / Web  

Leaving you free to write actual gameplay code.

---

## 📚 Documentation Sections

### ▶️ **Getting Started**
Learn how to install HyEditor, configure your environment, and compile the Engine.

- [Installation](installation.md)
- [Directory Structure](structure.md)
- [Creating Your First Project](getting-started.md)

---

### 🧩 **Fundamentals**
Understand the core concepts behind the engine and editor.

- Asset Pipeline  
- Project Items (Sprites, TileMaps, Text, Spine, Particles, Audio, Entities)  
- States  
- Nodes  
- Animation Floats  
- Entities & physics shapes  
- Meta vs Data  

Start here if you're new to the workflow.

---

### ⚙️ **Engine Programming**
Everything related to writing C++ gameplay code:

- Nodes and scene management  
- Entities and composition  
- Physics & shapes  
- Rendering and custom shaders  
- Input  
- Time systems  
- UI widgets & UI containers  
- Loading Editor-generated content  
- Hot-loading raw assets  

---

### 📖 **API Reference**
Organized by system:

- Core utilities  
- Graphics  
- Physics (Box2D integration)  
- Input  
- Audio  
- UI system  
- Math / RNG / JSON helpers  

---

### 🧪 **HyExamples**
Official example projects demonstrating:

- Basic rendering and scene graphs  
- Sprites and animations  
- TileMap usage  
- Loading Spine skeletons  
- Using Entities in code  
- UI examples  
- Physics examples  
- WebAssembly builds  

Browse the examples:  
**[HyExamples →](examples/index.md)**

---

## 🛠 Technologies

**Engine:**  
OpenGL, SDL2/GLFW, Box2D, glad, glm, stb, JSON (nlohmann or rapidjson)

**Editor:**  
Qt6, freetype2, freetype-gl, libogg/vorbis

**Build System:**  
CMake, Emscripten, MSVC, Clang, GCC

---

## ✨ Why HyEngine?

HyEngine focuses on three goals:

1. **Full control at the code level**  
2. **A powerful editor that handles the tedious parts**  
3. **A clean, deterministic, production-ready pipeline**

Whether you're building a cinematic platformer, a simulation-heavy title, or a VFX-intense 2D game, HyEngine provides the tools without locking you into a specific workflow.

---

## 📎 Next Steps

→ **[Install HyEngine](installation.md)**  
→ **[Learn the fundamentals](fundamentals/overview.md)**  
→ **[Build your first Entity](engine/entities.md)**  

Let’s build something amazing.

