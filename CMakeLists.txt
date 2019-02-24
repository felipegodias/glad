cmake_minimum_required(VERSION 3.6)

project(glad)

option(GLAD_DEBUG_MODE "Build as debug." ON)

if(GLAD_DEBUG_MODE)
    message(STATUS "GLAD debug mode on.")
    set(GLAD_MODE debug)
else()
    message(STATUS "GLAD release mode on.")
    set(GLAD_MODE release)
endif()

add_library(glad STATIC ${GLAD_MODE}/src/gl.c)

set(GLAD_INCLUDE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/${GLAD_MODE}/include)

target_include_directories(glad PUBLIC
    $<BUILD_INTERFACE:${GLAD_INCLUDE_DIR}>
)