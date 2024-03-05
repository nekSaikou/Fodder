cmake_minimum_required(VERSION 3.25)

project(
  Fodder
  VERSION 1.0
  LANGUAGES CXX
  )

set(CMAKE_CXX_STANDARD 17)

file(GLOB_RECURSE SRC_FILES 
  src/*.cpp 
  src/Core/*.cpp
  src/Search/*.cpp
  src/Search/NNUE/*.cpp
  )

add_compile_definitions(
  RELEASE_BUILD
  VERSION_NUMBER="1.0"
  )

add_compile_options(
  -O3
  -flto -funroll-loops -fno-exceptions
  -march=native
  -Wall -pedantic
  # -fsanitize=undefined -fsanitize=address
  )

add_link_options(
  -flto
  # -fsanitize=undefined -fsanitize=address
  )

add_executable(Fodder ${SRC_FILES})
