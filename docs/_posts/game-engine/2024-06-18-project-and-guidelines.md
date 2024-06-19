---
layout: post
title:  "Radium Engine: Project and Guidelines"
date:   2024-06-17 2:46:00 -0400
categories: game-engine
---
# The Project
For development I will be using Visual Studio 2022. I will start by creating a new project. I am choosing a CMake project (you may have to update your visual studio install) so I can port to Linux easily.

My game engine is called "Radium Engine". This is because it sounds cool. My apologies if this coincides with the name of your engine or tool, I am bad at naming and there so such thing as unique name anymore.

In my CMake file I will start by adding a CMake argument for enabling DirectX 12, then add spdlog as an include directory.

Note that VS2022 by default will create two CMakeFiles:
```
radium-engine/
├── CmakeLists.txt  
├── radium-engine/
    ├── CMakeLists.txt
```

The first includes the second. I will be putting macro definitions and include directories in first, and libraries in the second.

```cmake
# Outer CmakeLists.txt

# Enable Hot Reload for MSVC compilers if supported.
if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

project ("radium-engine")
option(RAD_API_DIRECTX12 "Compile DirectX 12 code and link" ON)
option(ENABLE_DUMMY_MAIN "Compile tests/dummymain.cpp for testing purposes" ON)


# Include sub-projects.
add_subdirectory ("radium-engine")
target_include_directories("radium-engine" PUBLIC
	"${CMAKE_CURRENT_SOURCE_DIR}/external/spdlog/include"
)

```
```cmake
# Inner CMakeLists.txt

# Add source to this project's executable.

if(ENABLE_DUMMY_MAIN)
	set(SOURCES ${SOURCES} "../tests/dummymain.cpp")
	add_definitions("/DENABLE_DUMMY_MAIN=1")
endif(ENABLE_DUMMY_MAIN)

add_executable (radium-engine ${SOURCES})


if (CMAKE_VERSION VERSION_GREATER 3.12)
  set_property(TARGET radium-engine PROPERTY CXX_STANDARD 20)
endif()

if(RAD_API_DIRECTX12)
	message("Compiling with Direct12 Support")
	add_definitions("/DRAD_API_DIRECTX=1")

	target_link_libraries("radium-engine" PUBLIC
		D3D12.lib d3dcompiler.lib dxgi.lib dxguid.lib
	)
endif(RAD_API_DIRECTX12)


```

The plan I have in mind is to have a ```dummymain.cpp``` file for testing. It will start and stop the engine and feed data to it. 
Then, the engine will be compiled as a library and linked with the scene editor. When you make a game in the editor, it will automatically create a ```dummymain.cpp``` file that loads whatever resources are need by your game, then links it with the engine. 
This idea may change over time.

This is what my dummymain file looks like:
```cpp
// defined in the root CMakeLists.txt
#ifdef ENABLE_DUMMY_MAIN

#include "radium-engine.h"
#include <spdlog/spdlog.h>

int main(int argc, char** argv)
{
    spdlog::info("Hello, World");
    return 0;
}
#endif // ENABLE_DUMMY_MAIN

```

Now my project looks like this:
```
radium-engine/
├── external
    ├── spdlog
├── radium-engine
    ├── CMakeLists.txt
    ├── radium-engine.h
├── tests
    ├── dummymain.cpp
├── CMakeLists.txt
```

And if I run it:![Alt text](/blog/assets/ge-hw-test.png)