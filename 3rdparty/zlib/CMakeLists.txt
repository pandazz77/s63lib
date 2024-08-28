cmake_minimum_required(VERSION 3.5)

project(zlib)

file(GLOB SOURCES
     "*.h"
     "*.c"
)

add_library(${PROJECT_NAME} SHARED ${SOURCES})
target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})