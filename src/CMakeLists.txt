set(HEADER_LIST "${CMAKE_CURRENT_SOURCE_DIR}/include/lib.hh")

add_library(another_lib STATIC lib.cc "${HEADER_LIST}")
target_include_directories(another_lib PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/include")
target_link_libraries(some_lib PUBLIC another_lib)
target_compile_features(another_lib PUBLIC cxx_std_20)

# IDEs put headers in nice place
source_group(
    TREE "${PROJECT_SOURCE_DIR}/include"
    PREFIX "Header Files"
    FILES "${HEADER_LIST})
