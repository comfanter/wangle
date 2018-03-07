cmake_minimum_required(VERSION 2.8)

project (RPCProject)

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
include_directories("${PROJECT_SOURCE_DIR}")
include_directories("/home/zgf/dev/lib/apache/thrift/test/cpp")

set(GEN_CPP_DIR "/home/zgf/dev/lib/apache/thrift/test/cpp/gen-cpp")

# add the executable

# client
add_executable(RPCClient RpcClient.cpp ClientSerializeHandler.h ${GEN_CPP_DIR}/ThriftTest_types.h ${GEN_CPP_DIR}/ThriftTest_types.cpp)
#add_executable(RpcClient main.cpp)
target_link_libraries(RPCClient folly pthread glog gflags wangle thrift)

# server
add_executable(RPCServer RpcServer.cpp ServerSerializeHandler.h ${GEN_CPP_DIR}/ThriftTest_types.h ${GEN_CPP_DIR}/ThriftTest_types.cpp)
target_link_libraries(RPCServer folly pthread glog gflags wangle ssl crypto thrift)

#add_definitions("-g")

