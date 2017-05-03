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

if (${TOOLCHAIN} MATCHES "clang")
	set(CXX_FLAGS "-stdlib=libc++")

add_custom_target(boost ALL)
add_custom_command(TARGET boost
	COMMAND ${CMAKE_COMMAND} -E chdir ${PACKAGE_ROOT}/repository ./b2 --build-dir=${PACKAGE_ROOT}/build --libdir=${PACKAGE_ROOT}/lib/${TOOLCHAIN}/${CMAKE_BUILD_TYPE} --includedir=${PACKAGE_ROOT}/include install variant=${BUILD_TYPE} --without-python toolset=${TOOLCHAIN} link=static,shared threading=multi cxxflags="-std=c++1z ${CXX_FLAGS}" -j 8)
install(DIRECTORY ${PACKAGE_ROOT}/include DESTINATION ${PACKAGE_ROOT})
