project(utils)

add_executable(aruco_test aruco_test.cpp)
add_executable(aruco_create_marker aruco_create_marker.cpp)

foreach(i aruco_test aruco_create_marker)
    target_include_directories(${i} SYSTEM PRIVATE ${OpenCV_INCLUDE_DIRS})
    target_include_directories(${i} SYSTEM PRIVATE ${PROJECT_SOURCE_DIR}/src)
    target_link_libraries(${i} aruco ${OpenCV_LIBS})
endforeach()

#add_executable(aruco_simple aruco_simple.cpp)
#add_executable(aruco_create_board aruco_create_board.cpp)
#add_executable(aruco_selectoptimalmarkers aruco_selectoptimalmarkers.cpp)
#add_executable(aruco_simple_board aruco_simple_board.cpp)
#add_executable(aruco_test_board aruco_test_board.cpp)
#add_executable(aruco_board_pix2meters aruco_board_pix2meters.cpp)
#add_executable(aruco_test_board_stability aruco_test_board_stability.cpp)

install(TARGETS aruco_test aruco_create_marker RUNTIME DESTINATION bin)
