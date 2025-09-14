cmake_minimum_required(VERSION 3.30)
project(metal_cpp_test)

set(CMAKE_CXX_STANDARD 26)

add_compile_options(-Wall -fno-objc-arc)
if(CMAKE_BUILD_TYPE STREQUAL "Debug")
    add_compile_options(-g)
elseif(CMAKE_BUILD_TYPE STREQUAL "Release")
    add_compile_options(-O2)
endif()

add_executable(metal_cpp_test main.cpp)
target_include_directories(metal_cpp_test PRIVATE "./metal-cpp" "./metal-cpp-extensions")
target_link_libraries(metal_cpp_test PRIVATE
        "-framework Metal"
        "-framework Foundation"
        "-framework Cocoa"
        "-framework CoreGraphics"
        "-framework MetalKit"
)