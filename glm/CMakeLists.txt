cmake_minimum_required(VERSION 3.7 FATAL_ERROR)
project(glm VERSION 0.0.0 LANGUAGES CXX)

add_custom_target(glm)
install(DIRECTORY ${PACKAGE_ROOT}/repositotry/glm DESTINATION ${PACKAGE_ROOT}/include)
