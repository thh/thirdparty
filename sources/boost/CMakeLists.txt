cmake_minimum_required(VERSION 2.8)
project(boost CXX)

set(ZLIB_SOURCE  ${PROJECT_SOURCE_DIR}/../zlib/origin)
set(BZIP2_SOURCE ${PROJECT_SOURCE_DIR}/../bzip2/1.0.6)
set(BOOST_SOURCE_DIRECTORY ${PROJECT_SOURCE_DIR}/1.55.0)

set(BOOST_BUILD_DIRECTORY ${PROJECT_BINARY_DIR})
set(BOOST_BUILD_TYPE "debug")
if (${CMAKE_BUILD_TYPE} EQUAL "Relase")
    set(BOOST_BUILD_TYPE "release")
endif()

#message("${ZLIB_SOURCE} ${BZIP2_SOURCE}")
#set(ENV{ZLIB_SOURCE} ${ZLIB_SOURCE})

#add_custom_target(boost_bjam ./bootstrap.bat WORKING_DIRECTORY ${BOOST_SOURCE_DIRECTORY})

add_custom_target(boost 
    COMMAND set ZLIB_SOURCE=${ZLIB_SOURCE}
    COMMAND set BZIP2_SOURCE=${BZIP2_SOURCE}
    COMMAND if not exist b2.exe ./bootstrap.bat
    COMMAND ./b2 -j5 install link=static runtime-link=shared threading=multi variant=${BOOST_BUILD_TYPE}
                 --prefix=${CMAKE_INSTALL_PREFIX}
                 #--build-dir= ${BOOST_BUILD_DIRECTORY}
                 #--build-type=complete 
                 --layout=tagged
                 --with-program_options
                 --with-filesystem
                 --with-system
                #--without-mpi 
                #--without-python
    WORKING_DIRECTORY  ${BOOST_SOURCE_DIRECTORY})

# if (WIN32)
#     if (CMAKE_SIZEOF_VOID_P EQUAL 8)
#         message("buiding x86_64 openssl")
#         add_custom_target(openssl_config perl Configure VC-WIN64A no-asm --prefix=${CMAKE_INSTALL_PREFIX} -DUNICODE -D_UNICODE WORKING_DIRECTORY ${OPENSSL_SOURCE_DIRECTORY})
#         add_custom_target(openssl_do_ms  ms/do_win64a WORKING_DIRECTORY ${OPENSSL_SOURCE_DIRECTORY})
#         add_custom_target(openssl_build  nmake -f ms/ntdll.mak WORKING_DIRECTORY ${OPENSSL_SOURCE_DIRECTORY})
#         add_custom_target(openssl_test nmake -f ms/ntdll.mak test WORKING_DIRECTORY ${OPENSSL_SOURCE_DIRECTORY})
#         add_custom_target(openssl_install nmake -f ms/ntdll.mak install WORKING_DIRECTORY ${OPENSSL_SOURCE_DIRECTORY})
#     else()
#         message("buiding x86 openssl")
#         add_custom_target(openssl_config perl Configure VC-WIN32 no-asm --prefix=${CMAKE_INSTALL_PREFIX} -DUNICODE -D_UNICODE WORKING_DIRECTORY ${OPENSSL_SOURCE_DIRECTORY})
#         add_custom_target(openssl_do_ms  ms/do_ms WORKING_DIRECTORY ${OPENSSL_SOURCE_DIRECTORY})
#         add_custom_target(openssl_build  nmake -f ms/ntdll.mak WORKING_DIRECTORY ${OPENSSL_SOURCE_DIRECTORY})
#         add_custom_target(openssl_test nmake -f ms/ntdll.mak test WORKING_DIRECTORY ${OPENSSL_SOURCE_DIRECTORY})
#         add_custom_target(openssl_install nmake -f ms/ntdll.mak install WORKING_DIRECTORY ${OPENSSL_SOURCE_DIRECTORY})
#     endif()

#     add_dependencies(openssl_install openssl_test)
#     add_dependencies(openssl_test openssl_build)
#     add_dependencies(openssl_build openssl_do_ms)
#     add_dependencies(openssl_do_ms openssl_config)
# endif()