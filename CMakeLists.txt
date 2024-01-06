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
    cutils.c
    libbf.c
    libregexp.c
    libunicode.c
    quickjs.c
    quickjs-libc.c
    )

# Create target.
add_library(${PROJECT_NAME} STATIC ${SOURCE_FILES})
target_include_directories(${PROJECT_NAME} PUBLIC .)
target_compile_definitions(${PROJECT_NAME} PRIVATE
    CONFIG_VERSION="${QUICKJS_VERSION}"
    CONFIG_BIGNUM
    _GNU_SOURCE
    )
