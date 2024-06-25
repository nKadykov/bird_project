cmake_minimum_required(VERSION 3.10)
project(bird_project)

set(CMAKE_CXX_STANDART 23)
set(CMAKE_CXX_STANDART_REQUIRED ON)

set(ASSETS_FOLDER ${CMAKE_SOURCE_DIR}/assets)
if(WIN32)
    set(ASSETS_OUTPUT_DIR Release/assets)
else()
    set(ASSETS_OUTPUT_DIR assets)
endif()

set(CMAKE_TOOLCHAIN_FILE "C:/vcpkg/scripts/buildsystems/vcpkg.cmake")

include_directories(include)

add_executable(bird_project include/barrier.h include/bird.h include/button.h include/game.h include/gameoverwindow.h include/menu.h src/barrier.cpp src/bird.cpp src/button.cpp src/game.cpp src/gameoverwindow.cpp src/main.cpp src/menu.cpp)

find_package(SFML 2.5 COMPONENTS system window graphics network audio REQUIRED)
target_link_libraries(bird_project sfml-system sfml-window sfml-graphics sfml-network sfml-audio)

add_custom_command(
    TARGET bird_project POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_directory
    ${ASSETS_FOLDER} ${ASSETS_OUTPUT_DIR}
    COMMENT "Copying assets to output directory"
)