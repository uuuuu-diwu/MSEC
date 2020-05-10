project(spp_rpc)

cmake_minimum_required(VERSION 3.6.2)
include_directories(
        comm
        internal/monitor/include
        internal/log/include
        internal/nlb/include
        internal/se/
        sync_frame/spp_plugin/
        sync_frame/micro_thread/
        sync_frame/valgrind
        rpc/
)
set(CMAKE_POSITION_INDEPENDENT_CODE ON)

SET(CMAKE_CXX_FLAGS_DEBUG "$ENV{CXXFLAGS} -O0 -Wall -g -ggdb")  # Debug模式下的编译指令
SET(CMAKE_CXX_FLAGS_RELEASE "$ENV{CXXFLAGS} -O3 -Wall")         # Release模式下的编译指令



SET(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/spp_compile_bin/)       #设置可执行文件的输出目录

SET(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/spp_compile_bin/)           #设置库文件的输出目录


set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_DEBUG ${PROJECT_SOURCE_DIR}/spp_compile_bin/)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_RELEASE ${PROJECT_SOURCE_DIR}/spp_compile_bin/)



add_subdirectory(
        comm
)


add_subdirectory(
        internal
)

add_subdirectory(
        sync_frame/micro_thread
)

add_subdirectory(
        sync_frame/spp_plugin
)


add_subdirectory(
        controller
)

add_subdirectory(
        proxy
)

add_subdirectory(
        worker
)

add_subdirectory(
        tool
)

add_library(
        echo
        SHARED
        module/example/simple/echo_example.cpp
)

target_link_libraries(
        echo
        common
)