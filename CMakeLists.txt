cmake_minimum_required(VERSION 3.24)
project(imcurve)

add_library(imcurve INTERFACE)
add_library(imcurve::imcurve ALIAS imcurve)
set_target_properties(imcurve PROPERTIES CXX_STANDARD 23)
target_include_directories(imcurve INTERFACE ${CMAKE_CURRENT_SOURCE_DIR})

if(PROJECT_IS_TOP_LEVEL)
    set(BINARY_DIR ${CMAKE_BINARY_DIR}/bin)
    set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${BINARY_DIR})
    set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_RELEASE ${BINARY_DIR})
    set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_DEBUG ${BINARY_DIR})
    set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${BINARY_DIR})
    set(CMAKE_LIBRARY_OUTPUT_DIRECTORY_RELEASE ${BINARY_DIR})
    set(CMAKE_LIBRARY_OUTPUT_DIRECTORY_DEBUG ${BINARY_DIR})
    add_subdirectory(lib/SDL)
    add_executable(imcurve_example
        example/main.cpp
        lib/imgui/backends/imgui_impl_sdl3.cpp
        lib/imgui/backends/imgui_impl_sdlrenderer3.cpp
        lib/imgui/imgui.cpp
        lib/imgui/imgui_demo.cpp
        lib/imgui/imgui_draw.cpp
        lib/imgui/imgui_tables.cpp
        lib/imgui/imgui_widgets.cpp
    )
    target_include_directories(imcurve_example PRIVATE lib/imgui lib/imgui/backends)
    set_target_properties(imcurve_example PROPERTIES CXX_STANDARD 23)
    target_link_libraries(imcurve_example PRIVATE SDL3::SDL3 imcurve)
endif()
