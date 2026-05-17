cmake_minimum_required(VERSION 3.16)
project(TetrisSFML LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

add_executable(tetris main.cpp)

target_compile_options(tetris PRIVATE
    $<$<CXX_COMPILER_ID:MSVC>:/W4>
    $<$<NOT:$<CXX_COMPILER_ID:MSVC>>:-Wall -Wextra -Wpedantic>
)

# Prefer CMake's SFML module for Linux distro packages (e.g., apt libsfml-dev).
find_package(SFML 2.5 REQUIRED COMPONENTS graphics window system)

target_link_libraries(tetris PRIVATE
    sfml-graphics
    sfml-window
    sfml-system
)

add_custom_command(TARGET tetris POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_directory
            ${CMAKE_SOURCE_DIR}/images
            $<TARGET_FILE_DIR:tetris>/images
)
