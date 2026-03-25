cmake_minimum_required(VERSION 3.15)
project(jerboa-flipper)

set(CMAKE_CXX_STANDARD 20)

# Build the SDK (disables examples and candletool to keep build fast)
set(CANDLESDK_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)
set(CANDLESDK_BUILD_CANDLETOOL OFF CACHE BOOL "" FORCE)
add_subdirectory(CANdle-SDK)

add_executable(motor_control motor_control.cpp)

# All SDK include paths are inherited via the PUBLIC target_include_directories in candlelib
target_link_libraries(motor_control PRIVATE candle pthread -static-libstdc++ -static-libgcc)
