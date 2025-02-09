cmake_minimum_required(VERSION 3.15..3.31)

set(CMAKE_CXX_STANDARD 26)

project(project-name
    VERSION 1.0
    DESCRIPTION "Some C++ Project"
    LANGUAGES CXX)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/bin")

# Cmake does an empty build type. Set default
set(default_build_type "Debug")
if(NOT CMAKE_BUILD_TYPE AND NOT CMAKE_CONFIGURATION_TYPES)
  message(STATUS "Setting build type to '${default_build_type}' as none was specified.")
  set(CMAKE_BUILD_TYPE "${default_build_type}" CACHE
      STRING "Choose the type of build." FORCE)
  # Set the possible values of build type for cmake-gui
  set_property(CACHE CMAKE_BUILD_TYPE PROPERTY STRINGS
    "Debug" "Release" "MinSizeRel" "RelWithDebInfo")
endif()

# only do the following if this is the main project and not a subdirectory
if(CMAKE_PROJECT_NAME STREQUAL PROJECT_NAME)

    # ensure -std=c++xx instead of -std=g++xx
    set(CMAKE_CXX_EXTENSIONS OFF)

    include(CTest)
    find_package(GTest REQUIRED)

    find_package(Doxygen)
    if(Doxygen_FOUND)
        add_subdirectory(docs)
    else()
        message(STATUS "Doxygen not found, not building docs")
    endif()
endif()

# external packages
find_package(Boost REQUIRED)

add_subdirectory(src)
add_subdirectory(apps)
if(CMAKE_PROJECT_NAME STREQUAL PROJECT_NAME)
    add_subdirectory(tests)
endif()

