# For more information about using CMake with Android Studio, read the
# documentation: https://d.android.com/studio/projects/add-native-code.html

# Sets the minimum version of CMake required to build the native library.

cmake_minimum_required(VERSION 3.10.2)

# Declares and names the project.

project("neaes")

# 正则匹配当前项目中的 所有的C++ 源码
file(GLOB_RECURSE SRC_NEAES_JNI ./*.cpp)
list(APPEND SRC_LIST ${SRC_NEAES_JNI})

# 生成链接库
add_library(
        # library name
        neaes-lib
        # shared library
        SHARED

        ""
)

target_sources(
        neaes-lib

        PUBLIC
        ${SRC_LIST}
)

# 包含rheia下所有的 .h 头文件
target_include_directories(
        neaes-lib

        PUBLIC
        NEAES.h
)


target_link_libraries(
        neaes-lib)