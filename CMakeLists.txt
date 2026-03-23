cmake_minimum_required(VERSION 3.17)
project(HostsMod)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

add_executable(HostsMod src/main.cpp)
if (WIN32)
    target_link_libraries(HostsMod
        wsock32
        ws2_32
        crypt32
        dnsapi
    )
    target_link_options(HostsMod PRIVATE
        -static-libgcc
        -static-libstdc++
        -Wl,-Bstatic,--whole-archive -lwinpthread -Wl,--no-whole-archive
    )
endif()
