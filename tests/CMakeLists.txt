add_executable(testlib test_utils.cpp
    ${PROJECT_SOURCE_DIR}/include/${PROJECT_NAME}/example_header.hpp)

target_compile_features(testlib PRIVATE cxx_std_26)

target_link_libraries(testlib PRIVATE gtest_main utils)

# register a test for ctest
add_test(NAME testlibtest COMMAND testlib)
