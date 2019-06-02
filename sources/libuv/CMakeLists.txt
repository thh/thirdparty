cmake_minimum_required(VERSION 2.8)
project(libuv CXX)

set(LIBUV ${PROJECT_SOURCE_DIR}/origin)
#set(CMAKE_INSTALL_PREFIX ${PROJECT_SOURCE_DIR})
message("-- Install Prefix: ${CMAKE_INSTALL_PREFIX}")

# set(DEVENV $ENV{VSINSTALLDIR}/../Enterprise/Common7/IDE/devenv.exe)

add_subdirectory(origin)

# ${LIBUV}/vcbuild.bat debug x64 nobuild static && ${DEVENV} uv.sln /Upgrade &&

# add_custom_target(libuv ALL COMMAND vcbuild.bat debug clean nobuild vs2017 x64 static && msbuild uv.sln WORKING_DIRECTORY ${LIBUV})
# add_custom_command(TARGET libuv PRE_BUILD ${LIBUV}/vcbuild.bat debug x64 nobuild static WORKING_DIRECTORY ${LIBUV})

install(DIRECTORY ${LIBUV}/include/ DESTINATION ${CMAKE_INSTALL_PREFIX}/include/ FILES_MATCHING PATTERN "*.h")
# install(DIRECTORY ${LIBEVENT}/WIN32-Code/ DESTINATION ${CMAKE_INSTALL_PREFIX}/include FILES_MATCHING PATTERN "*.h")
install(TARGETS uv DESTINATION ${CMAKE_INSTALL_PREFIX}/lib)
install(TARGETS uv_a DESTINATION ${CMAKE_INSTALL_PREFIX}/lib)

#install(FILES ${LIBUV}/Debug/lib/libuv.lib DESTINATION ${CMAKE_INSTALL_PREFIX}/lib)
# install(FILES ${LIBEVENT}/libevent_core.lib DESTINATION ${CMAKE_INSTALL_PREFIX}/lib)
# install(FILES ${LIBEVENT}/libevent_extras.lib DESTINATION ${CMAKE_INSTALL_PREFIX}/lib)
