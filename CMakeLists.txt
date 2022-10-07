# CMake dependencies
cmake_minimum_required(VERSION 3.24.2)
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

project(CrossPlatformProject)

# File dependency
file(GLOB HEADERS "./includes/*.hpp")
file(GLOB SOURCES "./sources/*.cpp")

# OS type
if (UNIX)

    # Project binary type
    add_executable(Template.out ${HEADERS} ${SOURCES})

    # Project compilation flags
    target_compile_options(Template.out PRIVATE -std=c++20 -Wall -Wextra -Werror -Wpedantic -g) # -Wall -Wextra -Werror -Wpedantic

    # Project library linking flag
    target_link_libraries(Template.out)

    # Project dependencies
    target_include_directories(Template.out PRIVATE includes)

elseif (WIN32)

    # Project binary type
    add_executable(Template ${HEADERS} ${SOURCES})
    
    # Project compilation flags
    target_compile_options(Template PRIVATE /std:c++20 /Wall /permissive-)

    # Project library linking flag
    target_link_libraries(Template)

    # Project dependencies
    target_include_directories(Template PRIVATE includes)

endif()
