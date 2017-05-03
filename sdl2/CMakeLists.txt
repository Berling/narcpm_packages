cmake_minimum_required(VERSION 3.7 FATAL_ERROR)
project(boost VERSION 0.0.0 LANGUAGES C)

execute_process(COMMAND ${CMAKE_COMMAND} ${PACKAGE_ROOT}/repository)
execute_process(COMMAND make -j 8)
file(GLOB_RECURSE include ${PACKAGE_ROOT}/repository/include/*.h)
install(FILES ${include} DESTINATION ${PACKAGE_ROOT}/include/SDL2)
