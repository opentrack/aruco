# ----------------------------------------------------------------------------
#   Basic Configuration
# ----------------------------------------------------------------------------
CMAKE_MINIMUM_REQUIRED(VERSION 2.6)

PROJECT(aruco)
set(PROJECT_VERSION "1.2.4")
string(REGEX MATCHALL "[0-9]" PROJECT_VERSION_PARTS "${PROJECT_VERSION}")
list(GET PROJECT_VERSION_PARTS 0 PROJECT_VERSION_MAJOR)
list(GET PROJECT_VERSION_PARTS 1 PROJECT_VERSION_MINOR)
list(GET PROJECT_VERSION_PARTS 2 PROJECT_VERSION_PATCH)
set(PROJECT_SOVERSION "${PROJECT_VERSION_MAJOR}.${PROJECT_VERSION_MINOR}")

#------------------------------------------------------
# Lib Names and Dirs
#------------------------------------------------------
include_directories(${OpenCV_INCLUDE_DIRS})

# Postfix of DLLs:
SET(PROJECT_DLLVERSION "${PROJECT_VERSION_MAJOR}${PROJECT_VERSION_MINOR}${PROJECT_VERSION_PATCH}")
SET(CMAKE_INSTALL_PREFIX "${CMAKE_BINARY_DIR}")
SET(RUNTIME_OUTPUT_PATH ${PROJECT_BINARY_DIR}/bin CACHE PATH "Directory for dlls and binaries")
SET(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/bin CACHE PATH "Directory for binaries")
SET(LIBRARY_OUTPUT_PATH ${PROJECT_BINARY_DIR}/bin CACHE PATH "Directory for dlls")

set(BUILD_SHARED_LIBS NO)

# ----------------------------------------------------------------------------
#   Find Dependencies
# ----------------------------------------------------------------------------

FIND_PACKAGE(OpenCV 	REQUIRED )
set (REQUIRED_LIBRARIES ${OpenCV_LIBS})

set(GL_FOUND "NO")

ADD_SUBDIRECTORY(src)
ADD_SUBDIRECTORY(utils)
