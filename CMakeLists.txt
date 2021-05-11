###########################################################
## CMAKE SETUP
###########################################################

cmake_minimum_required(VERSION 3.2)
project(hashtable)

###########################################################
## LIBRARY
###########################################################

add_library(hashtable SHARED hashtable.c)
add_library(hashtable-static STATIC hashtable.c)

###########################################################
## EXECUTABLES
###########################################################

include_directories(${CMAKE_CURRENT_SOURCE_DIR})

add_executable(hashtable-test ${CMAKE_CURRENT_SOURCE_DIR}/test/test.c)
add_executable(hashtable-example ${CMAKE_CURRENT_SOURCE_DIR}/test/example.c)

target_link_libraries(hashtable-test hashtable)
target_link_libraries(hashtable-example hashtable)

###########################################################
## COMPILER FLAGS
###########################################################

set_target_properties(hashtable PROPERTIES C_STANDARD 99)
set_target_properties(hashtable-static PROPERTIES C_STANDARD 99)
set_target_properties(hashtable-test PROPERTIES C_STANDARD 99)
set_target_properties(hashtable-example PROPERTIES C_STANDARD 99)

target_compile_options(hashtable PUBLIC -O3)
target_compile_options(hashtable-static PUBLIC -O3)
target_compile_options(hashtable-test PUBLIC -g)
target_compile_options(hashtable-example PUBLIC -g)
