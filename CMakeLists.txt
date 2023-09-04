#[[
# Author : KeeneChen
# Date   : 2023.09.04-11:40:29
]]

cmake_minimum_required(VERSION 3.10...3.20)

project(
  cmake_template
  VERSION 1.0.1
  DESCRIPTION "cmake_template"
  HOMEPAGE_URL "https://github.com/KeeneChen/cmake_template"
  LANGUAGES C CXX)

# 包括 kc_conf.cmake 模块,调用其中定义的宏
list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake")
include(kc_conf)
enable_kc_colors()
enable_kc_debug()

# 设置可执行文件、库生成位置
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)

# 开启测试
enable_testing()

# 添加子目录
add_subdirectory(src)
add_subdirectory(third_party)
