# minimum required cmake version for this project
cmake_minimum_required(VERSION 3.25 FATAL_ERROR)

# project details
project(
        "FirstProjectInCMake"
        VERSION 1.0.0
        DESCRIPTION "CMake C Project Template for Operating System II"
        LANGUAGES C
)


set(CMAKE_C_STANDARD 17)

# include directory for headers
include_directories(include)

# Defino las flags del proyecto
set(CMAKE_C_FLAGS )

# sources for .c files
file(GLOB_RECURSE SOURCES "src/*.c")

# make the executable
add_executable(${PROJECT_NAME} ${SOURCES})

# compile the libraries
# find in the argument's directory CMake files and considers it like an individual project
add_subdirectory(lib/libdyn)
add_subdirectory(lib/libsta)

# include the headers in lib (target headers)
target_include_directories(${PROJECT_NAME} PUBLIC lib/libdyn/include)
target_include_directories(${PROJECT_NAME} PUBLIC lib/libsta/include)

# link the libraries
target_link_libraries(${PROJECT_NAME} StatiCLib DynamiCLib)




