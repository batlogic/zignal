cmake_minimum_required (VERSION 3.0)
project ( zignal )

find_package(Boost)
#find_package(Benchmark)


add_library                ( flowz INTERFACE )
target_include_directories ( flowz INTERFACE . )

add_executable        ( benchmarks test/benchmark.cpp )
target_link_libraries ( benchmarks LINK_PUBLIC flowz benchmark )

add_executable        ( tests test/tests.cpp )
target_link_libraries ( tests LINK_PUBLIC flowz )

if( CMAKE_CXX_COMPILER_ID MATCHES "Clang|AppleClang" )
   set ( CMAKE_CXX_FLAGS "-g -O3 --std=c++1y --stdlib=libc++ -fcolor-diagnostics")
endif()


