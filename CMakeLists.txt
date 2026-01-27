cmake_minimum_required(VERSION 3.16)
project(qwt LANGUAGES CXX)

# Collect all Qwt sources
file(GLOB_RECURSE QWT_SOURCES
  src/*.cpp
  src/*.cxx
  src/*.cc
)

file(GLOB_RECURSE QWT_HEADERS
  src/*.h
  src/*.hpp
)

# Build the library
add_library(qwt STATIC ${QWT_SOURCES})

# Ensure PIC for static builds
set_target_properties(qwt PROPERTIES POSITION_INDEPENDENT_CODE ON)

# Public include path
target_include_directories(qwt PUBLIC
  ${CMAKE_CURRENT_SOURCE_DIR}/src
)

# Install headers
install(FILES ${QWT_HEADERS}
  DESTINATION include/qwt
)

# Install library
install(TARGETS qwt
  ARCHIVE DESTINATION lib
  LIBRARY DESTINATION lib
  RUNTIME DESTINATION bin
)
