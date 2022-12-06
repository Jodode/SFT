cmake_minimum_required(VERSION 3.0)
project(SFT VERSION 1.0 LANGUAGES CXX)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++14" )
set(CMAKE_CXX_STANDARD 14)
set(SOURCE_DIR ${CMAKE_SOURCE_DIR})
set(CMAKE_MODULE_PATH "${CMAKE_SOURCE_DIR}/cmake/modules;${CMAKE_MODULE_PATH}")
include("${CMAKE_SOURCE_DIR}/cmake/modules/detect.cmake")

detectOS()
detectCompiler()

IF (APPLE)
    FIND_LIBRARY(COREFOUNDATION_LIBRARY CoreFoundation )
    message("[+]CoreFoundation found in ${COREFOUNDATION_LIBRARY}")
    FIND_LIBRARY(SYSTEMCONFIGURATION_LIBRARY SystemConfiguration )
    message("[+]CoreFoundation found in ${SYSTEMCONFIGURATION_LIBRARY}")
ENDIF (APPLE)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include/header)
link_directories(${CMAKE_CURRENT_SOURCE_DIR}/include/lib)
# TODO: docopt https://stackoverflow.com/questions/33036333/docopt-linker-error-for-example-program
add_subdirectory(src)
