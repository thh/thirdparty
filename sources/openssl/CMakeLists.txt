cmake_minimum_required(VERSION 2.8)
project(openssl)

set(OPENSSL_SOURCE_DIRECTORY ${PROJECT_SOURCE_DIR}/1.0.1g)

find_program(PERL perl)

#message("PERL: ${PERL}")

if (PERL_NOT_FOUND)
    message(FATAL_ERROR 'perl not found')
endif(PERL_NOT_FOUND)

#message( STATUS "CMAKE_GENERATOR: ${CMAKE_GENERATOR}")

#message( STATUS "CMAKE_CL_64: ${CMAKE_CL_64}")
#message( STATUS "CMAKE_HOST_SYSTEM: ${CMAKE_HOST_SYSTEM_PROCESSOR}")

if (WIN32)
    if (CMAKE_SIZEOF_VOID_P EQUAL 8)
        message("Build x86_64")
        add_custom_target(openssl_config perl Configure VC-WIN64A no-asm --prefix=${CMAKE_INSTALL_PREFIX} -DUNICODE -D_UNICODE WORKING_DIRECTORY ${OPENSSL_SOURCE_DIRECTORY})
        add_custom_target(openssl_do_ms  ms/do_win64a WORKING_DIRECTORY ${OPENSSL_SOURCE_DIRECTORY})
        add_custom_target(openssl_build  nmake -f ms/ntdll.mak WORKING_DIRECTORY ${OPENSSL_SOURCE_DIRECTORY})
        add_custom_target(openssl_test nmake -f ms/ntdll.mak test WORKING_DIRECTORY ${OPENSSL_SOURCE_DIRECTORY})
        add_custom_target(openssl_install nmake -f ms/ntdll.mak install WORKING_DIRECTORY ${OPENSSL_SOURCE_DIRECTORY})
    else()
        message("Build x86")
        add_custom_target(openssl_config perl Configure VC-WIN32 no-asm --prefix=${CMAKE_INSTALL_PREFIX} -DUNICODE -D_UNICODE WORKING_DIRECTORY ${OPENSSL_SOURCE_DIRECTORY})
        add_custom_target(openssl_do_ms  ms/do_ms WORKING_DIRECTORY ${OPENSSL_SOURCE_DIRECTORY})
        add_custom_target(openssl_build  nmake -f ms/ntdll.mak WORKING_DIRECTORY ${OPENSSL_SOURCE_DIRECTORY})
        add_custom_target(openssl_test nmake -f ms/ntdll.mak test WORKING_DIRECTORY ${OPENSSL_SOURCE_DIRECTORY})
        add_custom_target(openssl_install nmake -f ms/ntdll.mak install WORKING_DIRECTORY ${OPENSSL_SOURCE_DIRECTORY})
    endif()

    add_dependencies(openssl_install openssl_test)
    add_dependencies(openssl_test openssl_build)
    add_dependencies(openssl_build openssl_do_ms)
    add_dependencies(openssl_do_ms openssl_config)
endif()