project(spp_demo)
cmake_minimum_required(VERSION 3.5.1)

include_directories(
        ../micro_thread/include
        ../spp_frame/include
)

add_library(
        echo_svr
        SHARED
        echo_example.cpp
)