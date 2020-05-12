cmake_minimum_required(VERSION 3.5)
project(lite LANGUAGES C)

if (WIN32)
    # 32-bit is: i686-w64-mingw32
    set(WIN_SDL_ROOT ${PROJECT_SOURCE_DIR}/winlib/SDL2-2.0.10/x86_64-w64-mingw32)
    set(SDL2_INCLUDE ${WIN_SDL_ROOT}/include)

    # Note: this link step is broken.
    # SDL2 needs to run its own WinMain, but the linker cannot find it.
    set(SDL2_LINK_LIB ${WIN_SDL_ROOT}/bin/SDL2.dll)
    set(EXTRA_COMPILE_OPTIONS -Dmain=SDL_main)
else ()
    add_definitions(-DLUA_USE_POPEN)
    set(SDL2_LINK_LIB SDL2)
endif ()

set(CMAKE_C_FLAGS_RELEASE "${CMAKE_C_FLAGS_RELEASE} -O3")
set(CMAKE_C_FLAGS_DEBUG "${CMAKE_C_FLAGS_DEBUG} -O0 -g")

add_library(project_options INTERFACE)
target_compile_features(project_options INTERFACE c_std_11)
target_compile_options(project_options INTERFACE -Wall ${EXTRA_COMPILE_OPTIONS})

add_subdirectory(src)

