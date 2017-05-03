cmake_minimum_required(VERSION 3.7 FATAL_ERROR)
project(boost VERSION 0.0.0 LANGUAGES C)

execute_process(COMMAND ${CMAKE_COMMAND} -E chdir ${PACKAGE_ROOT}/repository git submodule update --init)

if (NOT EXISTS ${PACKAGE_ROOT}/repository/b2)
	execute_process(COMMAND ${CMAKE_COMMAND} -E chdir ${PACKAGE_ROOT}/repository ./bootstrap.sh)
endif()

execute_process(COMMAND ${CMAKE_COMMAND} -E chdir ${PACKAGE_ROOT}/repository ./b2 --build-dir=${PACKAGE_ROOT}/build/${TOOLCHAIN}/${CMAKE_BUILD_TYPE} install toolset=${TOOLSET} link=static threading=multi -j 8)
execute_process(COMMAND ${CMAKE_COMMAND} -E chdir ${PACKAGE_ROOT}/repository ./b2 --build-dir=${PACKAGE_ROOT}/build/${TOOLCHAIN}/${CMAKE_BUILD_TYPE} install toolset=${TOOLSET} link=shared threading=multi -j 8)
execute_process(COMMAND ${CMAKE_COMMAND} -E copy_directory ${PACKAGE_ROOT}/repository/include/boost ${PACKAGE_ROOT}/include)
