cmake_minimum_required(VERSION 3.3)
project(SoFixer)





set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
if(MINGW)
    message("build with mingw")
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -static -static-libgcc -static-libstdc++")
endif()

set(ROOT_SRC ElfReader.cpp
        ElfRebuilder.cpp
        ObElfReader.cpp)

message("building SoFixer for 64bit target")
add_definitions("-D__SO64__")
set(TARGET_NAME SoFixer64)
add_executable(${TARGET_NAME} ${ROOT_SRC} main.cpp)

message("building SoFixer for 32bit target")
add_definitions("-D__SO32__")
set(TARGET_NAME SoFixer32)
add_executable(${TARGET_NAME} ${ROOT_SRC} main.cpp)
