cmake_minimum_required(VERSION 3.5)

project(blowfish)

set(SRCS
     ${CMAKE_CURRENT_SOURCE_DIR}/blowfish.cpp
)

set(HDRS
    ${CMAKE_CURRENT_SOURCE_DIR}/blowfish.h
)

add_library(${PROJECT_NAME} SHARED ${SRCS} ${HDRS})
target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})