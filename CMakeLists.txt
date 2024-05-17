cmake_minimum_required(VERSION 3.25.1)

set(PROJECT_NAME SickleHa)

project(${PROJECT_NAME})

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CURRENT_BINARY_DIR /build/bin/)

file(GLOB_RECURSE H_SRC
        src/*.h
        src/*.hpp
)
file(GLOB_RECURSE CPP_SRC
        src/*.cpp
)

# If current platform is Linux
if (CMAKE_SYSTEM_NAME MATCHES "Linux")

    add_executable(${PROJECT_NAME} src/main.cpp ${H_SRC} ${CPP_SRC})

endif (CMAKE_SYSTEM_NAME MATCHES "Linux")


# If current platform is Windows
if (CMAKE_SYSTEM_NAME MATCHES "Windows")

    set(CMAKE_EXE_LINKER_FLAGS "-static")
    add_executable(${PROJECT_NAME} src/main.cpp ${H_SRC} ${CPP_SRC})

endif (CMAKE_SYSTEM_NAME MATCHES "Windows")
