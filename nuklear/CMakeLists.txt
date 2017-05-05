cmake_minimum_required(VERSION 3.7 FATAL_ERROR)
project(nuklear VERSION 0.0.0 LANGUAGES CXX)

add_custom_target(nuklear)
install(DIRECTORY ${PACKAGE_ROOT}/repository/nuklear DESTINATION ${PACKAGE_ROOT}/include)
