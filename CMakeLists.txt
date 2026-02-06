cmake_minimum_required(VERSION 4.1)
project(GuTorrent)

set(CMAKE_CXX_STANDARD 20)

##############
# Libtorrent #
##############

include(FetchContent)

set(build_tests OFF CACHE BOOL "" FORCE)
set(build_examples OFF CACHE BOOL "" FORCE)
set(build_tools OFF CACHE BOOL "" FORCE)
set(python-bindings OFF CACHE BOOL "" FORCE)

FetchContent_Declare(
        libtorrent
        GIT_REPOSITORY https://github.com/arvidn/libtorrent.git
        GIT_TAG v2.0.11
)

FetchContent_MakeAvailable(libtorrent)

find_package(Qt6 REQUIRED COMPONENTS Core Widgets Network)

add_executable(GuTorrent main.cpp)

target_link_libraries(GuTorrent PRIVATE
        Qt6::Core Qt6::Widgets Qt6::Network torrent-rasterbar
)