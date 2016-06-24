project(aruco)

include_directories(.)
include_directories(${CMAKE_CURRENT_BINARY_DIR})
include_directories(${OpenCV_INCLUDE_DIRS})

file(GLOB srcs "*.c" "*.cpp" "*.h" "*.hpp")
add_library(${PROJECT_NAME} STATIC ${srcs} ${hdrs})
target_link_libraries(${PROJECT_NAME} ${REQUIRED_LIBRARIES})

set(perms PERMISSIONS OWNER_READ OWNER_WRITE OWNER_EXECUTE GROUP_READ GROUP_EXECUTE WORLD_READ WORLD_EXECUTE)
INSTALL(TARGETS ${PROJECT_NAME}
    RUNTIME DESTINATION bin COMPONENT main ${perms}
    LIBRARY DESTINATION lib ${perms}  COMPONENT main
    ARCHIVE DESTINATION lib COMPONENT main)
