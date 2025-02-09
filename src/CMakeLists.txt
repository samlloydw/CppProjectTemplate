set(HEADER_LIST "${PROJECT_SOURCE_DIR}/include/${PROJECT_NAME}/example_header.hpp")

add_library(utils STATIC utils.cpp "${HEADER_LIST}")
target_include_directories(utils PUBLIC "${PROJECT_SOURCE_DIR}/include")
target_link_libraries(utils PUBLIC Boost::boost)
target_compile_features(utils PUBLIC cxx_std_26)

# IDEs put headers in nice place
source_group(TREE "${PROJECT_SOURCE_DIR}/include"
    PREFIX "Header Files"
    FILES "${HEADER_LIST}")

