cmake_minimum_required(VERSION 3.0)
project(SDM)
set_property(GLOBAL PROPERTY USE_FOLDERS ON)

#General
add_compile_options(-Wall -g -fPIC)
include(CheckCXXCompilerFlag)
check_cxx_compiler_flag("-std=c++11" COMPILER_SUPPORTS_CXX11)
if(COMPILER_SUPPORTS_CXX11)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
else()
	message(STATUS "The compiler ${CMAKE_CXX_COMPILER} has no C++11 support.")
endif()

#Packages
find_package(OpenCV REQUIRED)

#Generate lib
add_subdirectory(src)

#Generate examples
add_subdirectory(examples)