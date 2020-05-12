file(GLOB LOCAL_SRC *.c)

add_library(lua52 ${LOCAL_SRC})
target_link_libraries(lua52 PRIVATE project_options)

