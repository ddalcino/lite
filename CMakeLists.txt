cmake_minimum_required(VERSION 3.5)
project(lite LANGUAGES C)

if (WIN32)
    add_subdirectory(winlib)
else ()
    add_definitions(-DLUA_USE_POPEN)
    set(SDL2_LINK_LIB SDL2)
endif ()

set(CMAKE_C_FLAGS_RELEASE "${CMAKE_C_FLAGS_RELEASE} -O3")
set(CMAKE_C_FLAGS_DEBUG "${CMAKE_C_FLAGS_DEBUG} -O0 -g")

add_library(project_options INTERFACE)
target_compile_features(project_options INTERFACE c_std_11)
target_compile_options(project_options INTERFACE -Wall)

add_subdirectory(src)

