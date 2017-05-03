cmake_minimum_required(VERSION 3.7 FATAL_ERROR)
project(boost VERSION 0.0.0 LANGUAGES C)

add_custom_target(boost)
add_custom_command(TARGET boost
	COMMAND ${PACKAGE_ROOT}/repository/boostrap.sh)
add_custom_command(TARGET boost
	COMMAND ${PACKAGE_ROOT}/repository/b2 --prefix=${PACKAGE_ROOT}/build install toolset=${TOOLSET} link=static threading=multi -j 8)
add_custom_command(TARGET boost
	COMMAND ${PACKAGE_ROOT}/repository/b2 --prefix=${PACKAGE_ROOT}/build install toolset=${TOOLSET} link=shared threading=multi -j 8)