include_directories(
        libunwind
        libbacktrace
)
add_library(
        spp_exception
        bthelper.c
        exception.c
        mem.c
        memlog.c
        vma.c
)


link_directories(
        ./libbacktrace
        ./libunwind
)


add_executable(
        exception_test
        setest.c
)

target_link_libraries(
        exception_test
        spp_exception
        backtrace
        unwind-x86_64
        unwind
)

