###############################################################
#
# run command:
#   cmake .. -G "NMake Makefiles" -DCMAKE_INSTALL_PREFIX=H:\works\repository\thirdparty\
#
###############################################################
cmake_minimum_required(VERSION 2.8)
project(thirdparty CXX C)

string(TOLOWER ${CMAKE_BUILD_TYPE} OUTPUT_BUILD_TYPE)

set(OUTPUT_CPU_ARCH x86)
if(CMAKE_SIZEOF_VOID_P EQUAL 8)
  set(OUTPUT_CPU_ARCH amd64)
endif()

set(CMAKE_INSTALL_PREFIX  ${PROJECT_SOURCE_DIR}/${OUTPUT_BUILD_TYPE}_${OUTPUT_CPU_ARCH})

#set(URL "https://github.com/downloads/libevent/libevent/libevent-2.0.21-stable.tar.gz")

#file(DOWNLOAD "${URL}" "${PROJECT_SOURCE_DIR}/dists/libevent-2.0.21-stable.tar.gz" SHOW_PROGRESS)

add_subdirectory(sources/libevent)
add_subdirectory(sources/AvroC)
#add_subdirectory(sources/zlib/1.2.8)