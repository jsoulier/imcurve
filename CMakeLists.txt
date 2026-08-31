cmake_minimum_required(VERSION 3.24)
project(imcurve)

add_library(imcurve INTERFACE)
add_library(imcurve::imcurve ALIAS imcurve)
set_target_properties(imcurve PROPERTIES CXX_STANDARD 20)
target_include_directories(imcurve INTERFACE ${CMAKE_CURRENT_SOURCE_DIR})
