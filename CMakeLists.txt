cmake_minimum_required(VERSION 3.10)
project(bird_project)

set(CMAKE_TOOLCHAIN_FILE "C:/vcpkg/scripts/buildsystems/vcpkg.cmake")

include_directories(include)

add_executable(bird_project include/barrier.h include/bird.h include/button.h include/game.h include/gameoverwindow.h include/menu.h src/barrier.cpp src/bird.cpp src/button.cpp src/game.cpp src/gameoverwindow.cpp src/main.cpp src/menu.cpp)

find_package(SFML 2.5 COMPONENTS system window graphics network audio REQUIRED)
target_link_libraries(bird_project sfml-system sfml-window sfml-graphics sfml-network sfml-audio)