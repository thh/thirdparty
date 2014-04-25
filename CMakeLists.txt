###############################################################
#
# run command:
#   cmake .. -G "NMake Makefiles" -DCMAKE_INSTALL_PREFIX=H:\works\repository\thirdparty\
#
###############################################################
cmake_minimum_required(VERSION 2.8)
project(thirdparty CXX)

#set(URL "https://github.com/downloads/libevent/libevent/libevent-2.0.21-stable.tar.gz")

#file(DOWNLOAD "${URL}" "${PROJECT_SOURCE_DIR}/dists/libevent-2.0.21-stable.tar.gz" SHOW_PROGRESS)

add_subdirectory(sources/libevent)
add_subdirectory(sources/AvroC)
