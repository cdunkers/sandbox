cmake_minimum_required (VERSION 3.8)
project (sandbox)

# The version number.
set (sandbox_VERSION_MAJOR 0)
set (sandbox_VERSION_MINOR 0)
set (sandbox_VERSION_PATCH 1)
 
set(CMAKE_CXX_CLANG_TIDY
  clang-tidy;
  -header-filter=.;
  -checks=-*,cppcoreguidelines-*;
  -warnings-as-errors=*;)

 # configure a header file to pass some of the CMake settings
 # to the source code
configure_file (
    "${PROJECT_SOURCE_DIR}/Config.h.in"
    "${PROJECT_BINARY_DIR}/Config.h"
    )

# add the binary tree to the search path for include files
# so that we will find TutorialConfig.h
include_directories("${PROJECT_BINARY_DIR}")

# add the executable
add_executable(sandbox_main src/main.cpp)


