cmake_minimum_required(VERSION 3.16)

project(hello_static_library)

#############################################################
# Create a library
#############################################################

# The source file of the libraray
add_library(hello_library STATIC
    src/Hello.cpp
)

target_include_directories(hello_library
    PUBLIC
        ${PROJECT_SOURCE_DIR}/include
)
# This will define the directory 'include' as a global root of include folder(because PUBLIC)
# So you can use somthing like '#include "static/Hello.h"' in your code to distinguish functions

# And PUBLIC, INTERFACE or PRIVATE?
# Ref: https://zhuanlan.zhihu.com/p/82244559
# In general: 
#   - I use it, and who use me do not use it. Then PRIVATE
#   - I do not use it, or just refer some struct or union, but who use me use it. Then INTERFACE
#   - I use it, and who use me also use it. Then PUBLIC

#############################################################
# Create a executable
#############################################################
add_executable(hello_binary
    src/main.cpp
)

target_link_libraries( hello_binary
    PRIVATE 
        hello_library
)
