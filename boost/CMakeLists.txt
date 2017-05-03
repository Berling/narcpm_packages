cmake_minimum_required(VERSION 3.7 FATAL_ERROR)
project(boost VERSION 0.0.0 LANGUAGES C)

execute_process(COMMAND git submodule update --init)
execute_process(
	COMMAND ${PACKAGE_ROOT}/repository/boostrap.sh
	COMMAND ${PACKAGE_ROOT}/repository/b2 --prefix=${PACKAGE_ROOT}/build install toolset=${TOOLSET} link=static threading=multi -j 8
	COMMAND ${PACKAGE_ROOT}/repository/b2 --prefix=${PACKAGE_ROOT}/build install toolset=${TOOLSET} link=shared threading=multi -j 8)
execute_process(COMMAND ${CMAKE_COMMAND} -E copy_directory ${PACKAGE_ROOT}/repository/include/boost ${PACKAGE_ROOT}/include)
