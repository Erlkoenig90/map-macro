cmake_minimum_required(VERSION 3.10)

project(MapMacroTestsuite)
enable_testing()

add_custom_command(
    OUTPUT  autotest.c
    COMMAND python3 ./gentest.py ${CMAKE_CURRENT_BINARY_DIR}/autotest.c
    DEPENDS gentest.py
)

set(CMAKE_C_STANDARD 99)
set(CMAKE_C_STANDARD_REQUIRED True)

add_executable(MapMacroTestsuite ${CMAKE_CURRENT_BINARY_DIR}/autotest.c)

add_test(AutoTest MapMacroTestsuite)

