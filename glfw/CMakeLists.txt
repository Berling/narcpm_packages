cmake_minimum_required(VERSION 3.7 FATAL_ERROR)
project(glfw VERSION 0.0.0 LANGUAGES C)

execute_process(COMMAND ${CMAKE_COMMAND} -DCMAKE_BUILD_TYPE=${CMAKE_BUILD_TYPE} -DCMAKE_C_COMPILER=${CMAKE_C_COMPILER} ${PACKAGE_ROOT}/repository)
execute_process(COMMAND make -j 8)
