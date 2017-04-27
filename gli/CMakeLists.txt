cmake_minimum_required(VERSION 3.7 FATAL_ERROR)
project(gli VERSION 0.0.0 LANGUAGES CXX)

add_custom_target(gli)
install(DIRECTORY ${PACKAGE_ROOT}/repository/gli DESTINATION ${PACKAGE_ROOT}/include)
