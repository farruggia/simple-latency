project(lm-bench)

message(STATUS "Compiler: ${CMAKE_CXX_COMPILER_ID}")

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -O -DRUSAGE -DHAVE_uint=1 -DHAVE_int64_t=1 -DHAVE_DRAND48 -DHAVE_SCHED_SETAFFINITY=1")
set(libraries src/getopt.c src/lib_timing.c src/lib_mem.c src/lib_sched.c)

add_library(bench_objs ${libraries})

add_executable(lat_mem_rd src/lat_mem_rd.c)
target_link_libraries(lat_mem_rd bench_objs m)