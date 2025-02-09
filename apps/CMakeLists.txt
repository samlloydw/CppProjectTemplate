# add headers so they show up in IDEs
add_executable(app main.cpp ${PROJECT_SOURCE_DIR}/include/project-name/example_header.hpp)

target_compile_features(app PRIVATE cxx_std_26)

target_link_libraries(app PRIVATE utils)
