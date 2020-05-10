add_executable(
        cost_stat_tool
        cost_stat_tool/main.cpp
)

add_executable(
        shm_key_tool
        shm_key_tool/main.cpp
)

add_executable(
        shmread
        shm_read_tool/shmread.c
)

add_executable(
        stat
        stat_tool/stat.cpp
)

target_link_libraries(
        stat
        common
)

target_link_libraries(
        shm_key_tool
        common
)