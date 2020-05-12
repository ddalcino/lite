file(GLOB LOCAL_SRC *.c)

add_subdirectory(lib/lua52)
add_subdirectory(lib/stb)
add_subdirectory(api)

add_executable(lite ${LOCAL_SRC})
target_include_directories(lite PUBLIC ${SDL2_INCLUDE})
target_link_libraries(lite
        PUBLIC lua52 api stb ${SDL2_LINK_LIB} m
        PRIVATE project_options)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/
        CACHE PATH "Output directory for executables and DLL's.")

