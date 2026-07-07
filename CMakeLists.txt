cmake_minimum_required(VERSION 3.10)

# 将 vcpkg 安装路径添加到 CMake 搜索路径
# 如果你的 vcpkg 安装在其他位置，请修改此行
list(APPEND CMAKE_PREFIX_PATH "${CMAKE_SOURCE_DIR}/vcpkg_installed/x64-mingw-dynamic")

project(HelloWorld)

find_package(fmt CONFIG REQUIRED)
find_package(GTest REQUIRED)

# 主程序
add_executable(HelloWorld main.cpp)
target_link_libraries(HelloWorld PRIVATE fmt::fmt)

# 测试程序
add_executable(HelloWorldTests tests/main_test.cpp)
target_link_libraries(HelloWorldTests PRIVATE GTest::gtest_main fmt::fmt)
