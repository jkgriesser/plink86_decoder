cmake_minimum_required(VERSION 3.6)
project(rtlink_decode)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

include_directories(../../scummvm)

set(SOURCE_FILES
    .gitignore
    Makefile
    module.mk
    rtlink_decode.cpp
    rtlink_decode.h
    variation1.cpp
    variation2.cpp
    variation3.cpp)

add_executable(rtlink_decode ${SOURCE_FILES})