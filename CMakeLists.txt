cmake_minimum_required(VERSION 2.6)
project(aruco)

set(CMAKE_POSITION_INDEPENDENT_CODE TRUE)

find_package(OpenCV REQUIRED)

if(WIN32)
    add_definitions(-D_CRT_SECURE_NO_WARNINGS)
endif()

add_definitions(-DARUCO_STATIC)

add_subdirectory(src)
add_subdirectory(utils)
