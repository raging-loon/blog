---
layout: post
title:  "Article Collection"
date:   2024-06-16 11:53:00 -0400
---

Welcome to the Kestrel Development Blog. Here I will document the creation of a Network Intrusion Detection System.

The repository is located [here](https://github.com/raging-loon/Kestrel).

Here are the high level goals:
1. Should run on almost anything. Windows, Linux, Mac, in containers, etc. 
2. Should have minimal system requirements. My goals is < 1GB RAM and a 1GHz processor
3. Should be able to be containerized (Docker)
4. *Fast* pattern matching
5. Easy-to-use, flexible, and extensible rule language
6. Integration with popular SIEMs. I will be using the ELK stack during development
7. Connection Tracking

Here are some low-level goals/ideas that I have:
1. Separate rule compiler
    - Either bytecode or some type of serialized data structure like a graph
2. Lua scripts for customized actions
3. Protocol Modules
    - Similar to what YARA has. 
    - You could load the TCP module and match ANY field using it

What will I be using for development?
1. C++20
2. GoogleTest for unit testing
3. libpcap when possible and npcap for Windows
4. CMake as a build system

This project is just getting started, so there is not much content.

If you have an issue, request, fix, etc. please submit an [issue](https://github.com/raging-loon/Kestrel/issues).

## Sections

1. Getting Started
    * [Setting up the environment, unit tests, and capturing some packets](/blog/getting-started/2024/11/14/Getting-Started.html)
    * Overall Design

