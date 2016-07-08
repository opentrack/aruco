cmake_minimum_required(VERSION 2.6)
project(aruco)

#include_directories(${OpenCV_INCLUDE_DIRS})

find_package(OpenCV REQUIRED COMPONENTS opencv_core opencv_calib3d opencv_imgproc opencv_videoio)
set(REQUIRED_LIBRARIES ${OpenCV_LIBS})

if(NOT (CMAKE_SYSTEM_NAME STREQUAL "Windows") AND CMAKE_COMPILER_IS_GNUCXX)
    add_definitions(-fPIC)
endif()

add_subdirectory(src)
add_subdirectory(utils)
