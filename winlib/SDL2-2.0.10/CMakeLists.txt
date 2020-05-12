option(USE_64_BIT_SDL "Link to 64-bit SDL2 binary (32-bit if off)" ON)

if(USE_64_BIT_SDL)
    set(SDL_PATH SDL2-2.0.10/x86_64-w64-mingw32)
else()
    set(SDL_PATH SDL2-2.0.10/i686-w64-mingw32)
endif()


