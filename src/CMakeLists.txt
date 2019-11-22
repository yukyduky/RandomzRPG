cmake_minimum_required(VERSION 3.8)

# List source file directories
file(GLOB_RECURSE "${PROJECT_NAME}_SRC"
	"*.cpp"
	"*.h"
	"*.hpp"
)

add_executable(${PROJECT_NAME} ${${PROJECT_NAME}_SRC})

target_link_libraries(${PROJECT_NAME} general "${CMAKE_SOURCE_DIR}/libs/x86/sfml/openal32.lib")

target_link_libraries(${PROJECT_NAME} debug "${CMAKE_SOURCE_DIR}/libs/x86/sfml/debug/sfml-audio-d.lib")
target_link_libraries(${PROJECT_NAME} debug "${CMAKE_SOURCE_DIR}/libs/x86/sfml/debug/sfml-graphics-d.lib")
target_link_libraries(${PROJECT_NAME} debug "${CMAKE_SOURCE_DIR}/libs/x86/sfml/debug/sfml-main-d.lib")
target_link_libraries(${PROJECT_NAME} debug "${CMAKE_SOURCE_DIR}/libs/x86/sfml/debug/sfml-system-d.lib")
target_link_libraries(${PROJECT_NAME} debug "${CMAKE_SOURCE_DIR}/libs/x86/sfml/debug/sfml-window-d.lib")

target_link_libraries(${PROJECT_NAME} optimized "${CMAKE_SOURCE_DIR}/libs/x86/sfml/release/sfml-audio.lib")
target_link_libraries(${PROJECT_NAME} optimized "${CMAKE_SOURCE_DIR}/libs/x86/sfml/release/sfml-graphics.lib")
target_link_libraries(${PROJECT_NAME} optimized "${CMAKE_SOURCE_DIR}/libs/x86/sfml/release/sfml-main.lib")
target_link_libraries(${PROJECT_NAME} optimized "${CMAKE_SOURCE_DIR}/libs/x86/sfml/release/sfml-system.lib")
target_link_libraries(${PROJECT_NAME} optimized "${CMAKE_SOURCE_DIR}/libs/x86/sfml/release/sfml-window.lib")

target_include_directories(${PROJECT_NAME} PUBLIC "${CMAKE_SOURCE_DIR}/includes")

# Make sure that the linker language gets set to C++
set_target_properties(${PROJECT_NAME} PROPERTIES LINKER_LANGUAGE CXX)

set_target_properties(${PROJECT_NAME} PROPERTIES RUNTIME_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}/output")
set_target_properties(${PROJECT_NAME} PROPERTIES LIBRARY_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}/output")
set_target_properties(${PROJECT_NAME} PROPERTIES ARCHIVE_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}/output")