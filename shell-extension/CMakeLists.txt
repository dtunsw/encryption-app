cmake_minimum_required(VERSION 3.20)
project(MyVaultShell LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Cô lập runtime C++ (/MT) để DLL chạy độc lập trong explorer.exe
set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")

find_package(nlohmann_json CONFIG REQUIRED)

# Khai báo xuất ra file thư viện động (.dll)
add_library(MyVaultShell SHARED
    src/dllmain.cpp
)

target_link_libraries(MyVaultShell PRIVATE
    nlohmann_json::nlohmann_json
    shlwapi.lib
    shell32.lib
    ole32.lib
)