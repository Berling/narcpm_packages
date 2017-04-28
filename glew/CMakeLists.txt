cmake_minimum_required(VERSION 3.7 FATAL_ERROR)
project(glew VERSION 0.0.0 LANGUAGES CXX)

exec_program(cd ${PACKAGE_ROOT}/repository/auto && make -j 8)
add_subdirectory(${PACKAGE_ROOT}/repository/build/cmake ${PACKAGE_ROOT}/build)
# install(DIRECTORY ${PACKAGE_ROOT}/repository/glm DESTINATION ${PACKAGE_ROOT}/include)
