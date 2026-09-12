cmake_minimum_required(VERSION 3.30)
project(spot_future_arbitrage)

set(CMAKE_CXX_STANDARD 20)

add_compile_options(
        -fsanitize=thread
        -g
        -O1
        -fno-omit-frame-pointer
)

add_link_options(
        -fsanitize=thread
)

find_package(GTest CONFIG REQUIRED)

add_executable(spot_future_arbitrage main.cpp)

target_include_directories(spot_future_arbitrage PRIVATE
        ${CMAKE_SOURCE_DIR}/include)

target_link_libraries(spot_future_arbitrage)


# --- Testing setup ---

enable_testing()

add_executable(spot_future_arbitrage_tests
    tests/tick_handler_test.cpp
        src/tick_handler.cpp

)

target_include_directories(spot_future_arbitrage_tests PRIVATE include)

target_link_libraries(spot_future_arbitrage_tests PRIVATE
    GTest::gtest
    GTest::gtest_main
)

include(GoogleTest)
gtest_discover_tests(spot_future_arbitrage_tests)

