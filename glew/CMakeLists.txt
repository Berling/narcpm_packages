cmake_minimum_required(VERSION 3.7 FATAL_ERROR)
project(glew VERSION 0.0.0 LANGUAGES C)

if (NOT EXISTS ${PACKAGE_ROOT}/glew.zip)
	message("-- downloading snapshot for package glew")
	file(DOWNLOAD
		https://github.com/nigels-com/glew/releases/download/glew-2.0.0/glew-2.0.0.zip
		${PACKAGE_ROOT}/glew.zip
		SHOW_PROGRESS)
endif()

if (${BUILD_SHARED_LIBS})
	message("FOOOOOOO!!!!!!!!!!!!!!!!")
endif()

if (NOT EXISTS ${PACKAGE_ROOT}/repository)
	execute_process(COMMAND ${CMAKE_COMMAND} -E tar xf glew.zip
		WORKING_DIRECTORY ${PACKAGE_ROOT})
	execute_process(COMMAND ${CMAKE_COMMAND} -E rename ${PACKAGE_ROOT}/glew-2.0.0 ${PACKAGE_ROOT}/repository)
endif()

add_library(glew
	${PACKAGE_ROOT}/repository/src/glew.c)

target_include_directories(glew PUBLIC
	$<BUILD_INTERFACE:${PACKAGE_ROOT}/repository/include>
	$<INSTALL_INTERFACE:include>)

install(TARGETS glew EXPORT glew
	ARCHIVE DESTINATION ${PACKAGE_ROOT}/lib/${TOOLCHAIN}/${CMAKE_BUILD_TYPE}
	LIBRARY DESTINATION ${PACKAGE_ROOT0/lib/${TOOLCHAIN}/${CMAKE_BUILD_TYPE}})
install(DIRECTORY ${PACKAGE_ROOT}/repository/include/GL DESTINATION ${PACKAGE_ROOT}/include)
