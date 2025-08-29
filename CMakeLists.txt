cmake_minimum_required(VERSION 3.5)
project(optional)

add_library(akrzemi1_optional INTERFACE)
add_library(optional ALIAS akrzemi1_optional)
add_library(akrzemi1::optional ALIAS akrzemi1_optional)
target_include_directories(akrzemi1_optional
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
