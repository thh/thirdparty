cmake_minimum_required(VERSION 2.8)
project(bzip2)

set(CMAKE_PREFIX_PATH H:/works/repository/thirdparty/release_x86)

message('*************************************')
message("${OUTPUT_CPU_ARCH}")
message('*************************************')

message("CMAKE_PREFIX_PATH: ${CMAKE_PREFIX_PATH}")
message("CMAKE_BINARY_DIR: ${CMAKE_BINARY_DIR}")
message("ZLIB_DIR: ${ZLIB_DIR}")
message("CMAKE_PREFIX_PATH: ${CMAKE_PREFIX_PATH}")
message("CMAKE_FRAMEWORK_PATH: ${CMAKE_FRAMEWORK_PATH}")
message("CMAKE_APPBUNDLE_PATH: ${CMAKE_APPBUNDLE_PATH}")

message("CMAKE_SYSTEM_PREFIX_PATH: ${CMAKE_SYSTEM_PREFIX_PATH}")
message("CMAKE_SYSTEM_FRAMEWORK_PATH: ${CMAKE_SYSTEM_FRAMEWORK_PATH}")
message("CMAKE_SYSTEM_APPBUNDLE_PATH: ${CMAKE_SYSTEM_APPBUNDLE_PATH}")

find_package(ZLIB)
