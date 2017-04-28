cmake_minimum_required(VERSION 3.7 FATAL_ERROR)
project(glew VERSION 0.0.0 LANGUAGES CXX)

if (NOT EXISTS ${PACKAGE_ROOT}/glew.zip)
	message("-- downloading snapshot for package glew")
	file(DOWNLOAD
		https://github.com/nigels-com/glew/releases/download/glew-2.0.0/glew-2.0.0.zip
		${PACKAGE_ROOT}/glew.zip
		SHOW_PROGRESS)
endif()

add_custom_target(extract)
add_custom_command(TARGET glew
	COMMAND ${CMAKE_COMMAND} -E tar xf ${PACKAGE_ROOT}/glew.zip)
add_custom_command(TARGET glew
	COMMAND ${CMAKE_COMMAND} -E rename ${PACKAGE_ROOT}/glew-2.0.0 ${PACKAGE_ROOT}/repository)

# file(GLOB_RECURSE src
# 	${PACKAGE_ROOT}/repository/src/*.cpp)

# add_library(glew
# 	${src})
