cmake_minimum_required(VERSION 3.10)
project(MyGame)

# Set C and C++ standards
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

# Include directories
include_directories(include)

# Add source files
file(GLOB SOURCES "src/*.c")

# Find required packages
find_package(OpenGL REQUIRED)
find_package(PkgConfig REQUIRED)
pkg_check_modules(SDL2 REQUIRED sdl2)
pkg_check_modules(GLFW REQUIRED glfw3)
pkg_check_modules(OpenAL REQUIRED openal)

# Add executable
add_executable(MyGame ${SOURCES})

# Link libraries
target_include_directories(MyGame PRIVATE ${SDL2_INCLUDE_DIRS} ${GLFW_INCLUDE_DIRS} ${OpenAL_INCLUDE_DIRS})
target_link_libraries(MyGame PRIVATE ${SDL2_LIBRARIES} ${GLFW_LIBRARIES} ${OpenAL_LIBRARIES} OpenGL::GL)

