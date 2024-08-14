cmake_minimum_required(VERSION 3.5)

project(inih)

set(SRCS
    ${CMAKE_CURRENT_SOURCE_DIR}/ini.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/INIReader.cpp
)

set(HDRS
    ${CMAKE_CURRENT_SOURCE_DIR}/ini.h
    ${CMAKE_CURRENT_SOURCE_DIR}/INIReader.h
)

add_library(${PROJECT_NAME} STATIC ${SRCS} ${HDRS})
target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})