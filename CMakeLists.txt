cmake_minimum_required(VERSION 2.8)
project(optional)

add_library(optional INTERFACE)
target_include_directories(optional
    INTERFACE $<BUILD_INTERFACE:${PROJECT_SOURCE_DIR}>
    )

option(optional_ENABLE_TESTS "Enable unit tests for Optional" ON)

if(optional_ENABLE_TESTS)
  enable_testing()

  add_executable(test_optional test_optional.cpp)
  set_target_properties(test_optional PROPERTIES CXX_STANDARD 11)
  set_target_properties(test_optional PROPERTIES COMPILE_FLAGS "-Wall -Wextra")
  add_test(test_optional test_optional)

  add_executable(test_type_traits test_type_traits.cpp)
  set_target_properties(test_type_traits PROPERTIES CXX_STANDARD 11)
  set_target_properties(test_type_traits PROPERTIES COMPILE_FLAGS "-Wall -Wextra")
  add_test(test_type_traits test_type_traits)
endif()
