cmake_minimum_required(VERSION 2.8)

project (EchoProject)

# The version number.
#set (Tutorial_VERSION_MAJOR 1)
#set (Tutorial_VERSION_MINOR 0)

# configure a header file to pass some of the CMake settings
# to the source code
#configure_file (
#  "${PROJECT_SOURCE_DIR}/TutorialConfig.h.in"
#  "${PROJECT_BINARY_DIR}/TutorialConfig.h"
#  )
#
# add the binary tree to the search path for include files
# so that we will find TutorialConfig.h
#include_directories("${PROJECT_BINARY_DIR}")

# add the executable

# client
add_executable(EchoClient EchoClient.cpp)
target_link_libraries(EchoClient folly pthread glog gflags wangle)

# server
add_executable(EchoServer EchoServer.cpp)
target_link_libraries(EchoServer folly pthread glog gflags wangle ssl crypto)

add_definitions("-g")

