cmake_minimum_required(VERSION 3.16)

project(PacketAnalyzer VERSION 1.0 LANGUAGES CXX)

# ------------------------------------------------------------------
# C++ Standard
# ------------------------------------------------------------------

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# ------------------------------------------------------------------
# Include directory
# ------------------------------------------------------------------

include_directories(${PROJECT_SOURCE_DIR}/include)

# ------------------------------------------------------------------
# Compiler settings
# ------------------------------------------------------------------

if(MSVC)
    add_compile_options(/EHsc)
else()
    add_compile_options(-Wall -Wextra -O2)
endif()

# ------------------------------------------------------------------
# Threads
# ------------------------------------------------------------------

find_package(Threads REQUIRED)

# ==================================================================
# 1. Packet Analyzer
# ==================================================================

add_executable(packet_analyzer
    src/main.cpp
    src/pcap_reader.cpp
    src/packet_parser.cpp
)

target_link_libraries(packet_analyzer
    PRIVATE Threads::Threads
)

# ==================================================================
# 2. Simple DPI
# ==================================================================

add_executable(dpi_simple
    src/main_simple.cpp
    src/pcap_reader.cpp
    src/packet_parser.cpp
    src/sni_extractor.cpp
    src/types.cpp
)

target_link_libraries(dpi_simple
    PRIVATE Threads::Threads
)

# ==================================================================
# 3. Working DPI Engine
# ==================================================================

add_executable(dpi_working
    src/main_working.cpp
    src/pcap_reader.cpp
    src/packet_parser.cpp
    src/sni_extractor.cpp
    src/types.cpp
)

target_link_libraries(dpi_working
    PRIVATE Threads::Threads
)

# ==================================================================
# 4. Multi-threaded DPI Engine
# ==================================================================

add_executable(dpi_mt
    src/dpi_mt.cpp
    src/pcap_reader.cpp
    src/packet_parser.cpp
    src/sni_extractor.cpp
    src/types.cpp
)

target_link_libraries(dpi_mt
    PRIVATE Threads::Threads
)

# ------------------------------------------------------------------
# Output folders
# ------------------------------------------------------------------

set_target_properties(
    packet_analyzer
    dpi_simple
    dpi_working
    dpi_mt
    PROPERTIES

    RUNTIME_OUTPUT_DIRECTORY_DEBUG
        ${CMAKE_BINARY_DIR}/Debug

    RUNTIME_OUTPUT_DIRECTORY_RELEASE
        ${CMAKE_BINARY_DIR}/Release
)

# ------------------------------------------------------------------
# Status
# ------------------------------------------------------------------

message(STATUS "")
message(STATUS "=======================================")
message(STATUS " Packet Analyzer Build Configuration")
message(STATUS "=======================================")
message(STATUS "C++ Standard : ${CMAKE_CXX_STANDARD}")
message(STATUS "Compiler     : ${CMAKE_CXX_COMPILER_ID}")
message(STATUS "Build Type   : ${CMAKE_BUILD_TYPE}")
message(STATUS "")
message(STATUS "Targets:")
message(STATUS "  - packet_analyzer")
message(STATUS "  - dpi_simple")
message(STATUS "  - dpi_working")
message(STATUS "  - dpi_mt")
message(STATUS "=======================================")