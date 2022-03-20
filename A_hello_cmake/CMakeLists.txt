cmake_minimum_required(VERSION 3.16)

# Set the project name
project(hello_cmake)

# add an executable
add_executable(hello_cmake main.cc)
# executable name and project name are two different concept
# but many will use the same name, so you can also do like this:
# add_executable(${PROJECT_NAME} main.cc)
