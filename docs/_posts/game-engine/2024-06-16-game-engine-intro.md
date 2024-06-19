---
layout: post
title:  "Game Engine Series: Introduction"
date:   2024-06-16 2:46:00 -0400
categories: game-engine
---
# Introductions
Welcome to my game engine development series. This is designed to document the creation of my game engine from the ground up. This is a learning experience for me as well so there will be entire articles dedicated to theory. I am not a professional developer (yet) so please submit any errata to [my email](mailto:cxmacolley@gmail.com).

# Goals
With all of that in mind, let us outline some goals for this project:
1. Real-time rendering of 3D meshes complete with lighting and texturing
2. Provide a clean abstraction layer over DirectX 12, 11, and eventually Vulkan
3. Create a scene-graph or tree for describing and searching for objects in a scene
4. Provide a scripting API through which game logic can be written
5. Provide a scene editor to make game development easier
6. A completely data driven architecture
7. Make a game

You might be asking: "Why not just use a pre-exising engine?" The answer is that I would...if my goal were to just make a game. I aim to learn the following by completing this project:
* Graphics APIs, specifically DirectX
* Optimization
* Management of large software projects
* Unit testing
* Implementation of design patterns
* C++ Development best practices

# Tools
* Visual Studios 2022 - for its wonderful debugger and ease of building
* C++20 - mainly for its support of Designated Initializers and possible abbreviated function templates.
* DirectX 12
 
    - This is a powerful, low level API. I am choosing it over OpenGL for the following reasons:
        * OpenGL can be slow and clunky (e.g. glSetUniform)
        * OpenGL abstracts away low level functionality such as pipelines and command lists
* SPDLOG - A fast logging library
* ASSIMP - "Asset Importer" - this can import 100s of different 3D file formats. I plan to use it so I can load models into the engine without much thought as to the specifics of their respective formats.
* RenderDoc - a graphics debugger

These are tools that I might end up using:
* ENTT - A fast entity-component-system
* GLFW/SDL - for when I port this engine to Linux

# Resources
Here is a list of resources I will be using to aid me

* Books
    *   Introduction To 3D Game Programming with DirectX 12 - Frank Luna
    *   Real-Time Renderering (4th ed.) - Akenine-Möller et. al.
    *   Game Engine Architecture (3rd ed.) - Jason Gregory
    *   Design Patterns: Elements of Reusable Software - Gang of Four
    *   Essential Mathetematics for Games and Interactive Applications - Verth (2015)
    *   Effective Modern C++ - Scott Meyers
* Websites
    *   DirectX 12 Documentation on MSDN
    *   Various repositories on GitHub (I will credit them as I come across them)


## Next 
[Project and Guidelines](/blog/game-engine/2024/06/17/project-and-guidelines.html)