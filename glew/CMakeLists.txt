cmake_minimum_required(VERSION 3.7 FATAL_ERROR)
project(glew VERSION 0.0.0 LANGUAGES CXX)

add_custom_target(glew)
add_custom_command(TARGET glew COMMAND
	cmake ${PACKAGE_ROOT}/repository/cmake)
# install(DIRECTORY ${PACKAGE_ROOT}/repository/glm DESTINATION ${PACKAGE_ROOT}/include)
