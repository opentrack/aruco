project(aruco)

add_definitions(-DARUCO_BUILD)

if(WIN32)
    add_definitions(-D_USE_MATH_DEFINES -DNOMINMAX)
endif()

file(GLOB srcs "*.c" "*.cpp" "*.h" "*.hpp")

add_library(aruco STATIC ${srcs})

target_include_directories(aruco SYSTEM PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}")
target_include_directories(aruco SYSTEM PUBLIC "${OpenCV_INCLUDE_DIRS}")

target_link_libraries(${PROJECT_NAME} opencv_core opencv_calib3d opencv_imgproc)

set(perms PERMISSIONS OWNER_READ OWNER_WRITE GROUP_READ WORLD_READ)
set(perms2 ${perms} OWNER_EXECUTE GROUP_EXECUTE WORLD_EXECUTE)

file(GLOB hdrs "${CMAKE_CURRENT_SOURCE_DIR}/*.h" LIST_DIRECTORIES FALSE)
file(COPY ${hdrs} DESTINATION "${CMAKE_CURRENT_BINARY_DIR}/include/aruco" USE_SOURCE_PERMISSIONS)

INSTALL(TARGETS ${PROJECT_NAME}
    RUNTIME DESTINATION bin ${perms2}
    LIBRARY DESTINATION lib ${perms2}
    ARCHIVE DESTINATION lib
)
