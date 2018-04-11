cmake_minimum_required(VERSION 2.6)
project(aruco)
find_package(OpenCV REQUIRED)

if(NOT (CMAKE_SYSTEM_NAME STREQUAL "Windows") AND CMAKE_COMPILER_IS_GNUCXX)
    add_definitions(-fPIC)
endif()

add_subdirectory(src)
add_subdirectory(utils)
