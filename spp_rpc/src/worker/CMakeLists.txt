

add_executable(
        spp_worker
        defaultworker.cpp
        main.cpp
)



link_directories(
        ${PROJECT_SOURCE_DIR}/spp_compile_bin/
        ${PROJECT_SOURCE_DIR}/internal/se/libbacktrace/
        ${PROJECT_SOURCE_DIR}/internal/se/libunwind/
)


find_library(
        UNWIND_64
        libunwind-x86_64.a
        ${PROJECT_SOURCE_DIR}/internal/se/libunwind/
)

find_library(
        UNWIND
        libunwind.a
        ${PROJECT_SOURCE_DIR}/internal/se/libunwind/
)

find_library(
        BACKTRACE
        libbacktrace.a
        ${PROJECT_SOURCE_DIR}/internal/se/libbacktrace/
)


find_library(
        MONITOR_CLIENT
        libmonitor.a
        ${PROJECT_SOURCE_DIR}/internal/monitor/lib
)


target_link_libraries(
        spp_worker
        common
        spp_micro_thread
        spp_sync_frame
        bench_adapter
        dl
        spp_exception
        ${UNWIND_64}
        ${UNWIND}
        ${BACKTRACE}
        ${MONITOR_CLIENT}
)