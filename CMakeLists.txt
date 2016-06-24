cmake_minimum_required(VERSION 2.6)
project(aruco)

#include_directories(${OpenCV_INCLUDE_DIRS})

find_package(OpenCV REQUIRED)
set(REQUIRED_LIBRARIES ${OpenCV_LIBS})

add_subdirectory(src)
add_subdirectory(utils)
