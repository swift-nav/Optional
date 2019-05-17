project(optional)
cmake_minimum_required(VERSION 2.8)

set(CMAKE_CXX_FLAGS "-std=c++11 -Wall -Wextra")

add_library(optional INTERFACE)
target_include_directories(optional
    INTERFACE $<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}>
    )

option(OptionalBuildTests "Build optional library unit tests" ON)
if(OptionalBuildTests)
  enable_testing()
  add_executable(test_optional test_optional.cpp)
  add_executable(test_type_traits test_type_traits.cpp)

  add_test(test_optional test_optional)
  add_test(test_type_traits test_type_traits)
endif()
