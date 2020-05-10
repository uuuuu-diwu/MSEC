include_directories(
        ${PROJECT_SOURCE_DIR}/worker
)

add_library(
        spp_sync_frame
        SyncFrame.cpp
)

target_link_libraries(
        spp_sync_frame
        spp_micro_thread
        common
)