cmake_minimum_required(VERSION 3.10)
project(aruco)

set(CMAKE_POSITION_INDEPENDENT_CODE TRUE)
set(CMAKE_C_VISIBILITY_PRESET hidden)
set(CMAKE_CXX_VISIBILITY_PRESET hidden)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_DEFAULT 17)
set(CMAKE_CXX_STANDARD_REQUIRED FALSE)
set(CMAKE_CXX_EXTENSIONS FALSE)

add_definitions(-DARUCO_STATIC)

find_package(OpenCV REQUIRED)

if(WIN32)
    add_definitions(-D_CRT_SECURE_NO_WARNINGS -DWIN32_LEAN_AND_MEAN -DNOMINMAX)
endif()

if(MSVC)
    add_definitions(-D_HAS_EXCEPTIONS=0)
endif()

add_subdirectory(src)
add_subdirectory(utils)
