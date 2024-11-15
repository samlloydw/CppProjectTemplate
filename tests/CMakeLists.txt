add_executable(testlib testlib.cpp)

target_compile_features(testlib PRIVATE cxx_std_20)

target_link_libraries(testlib PRIVATE some_exec)

# register a test for ctest
add_test(NAME testlibtest COMMAND testlib)
