cmake_minimum_required(VERSION 3.4.1)
project(quickjs LANGUAGES C)

# Set quickjs version.
file(STRINGS VERSION QUICKJS_VERSION)

# C standard requirements.
set(CMAKE_C_STANDARD 11)
set(CMAKE_C_STANDARD_REQUIRED ON)
set(CMAKE_C_EXTENSIONS ON)

# Add source files.
set(SOURCE_FILES
    cutils.h
    cutils.c

    libbf.c
    libbf.h

    libregexp.h
    libregexp-opcode.h
    libregexp.c

    libunicode.h
    libunicode-table.h
    libunicode.c

    quickjs.h
    quickjs-atom.h
    quickjs-opcode.h
    quickjs.c

    quickjs-libc.h
    quickjs-libc.c
    )

# Create target.
add_library(${PROJECT_NAME} STATIC ${SOURCE_FILES})
target_compile_definitions(${PROJECT_NAME} PRIVATE
    CONFIG_VERSION="${QUICKJS_VERSION}"
    CONFIG_BIGNUM
    _GNU_SOURCE
    )
