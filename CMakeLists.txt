cmake_minimum_required(VERSION 3.15..3.31)

set(CMAKE_CXX_STANDARD 20)

project(<ProjectNameHere> VERSION 1.0
    DESCRIPTION "Some C++ project"
    LANGUAGES CXX)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/bin")

# Cmake does an empty build type. Set default
set(default_build_type "Release")
if(NOT CMAKE_BUILD_TYPE AND NOT CMAKE_CONFIGURATION_TYPES)
  message(STATUS "Setting build type to '${default_build_type}' as none was specified.")
  set(CMAKE_BUILD_TYPE "${default_build_type}" CACHE
      STRING "Choose the type of build." FORCE)
  # Set the possible values of build type for cmake-gui
  set_property(CACHE CMAKE_BUILD_TYPE PROPERTY STRINGS
    "Debug" "Release" "MinSizeRel" "RelWithDebInfo")
endif()

find_package(gtest REQUIRED)
# find_package(Boost REQUIRED)

# add headers so they show up in IDEs
# add_executable(some_exec apps/source.cc include/header.hh)

# add_library(some_lib STATIC src/source.cc include/header.hh)


add_subdirectory(src)
add_subdirectory(apps)
add_subdirectory(test)

# target_link_libraries(some_exec PRIVATE some_lib)

include(CTest)
