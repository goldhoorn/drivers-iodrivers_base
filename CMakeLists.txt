# CMakeLists.txt has to be located in the project folder and cmake has to be
# executed from 'project/build' with 'cmake ../'.
#cmake_minimum_required(VERSION 2.6)
#find_package(Rock)
#rock_init(iodrivers_base 0.1)
#rock_standard_layout()

project(iodrivers_base)

cmake_minimum_required(VERSION 2.6)

INCLUDE_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR}/inc)
add_definitions("-std=c++11")

add_subdirectory(src)

INSTALL( DIRECTORY inc/ DESTINATION include)


