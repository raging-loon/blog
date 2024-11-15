---
layout: post
title: "Getting Started"
categories: getting-started
---
<link rel="stylesheet" href="{{ "/assets/css/styles.css" | relative_url }}">
# Getting Started

## The Build Script

I am using CMake for this. My idea is to have one top level "project" that kicks off the building of that actual projects (e.g. sensor, compiler, various libraries).

My directory structure looks like this:
```
📦kestrel
 ┣━ 📂build
 ┣━ 📂sensor
 ┃ ┣━ main.cpp
 ┃ ┣━ CMakeLists.txt
 ┣━ CMakeLists.txt
```
So the top level CMakeLists would add every project as a subdirectory and make sure everything ends up in the build directory:

```cmake
cmake_minimum_required(VERSION 3.10)

# Enable Hot Reload for MSVC compilers if supported.
if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

set(CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD 20)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}/build/")
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}/build/")

add_subdirectory(sensor)

```

Then in the sensor directory, we have an actual project:
```cmake

project(kestrel-sensor VERSION 0.1)

add_executable(kestrel-sensor 
    main.cpp
)

target_include_directories(
kestrel-sensor 
PUBLIC
    "${CMAKE_CURRENT_SOURCE_DIR}"
)

```

Our `main.cpp` file just contains hello.



