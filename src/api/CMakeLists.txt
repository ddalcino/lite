file(GLOB API_SRC *.c *.h)
add_library(api ${API_SRC})
target_include_directories(api PUBLIC ..)
target_link_libraries(api
        PUBLIC lua52 stb
        PRIVATE project_options)
