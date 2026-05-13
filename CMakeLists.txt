cmake_minimum_required(VERSION 3.16)

project(unitree_uc
    VERSION 0.1.0
    DESCRIPTION "Unitree UC C++ project"
    LANGUAGES CXX
)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

find_package(unitree_sdk2 CONFIG REQUIRED)

set(UNITREE_UC_INCLUDE_DIR "${CMAKE_CURRENT_SOURCE_DIR}/include")

add_executable(${PROJECT_NAME}
    src/main.cpp
)

target_include_directories(${PROJECT_NAME} PRIVATE
    "${UNITREE_UC_INCLUDE_DIR}"
)

target_link_libraries(${PROJECT_NAME} PRIVATE unitree_sdk2)

if(MSVC)
    target_compile_options(${PROJECT_NAME} PRIVATE /W4 /permissive-)
else()
    target_compile_options(${PROJECT_NAME} PRIVATE -Wall -Wextra -Wpedantic)
endif()
