cmake_minimum_required(VERSION 3.10.0)

project(
  test_cmake_template
  VERSION 1.0.0
  DESCRIPTION "test_cmake_template")

# 设置语言标准
set(CMAKE_C_STANDARD 11)
set(CMAKE_C_STANDARD_REQUIRED True)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# 包括colors.cmake模块,调用其中定义的宏
list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake")
include(colors)
define_colors()

# 设置默认构建类型
if(NOT CMAKE_BUILD_TYPE)
  if("${CMAKE_BINARY_DIR}" MATCHES "build_.*(D|d)ebug$")
    message(STATUS "${Red}>>> Build Debug Type >>>${ColourReset}")
    set(CMAKE_BUILD_TYPE "Debug")
  elseif("${CMAKE_BINARY_DIR}" MATCHES "build_.*(R|r)elWithDebInfo$")
    message(STATUS "${Green}>>> Build RelWithDebInfo Type >>>${ColourReset}")
    set(CMAKE_BUILD_TYPE "RelWithDebInfo")
  elseif("${CMAKE_BINARY_DIR}" MATCHES "build_.*(M|m)inSizeRel$")
    message(STATUS "${Blue}>>> Build MinSizeRel Type>>>${ColourReset}")
    set(CMAKE_BUILD_TYPE "MinSizeRel")
  else()
    message(STATUS "${BoldYellow}>>> Build Release Type >>>${ColourReset}")
    set(CMAKE_BUILD_TYPE "Release")
  endif()
endif()

# 设置可执行文件、库生成位置
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)

# 导出编译命令配置,供clangd使用
set(CMAKE_EXPORT_COMPILE_COMMANDS 1)

# 开启测试
enable_testing()

# 添加子目录
add_subdirectory(src)
add_subdirectory(third_party)
