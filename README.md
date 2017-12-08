# libdumb fork for cross compiling with DJGPP

This is a modified version of DUMB for cross compiling for MS-DOS with DJGPP. See [kode54/dumb](https://github.com/kode54/dumb/) for the original code. This fork was prompted by some cross compilation problems I had that you can read about in [issue #73](https://github.com/kode54/dumb/issues/73).

## Compiling

This project uses CMake. To compile, first make a `build` dir, go there, and then use the following command:

    cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/usr/local \
      -DBUILD_SHARED_LIBS:BOOL=OFF -DBUILD_EXAMPLES:BOOL=OFF \
      -DCMAKE_C_COMPILER="$DJGPP_CC" -DCMAKE_RANLIB="$DJGPP_RANLIB" \
      -DCMAKE_C_FLAGS="-mtune=i586 -ffast-math" -DBUILD_ALLEGRO4:BOOL=ON \
      -DALLEGRO_INCLUDE_DIR="/allegro-4.2.2-xc/include/" \
      -DALLEGRO_LIBRARY="/allegro-4.2.2-xc/lib/djgpp/liballeg.a" \
      ..

Note: replace `/allegro-4.2.2-xc` with the path to your [DJGPP Allegro 4](https://github.com/msikma/allegro-4.2.2-xc) build. You will need to have `$DJGPP_CC` and `$DJGPP_RANLIB` set to your DJGPP binaries, e.g. `/usr/local/djgpp/bin/i586-pc-msdosdjgpp-gcc`. I suggest using [Andrew Wu's build](https://github.com/andrewwutw/build-djgpp).