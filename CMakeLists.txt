cmake_minimum_required(VERSION 3.16)

project(SouthProject VERSION 3.0.0 LANGUAGES CXX)

set(CMAKE_INCLUDE_CURRENT_DIR ON)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)


message(STATUS "交叉编译模式: ${CMAKE_SYSTEM_PROCESSOR}")
message(STATUS "构建类型: ${CMAKE_BUILD_TYPE}")

# 源文件
set(SOURCES
    main.cpp
)


add_executable(${PROJECT_NAME} ${SOURCES})
# 设置输出名称和属性
set_target_properties(${PROJECT_NAME} PROPERTIES
    OUTPUT_NAME "AcquisitionServer"     # 输出文件基本名称
    DEBUG_POSTFIX "-d"                  # Debug版本后缀
    RELEASE_POSTFIX ""                  # Release版本无后缀
)

# 设置可执行文件的本地（编译机）安装目录-->/tmp
set(EXECUTABLE_OUTPUT_PATH "/tmp/")
# 设置可执行文件exe_name的远程（待部署机）安装目录-->/tmp
