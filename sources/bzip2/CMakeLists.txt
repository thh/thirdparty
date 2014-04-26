cmake_minimum_required(VERSION 2.8)
project(bzip2)

set(BZIP2_SOURCE_DIRECTORY ${PROJECT_SOURCE_DIR}/1.0.6)



INSTALL(FILES ${BZIP2_SOURCE_DIRECTORY}/bzlib.h DESTINATION include)
INSTALL(FILES ${BZIP2_SOURCE_DIRECTORY}/libbz2.lib DESTINATION lib)

add_custom_target(build ALL nmake -f ${BZIP2_SOURCE_DIRECTORY}/makefile.msc WORKING_DIRECTORY ${BZIP2_SOURCE_DIRECTORY})
#add_dependencies(install build)