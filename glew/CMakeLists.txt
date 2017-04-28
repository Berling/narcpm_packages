cmake_minimum_required(VERSION 3.7 FATAL_ERROR)
project(glew VERSION 0.0.0 LANGUAGES CXX)

message("-- downloading snapshot for package glew")
file(DOWNLOAD
	https://github.com/nigels-com/glew/releases/download/glew-2.0.0/glew-2.0.0.zip
	${PACKAGE_ROOT}/glew.zip
	SHOW_PROGRESS)
