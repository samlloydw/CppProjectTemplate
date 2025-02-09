add_executable(app main.cpp)

target_compile_features(app PRIVATE cxx_std_26)

target_link_libraries(app PRIVATE utils)
