cmake_minimum_required(VERSION 3.16)

project(hello_headers)

# SOURCES is a variable name, the following is its content
set(SOURCES
    src/Hello.cc
    src/main.cc
)
# you can also do like this:
# file(GLOB SOURCES "src/*.cc")
# But in modern practice, both of them are recommended
# because it is not recommended to declare sources as a variable
# instead it is expected to add them directly to 'add_xxx()' function

add_executable(${PROJECT_NAME} ${SOURCES})

# this function add include folders
target_include_directories(hello_headers
    PRIVATE
        ${PROJECT_SOURCE_DIR}/include
)
# 'PRIVATE' indicate the scope of the include. Explained in next example
