# Copyright (c) 2014-2016, Ruslan Baratov
# All rights reserved.

cmake_minimum_required(VERSION 3.0)

set (CMAKE_CXX_STANDARD 11)

### Hunter snapshot that will be used ###
include("cmake/HunterGate.cmake")
HunterGate(
    URL "https://github.com/ruslo/hunter/archive/v0.19.87.tar.gz"
    SHA1 "1b0041a06357d2c9f1f1a7e93ff3132c36411719"
)
project(curllab)

### Download dependencies ###
hunter_add_package(CURL)
find_package (Threads)
### Find dependencies ###
#find_package(GTest CONFIG REQUIRED) # GTest::main

### Targets ###
add_executable(simple simple.cpp)
target_link_libraries(simple curl)
target_link_libraries (simple ${CMAKE_THREAD_LIBS_INIT})

