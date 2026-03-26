cmake_minimum_required(VERSION 3.21)

project(PingPong LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

add_executable(PingPong
        main.cpp
)

add_subdirectory()

find_package(directxtk CONFIG REQUIRED)
target_include_directories(PingPong PRIVATE
        ${CMAKE_CURRENT_SOURCE_DIR}
)

target_link_libraries(PingPong PRIVATE
        Microsoft::DirectXTK
        d3d11
        dxgi
        d3dcompiler
        dxguid
        user32
        gdi32
)
file(COPY ${CMAKE_SOURCE_DIR}/Game/Pong/Assets DESTINATION ${CMAKE_BINARY_DIR}/Game/Pong)

file(COPY
        ${CMAKE_SOURCE_DIR}/Core/Shaders
        DESTINATION ${CMAKE_BINARY_DIR}/Core
)