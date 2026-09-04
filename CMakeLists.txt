cmake_minimum_required(VERSION 3.30)
project(spot_future_arbitrage)

set(CMAKE_CXX_STANDARD 20)

find_package(fmt CONFIG REQUIRED)

add_executable(spot_future_arbitrage main.cpp)

target_link_libraries(spot_future_arbitrage PRIVATE
        fmt::fmt
)




