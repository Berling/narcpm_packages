cmake_minimum_required(VERSION 3.7 FATAL_ERROR)
project(boost VERSION 0.0.0 LANGUAGES C)

execute_process(COMMAND ${CMAKE_COMMAND} -E chdir ${PACKAGE_ROOT}/repository git submodule update --init)

if (NOT EXISTS ${PACKAGE_ROOT}/repository/b2)
	execute_process(COMMAND ${CMAKE_COMMAND} -E chdir ${PACKAGE_ROOT}/repository ./bootstrap.sh)
endif()

if (${CMAKE_BUILD_TYPE} MATCHES "Debug")
	set(BUILD_TYPE debug)
else()
	set(BUILD_TYPE release)
endif()

add_custom_command(boost)
add_custom_command(TARGET boost
	COMMAND ${CMAKE_COMMAND} -E chdir ${PACKAGE_ROOT}/repository ./b2 --build-dir=${PACKAGE_ROOT}/build/${TOOLCHAIN}/${CMAKE_BUILD_TYPE}/static install variant=${BUILD_TYPE} toolset=${TOOLCHAIN} link=static threading=multi -j 8)
add_custom_command(TARGET boost
	COMMAND ${CMAKE_COMMAND} -E chdir ${PACKAGE_ROOT}/repository ./b2 --build-dir=${PACKAGE_ROOT}/build/${TOOLCHAIN}/${CMAKE_BUILD_TYPE}/shared install variant=${BUILD_TYPE} toolset=${TOOLCHAIN} link=shared threading=multi -j 8)
