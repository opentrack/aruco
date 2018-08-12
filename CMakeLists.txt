cmake_minimum_required(VERSION 2.6)
project(aruco)

find_package(OpenCV REQUIRED)

if(WIN32)
    add_definitions(-D_CRT_SECURE_NO_WARNINGS)
endif()

if(NOT (CMAKE_SYSTEM_NAME STREQUAL "Windows") AND CMAKE_COMPILER_IS_GNUCXX)
    add_definitions(-fPIC)
endif()

add_definitions(-DARUCO_STATIC)

add_subdirectory(src)
add_subdirectory(utils)
