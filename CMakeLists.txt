cmake_minimum_required(VERSION 3.26)

project(MicroBenchmark CXX)

list(APPEND CMAKE_MODULE_PATH "${CMAKE_SOURCE_DIR}/cmake_modules" C:/rocm/5.5/lib/cmake/hip)

set(hip_DIR C:/rocm/5.5/lib/cmake/hip)
find_package(hip)

message(STATUS "${HIP_INCLUDE_DIR}")
message(STATUS "${HIP_INCLUDE_DIRS}")
message(STATUS "${HIP_LIB_INSTALL_DIR}")
message(STATUS "${HIP_BIN_INSTALL_DIR}")
message(STATUS "${HIP_LIBRARIES}")
message(STATUS "${HIP_LIBRARY}")
message(STATUS "${HIP_HIPCC_EXECUTABLE}")
message(STATUS "${HIP_HIPCONFIG_EXECUTABLE}")

# include(FetchContent)
# FetchContent_Declare(googletest
#         GIT_REPOSITORY https://github.com/google/googletest.git
#         GIT_TAG main)

# FetchContent_Declare(googlebenchmark
#         GIT_REPOSITORY https://github.com/google/benchmark.git
#         GIT_TAG main) # need master for benchmark::benchmark

# FetchContent_MakeAvailable(
#         googletest
#         googlebenchmark)

file(GLOB_RECURSE SOURCE_FILES inc/* src/*)

add_executable(MicroBenchmark ${SOURCE_FILES})
target_link_libraries(MicroBenchmark hip::host hip::device)
target_include_directories(MicroBenchmark PUBLIC inc)
target_include_directories(MicroBenchmark PUBLIC hip::host hip::device)
