cmake_minimum_required(VERSION 3.7)
project(skynet)

find_package(Threads)

add_definitions(-DNOUSE_JEMALLOC)

include_directories(./3rd/lua)
include_directories(./skynet-src)

aux_source_directory(skynet-src SKYNET_SOURCES)

add_executable(skynet ${SKYNET_SOURCES})

target_link_libraries(skynet ${PROJECT_SOURCE_DIR}/3rd/lua/liblua.a)
target_link_libraries(skynet dl m ${CMAKE_THREAD_LIBS_INIT})
