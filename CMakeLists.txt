cmake_minimum_required(VERSION 3.10)

# 项目名称和版本号
project(UN_FVM VERSION 1.2.0)

# 设置 C++ 标准
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# 编译选项
# 设置调试选项
if(CMAKE_BUILD_TYPE STREQUAL "Debug")
    # set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O3")
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O0 -g")
else()
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -O3")
endif()

# 包含目录
include_directories(${PROJECT_SOURCE_DIR}/include)

# 查找所有的源文件（.cpp 文件）
file(GLOB_RECURSE SRC_FILES
    "${PROJECT_SOURCE_DIR}/src/*.cpp"
)

# 查找所有的头文件（.hpp 和 .inl 文件）
file(GLOB_RECURSE HEADER_FILES
    "${PROJECT_SOURCE_DIR}/include/*.h"
)

# 将可执行文件放在 bin 目录下
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/run)

# 定义目标可执行文件
add_executable(Unstruct2D ${SRC_FILES} ${HEADER_FILES})

