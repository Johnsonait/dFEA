cmake_minimum_required(VERSION 3.18)

# Set the project name and version
set(PROJECT_NAME dFEA)
project(${PROJECT_NAME} VERSION 1.0)

# Specify the C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Set the build type 
set(CMAKE_BUILD_TYPE Release)

# Set optimization flags for the Release build
set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} -O3 -march=native -mtune=native -flto")

set(CMAKE_PREFIX_PATH "/Users/johannscheepers/Documents/pytorch")

# Find the PyTorch package
find_package(Torch REQUIRED)

# Add the executable
add_executable(${PROJECT_NAME} ./src/main.cpp)

# Include directories
include_directories(${CMAKE_SOURCE_DIR}/include)

# Link the PyTorch library
target_link_libraries(${PROJECT_NAME} "${TORCH_LIBRARIES}")

# Set C++ flags for PyTorch
set_property(TARGET ${PROJECT_NAME} PROPERTY CXX_STANDARD 17)

# Add this line to enable RPATH support (helps with locating shared libraries)
set(CMAKE_BUILD_RPATH_USE_ORIGIN TRUE)
