cmake_minimum_required(VERSION 3.3)

project(fst
  LANGUAGES CXX
)

set(FST_SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR})
set(FST_BINARY_DIR ${CMAKE_CURRENT_BINARY_DIR})

# Include guards
if (FST_SOURCE_DIR STREQUAL FST_BINARY_DIR)
  message(FATAL_ERROR "In-source builds not allowed. Please make a new directory (called a build directory) and run CMake from there.")
endif ()

set(CMAKE_CXX_STANDARD 20)

set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_CXX_VISIBILITY_PRESET hidden)

set(CMAKE_VISIBILITY_INLINES_HIDDEN ON)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

add_library(fst OBJECT
  src/lib/compat.cc
  src/lib/encode.cc
  src/lib/flags.cc
  src/lib/fst-types.cc
  src/lib/fst.cc
  src/lib/mapped-file.cc
  src/lib/properties.cc
  src/lib/symbol-table-ops.cc
  src/lib/symbol-table.cc
  src/lib/util.cc
  src/lib/weight.cc
)

target_include_directories(fst SYSTEM
  PUBLIC src/include
)
