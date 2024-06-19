---
layout: post
title:  "Game Engine Series: Application Framework"
date:   2024-06-17 2:46:00 -0400
categories: game-engine
---
# The Project
For development I will be using Visual Studio 2022. I will start by creating a new project. I am choosing a CMake project (you may have to update your visual studio install) so I can port to Linux easily.

My game engine is called "Radium Engine". This is because it sounds cool. My apologies if this coincides with the name of your engine or tool, I am bad at naming and there so such thing as unique name anymore.

Once that is finished I will add the appropriate include directories, preprocessor definitions, library directories, and libraries.

For DirectX 12, you MUST list these libraries in Visual Studio's Linker Input:
* D3D12.lib
* d3dcompiler.lib
* dxgi.lib
* dxguid.lib


Note: from now on I will be referring to DirectX 12 as "DX12" or "D3D12".
