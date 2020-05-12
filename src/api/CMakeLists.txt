file(GLOB API_SRC *.c *.h)
add_library(api ${API_SRC})
target_include_directories(api PUBLIC .. ${SDL2_INCLUDE})
target_link_libraries(api
        PUBLIC lua52 stb ${SDL2_LINK_LIB}
        PRIVATE project_options)
