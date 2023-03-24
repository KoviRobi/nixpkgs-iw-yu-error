cmake_minimum_required(VERSION 3.3 FATAL_ERROR)

project(iw_yu_test)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

find_program(iw_yu_path NAMES include-what-you-use iwyu REQUIRED)

add_executable(hello_c main.c)
add_executable(hello_cpp main.cpp)

set(iw_yu_options -Xiwyu --help)

set_property(TARGET hello_c PROPERTY C_INCLUDE_WHAT_YOU_USE ${iw_yu_path} ${iw_yu_options})
set_property(TARGET hello_cpp PROPERTY CXX_INCLUDE_WHAT_YOU_USE ${iw_yu_path} ${iw_yu_options})
