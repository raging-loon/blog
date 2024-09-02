---
layout: post
title:  "Article Collection"
date:   2024-06-16 11:53:00 -0400
---
<!-- ---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
--- -->
Welcome to Game Dev From Scratch.

In this series of articles, I will be building an Isometric game engine.

Here are my general guidelines:
2. Absolutely NO STL
3. Exceptions should be disabled 
4. The ANSI C standard library is able to be used
5. The end product should run on Windows, all major Linux distributions, and perhaps MacOS.

Scott Meyers described C++ as four languages in a trenchcoat: C, Objected Oriented C++, Template C++, and STL. I will be using all of these 'languages' except for STL.

Why not STL? For starters, it would defeat the purpose of this project ('From Scratch'), and 2. it is unwieldly, slow, and can be an utter pain in the rear to debug (what is `orphan_locked_v3`?? why is it in my `vector`??)

What am I making? My goal is to create an engine that can run an Isometric game (which I will also be developing). The game will have graphics similar to Stronghold Crusader and the first couple Fallout games.
I am not sure exactly what the game will be about, but fortunately I will have plenty of time to think about it :) (probably WW2).

Why am I doing this to myself? For a few reasons:
1. I *really* enjoy building things from the ground up
2. I want to experience all avenues of engine development
3. It will (hopefully) be impressive to employers
4. ~~[Linux Torvalds made me feel like a 'substandard' programmer](https://lwn.net/Articles/249460/)~~

What tools will I be using?

1. C++20 - the main language. I may have some python or bash scripts laying around, though.
2. CMake - My ~~cursed~~ build system
3. Visual Studio for development on Windows, VSCode on Linux
4. OpenGL and GLEW
6. Git as a VCS
7. GTest

This engine will be called the "Radium Engine" because it sounds like a cool name.

Finally, this series of articles is not meant to teach you everything. I am not going to teach C++ or graphics programming or vector algebra. I am simply documenting the development and design decisions of the engine.

Without further ado, here is the table of contents:

1. [Design](/blog/design/2024/02/09/Design.html)
2. [logging](/blog/logging/2024/07/07/Radium-Logger.html)

