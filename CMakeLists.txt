cmake_minimum_required(VERSION 3.5)
project(RTNeural VERSION 1.0.0)
include(cmake/CXXStandard.cmake)

add_subdirectory(RTNeural)

include(cmake/SIMDExtensions.cmake)
include(cmake/ChooseBackend.cmake)
include(cmake/CPM.cmake)
include(cmake/Testing.cmake)

option(BUILD_TESTS "Build RTNeural accuracy tests" OFF)
if(BUILD_TESTS)
    message(STATUS "RTNeural -- Configuring tests...")
    rtneural_setup_testing()
    add_subdirectory(tests)
endif()

option(BUILD_BENCH "Build RTNeural benchmarks" OFF)
if(BUILD_BENCH)
    message(STATUS "RTNeural -- Configuring benchmarks...")
    add_subdirectory(bench)
endif()

option(BUILD_EXAMPLES "Build RTNeural examples" OFF)
if(BUILD_EXAMPLES)
    message(STATUS "RTNeural -- Configuring examples...")
    add_subdirectory(examples)
endif()
