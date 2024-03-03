# Minimum required CMake version
cmake_minimum_required(VERSION 3.12)

find_package(Vulkan REQUIRED)
find_package(glfw3 REQUIRED)

# Project name
project(vkfw)

# Set C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Find all cpp files in the example directory
file(GLOB EXAMPLE_SOURCES "example/*.cpp")

# Generate a separate binary for each cpp file
foreach(EXAMPLE_SOURCE ${EXAMPLE_SOURCES})
    # Get the base name of the cpp file
    get_filename_component(EXAMPLE_NAME ${EXAMPLE_SOURCE} NAME_WE)

    # Create an executable for each cpp file
    add_executable(${EXAMPLE_NAME} ${EXAMPLE_SOURCE})

    # Add include directories for each target
    target_include_directories(${EXAMPLE_NAME} PRIVATE include)
endforeach()
