cmake_minimum_required(VERSION 3.16)
project(chatrooms)

set(CMAKE_CXX_STANDARD 20)

set(ASIO_DIR "/opt/homebrew/Cellar/asio/1.36.0/include")

add_executable(chatrooms main.cpp
        pch.hpp)

add_library(asio INTERFACE)
target_compile_definitions(asio INTERFACE ASIO_STANDALONE)
target_include_directories(asio INTERFACE ${ASIO_DIR})

target_link_libraries(chatrooms PRIVATE asio)

target_precompile_headers(chatrooms PRIVATE pch.hpp)