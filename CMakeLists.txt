cmake_minimum_required(VERSION 3.12)

# Project
project(Libchess VERSION 1.0 LANGUAGES CXX)

# Base directory relative includes
include_directories(.)
include_directories(./src/)

# Flags
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_FLAGS "-Wall -pedantic -pedantic-errors -Wextra -Wcast-align -Wcast-qual -Wchar-subscripts -Wcomment -Wdisabled-optimization -Wfloat-equal -Wformat -Wformat=2 -Wformat-nonliteral -Wformat-security -Wformat-y2k -Wimport -Winit-self -Winline -Winvalid-pch -Wmissing-braces -Wmissing-field-initializers -Wmissing-format-attribute -Wmissing-include-dirs -Wmissing-noreturn -Wodr -Wpacked -Wparentheses -Wpointer-arith -Wredundant-decls -Wreturn-type -Wsequence-point -Wshadow -Wsign-compare -Wstack-protector -Wstrict-aliasing -Wstrict-aliasing=2 -Wswitch -Wswitch-default -Wswitch-enum -Wtrigraphs -Wuninitialized -Wunknown-pragmas -Wunreachable-code -Wunused -Wunused-function -Wunused-label -Wunused-parameter -Wunused-value -Wunused-variable -Wvariadic-macros -Wvolatile-register-var -Wwrite-strings")
set(CMAKE_CXX_FLAGS_DEBUG "-g")
set(CMAKE_CXX_FLAGS_RELEASE "-O3 -march=native -DNDEBUG")

# Default build type
if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE Release)
endif()

# Add the static library
add_library(
    libchess-static
    STATIC
    src/attackers.cpp
    src/checkers.cpp
    src/check_evasions.cpp
    src/count_moves.cpp
    src/get_fen.cpp
    src/is_legal.cpp
    src/king_allowed.cpp
    src/legal_captures.cpp
    src/legal_moves.cpp
    src/legal_noncaptures.cpp
    src/makemove.cpp
    src/movegen.cpp
    src/perft.cpp
    src/pinned.cpp
    src/predict_hash.cpp
    src/set_fen.cpp
    src/square_attacked.cpp
    src/squares_attacked.cpp
    src/undomove.cpp
)

# Add the shared library
add_library(
    libchess-shared
    SHARED
    src/attackers.cpp
    src/checkers.cpp
    src/check_evasions.cpp
    src/count_moves.cpp
    src/get_fen.cpp
    src/is_legal.cpp
    src/king_allowed.cpp
    src/legal_captures.cpp
    src/legal_moves.cpp
    src/legal_noncaptures.cpp
    src/makemove.cpp
    src/movegen.cpp
    src/perft.cpp
    src/pinned.cpp
    src/predict_hash.cpp
    src/set_fen.cpp
    src/square_attacked.cpp
    src/squares_attacked.cpp
    src/undomove.cpp
)

set_target_properties(
    libchess-static
    PROPERTIES
    OUTPUT_NAME "chess"
    ARCHIVE_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/static"
    LIBRARY_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/static"
    RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/static"
)

set_target_properties(
    libchess-shared
    PROPERTIES
    OUTPUT_NAME "chess"
    ARCHIVE_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/shared"
    LIBRARY_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/shared"
    RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/shared"
)
