cmake_minimum_required(VERSION 2.8)
project(libevent CXX)

set(LIBEVENT ${PROJECT_SOURCE_DIR}/2.0.21)
#set(CMAKE_INSTALL_PREFIX ${PROJECT_SOURCE_DIR})
message("-- Install Prefix: ${CMAKE_INSTALL_PREFIX}")

#execute_process(COMMAND dir ERROR_QUIET)
#add_custom_command(TARGET install PRE_BUILD cmd /k echo  WORKING_DIRECTORY ${LIBEVENT})
#add_custom_command(TARGET install PRE_BUILD nmake /f Makefile.nmake WORKING_DIRECTORY ${LIBEVENT})

add_custom_target(libevent ALL nmake /f Makefile.nmake WORKING_DIRECTORY ${LIBEVENT})

install(DIRECTORY ${LIBEVENT}/include/ DESTINATION ${CMAKE_INSTALL_PREFIX}/include  FILES_MATCHING PATTERN "*.h")
install(DIRECTORY ${LIBEVENT}/WIN32-Code/ DESTINATION ${CMAKE_INSTALL_PREFIX}/include FILES_MATCHING PATTERN "*.h")

install(FILES ${LIBEVENT}/libevent.lib DESTINATION ${CMAKE_INSTALL_PREFIX}/lib)
install(FILES ${LIBEVENT}/libevent_core.lib DESTINATION ${CMAKE_INSTALL_PREFIX}/lib)
install(FILES ${LIBEVENT}/libevent_extras.lib DESTINATION ${CMAKE_INSTALL_PREFIX}/lib)

