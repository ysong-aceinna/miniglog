cmake_minimum_required(VERSION 2.8)
project(test)

set(CMAKE_BUILD_TYPE "Release")
set(CMAKE_CXX_FLAGS "-std=c++11")
set(CMAKE_CXX_FLAGS_RELEASE "-O3 -Wall -g")

set(ROOT_PATH ${PROJECT_SOURCE_DIR}/../..)
set(MINIGLOG_LIBS ${ROOT_PATH}/build/lib/libminiglog.so) #libminiglog.dylib for Mac;libminiglog.so for Linux.
set(MINIGLOG_INCLUDE_DIRS ${ROOT_PATH}/build/include)

file(GLOB test_dep
    "*.h"
    "*.cpp"
)

find_package (Threads)
include_directories( ${MINIGLOG_INCLUDE_DIRS})
add_executable( test ${test_dep} )
target_link_libraries( test ${MINIGLOG_LIBS} ${CMAKE_THREAD_LIBS_INIT})
