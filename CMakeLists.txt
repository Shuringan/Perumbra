cmake_minimum_required(VERSION 3.15)
project(Perumbra)

set(CMAKE_CXX_STANDARD 17)

# GLAD
add_library(glad STATIC external/glad/src/gl.c)
target_include_directories(glad PUBLIC external/glad/include)

# GLFW
add_subdirectory(external/glfw)

# source
file(GLOB_RECURSE SOURCES CONFIGURE_DEPENDS src/*.cpp)

add_executable(Perumbra ${SOURCES})

target_include_directories(Perumbra PUBLIC
    src
    external/glad/include
    external/glfw/include
)

target_link_libraries(Perumbra
    glad
    glfw
    ${CMAKE_DL_LIBS}
)
