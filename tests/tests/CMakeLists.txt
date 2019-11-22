cmake_minimum_required (VERSION 3.8)

# List source file directories
file(GLOB_RECURSE TEST_SRC
	"*.h"
	"*.hpp"
	"*.cpp"
)

add_executable(tests ${TEST_SRC})

# Make sure that the linker language gets set to C++
set_target_properties(tests PROPERTIES LINKER_LANGUAGE CXX)

set_target_properties(tests PROPERTIES RUNTIME_OUTPUT_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/output")
set_target_properties(tests PROPERTIES LIBRARY_OUTPUT_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/output")
set_target_properties(tests PROPERTIES ARCHIVE_OUTPUT_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/output")

target_link_libraries(tests gtest gmock_main)

target_include_directories(tests PUBLIC "${CMAKE_SOURCE_DIR}/src")

add_test(NAME tests COMMAND tests)