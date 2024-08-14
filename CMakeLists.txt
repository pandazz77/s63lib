cmake_minimum_required(VERSION 3.5)

project(s63lib)

add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/3rdparty/blowfish)
add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/3rdparty/inih)
add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/3rdparty/zlib)

set(SRCS
    ${CMAKE_CURRENT_SOURCE_DIR}/src/s63.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/src/s63client.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/src/simple_zip.cpp
)

set(HDRS
    ${CMAKE_CURRENT_SOURCE_DIR}/include/s63.h
    ${CMAKE_CURRENT_SOURCE_DIR}/include/s63client.h
    ${CMAKE_CURRENT_SOURCE_DIR}/include/s63utils.hpp
    ${CMAKE_CURRENT_SOURCE_DIR}/include/simple_zip.h
)

option(BUILD_TEST "Build s63lib test" OFF)
if(BUILD_TEST)
    add_executable(s63test ${CMAKE_CURRENT_SOURCE_DIR}/tests/test.cpp ${SRCS} ${HDRS})
    target_link_libraries(s63test blowfish inih zlib)
    target_include_directories(s63test PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include)
endif()

option(BUILD_EXTRACTOR "Build s63 extractor util" OFF)
if(BUILD_EXTRACTOR)
    set(CMAKE_CXX_STANDARD 17)
    add_executable(s63extractor ${CMAKE_CURRENT_SOURCE_DIR}/tests/extractor.cpp ${SRCS} ${HDRS})
    target_link_libraries(s63extractor blowfish inih zlib)
    target_include_directories(s63extractor PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include)
endif()

add_library(${PROJECT_NAME} STATIC ${SRCS} ${HDRS})
target_link_libraries(${PROJECT_NAME} blowfish zlib)
target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include)
