project(aruco)

file(GLOB srcs "*.c" "*.cpp" "*.h" "*.hpp")
add_library(aruco STATIC ${srcs})

target_include_directories(aruco SYSTEM PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
target_include_directories(aruco SYSTEM PUBLIC ${OpenCV_INCLUDE_DIRS})
target_include_directories(aruco SYSTEM PUBLIC ${OpenCV_INCLUDE_DIRS})

target_link_libraries(${PROJECT_NAME} ${OpenCV_LIBS})

set(perms PERMISSIONS OWNER_READ OWNER_WRITE OWNER_EXECUTE GROUP_READ GROUP_EXECUTE WORLD_READ WORLD_EXECUTE)
INSTALL(TARGETS ${PROJECT_NAME}
    RUNTIME DESTINATION bin COMPONENT main ${perms}
    LIBRARY DESTINATION lib ${perms}  COMPONENT main
    ARCHIVE DESTINATION lib COMPONENT main)
