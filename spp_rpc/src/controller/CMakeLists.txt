add_executable(
        spp_ctrl
        defaultctrl.cpp
        main.cpp
)


find_library(
        MONITOR_CLIENT
        libmonitor.a
        ${PROJECT_SOURCE_DIR}/internal/monitor/lib
)


target_link_libraries(
        spp_ctrl
        common
        spp_micro_thread
        spp_sync_frame
        bench_adapter
        dl
        spp_exception
        ${MONITOR_CLIENT}
)