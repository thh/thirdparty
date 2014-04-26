cmake_minimum_required(VERSION 2.8)
project(gtest CXX)

set(gtest_force_shared_crt ON)
set(GTEST_SOURCE_DIRECTORY 1.7.0)
#message (${PROJECT_BINARY_DIR})

add_subdirectory(${GTEST_SOURCE_DIRECTORY} gtest)

install(DIRECTORY ${GTEST_SOURCE_DIRECTORY}/include/ DESTINATION include FILES_MATCHING PATTERN "*.h")
install(DIRECTORY ${GTEST_SOURCE_DIRECTORY}/src/     DESTINATION src     FILES_MATCHING PATTERN "*")

if(DEFINED WIN32)      
    install(FILES ${PROJECT_BINARY_DIR}/gtest/gtest.lib DESTINATION lib)
    install(FILES ${PROJECT_BINARY_DIR}/gtest/gtest_main.lib DESTINATION lib)
elseif(DEFINED UNIX)
    install(FILES ${PROJECT_BINARY_DIR}/gtest/libgtest.a DESTINATION lib)
    install(FILES ${PROJECT_BINARY_DIR}/gtest/libgtest_main.a DESTINATION lib)
endif()

#install(TARGETS gtest DESTINATION ${CMAKE_INSTALL_PREFIX}/release/ CONFIGURATIONS Release)
#install(TARGETS gtest_main DESTINATION ${CMAKE_INSTALL_PREFIX}/release/ CONFIGURATIONS Release)
