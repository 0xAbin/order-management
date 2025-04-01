cmake_minimum_required(VERSION 3.10)

# Project name
project(DeribitTradingSystem VERSION 1.0 LANGUAGES CXX)

# Specify C++ standard
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Include directories
include_directories(${PROJECT_SOURCE_DIR}/include)

# Enable more warnings and optimization
add_compile_options(-Wall -Wextra -Wpedantic -O3)

# Find Boost and OpenSSL libraries
find_package(Boost 1.87 REQUIRED COMPONENTS system thread)
find_package(OpenSSL REQUIRED)

if (Boost_FOUND)
    include_directories(${Boost_INCLUDE_DIRS})
    message(STATUS "Boost found: ${Boost_INCLUDE_DIRS}")
    message(STATUS "Boost libraries: ${Boost_LIBRARIES}")
else()
    message(FATAL_ERROR "Boost not found!")
endif()

if (OpenSSL_FOUND)
    message(STATUS "OpenSSL found: ${OPENSSL_VERSION}")
else()
    message(FATAL_ERROR "OpenSSL not found!")
endif()

# Add source files
file(GLOB_RECURSE SOURCES "src/*.cpp")

# Create a static library from core sources
add_library(CoreLib STATIC ${SOURCES})

# Add main executable
add_executable(DeribitTradingSystem src/main.cpp)

# Link libraries to the executable
target_link_libraries(DeribitTradingSystem PRIVATE
        CoreLib
        ${Boost_LIBRARIES}
        OpenSSL::SSL
        OpenSSL::Crypto
        pthread
)

# Tests
add_subdirectory(tests)

# Install target
install(TARGETS DeribitTradingSystem DESTINATION bin)
install(DIRECTORY include/ DESTINATION include)

# Output directory
set_target_properties(DeribitTradingSystem PROPERTIES
        RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/bin"
)

# Print success message
message(STATUS "Deribit Trading System configured successfully!")
