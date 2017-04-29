cmake_minimum_required(VERSION 3.7 FATAL_ERROR)
project(gsl VERSION 0.0.0 LANGUAGES CXX)

add_custom_target(gsl)
install(DIRECTORY ${PACKAGE_ROOT}/repository/include/glm DESTINATION ${PACKAGE_ROOT}/include)
