cmake_minimum_required(VERSION 3.24)
project(hello_world_project VERSION 1.0.0 LANGUAGES CXX)

# Set the C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Include FetchContent module
include(FetchContent)

# Fetch the mdio-cpp library from the specified branch
FetchContent_Declare(
  mdio
  GIT_REPOSITORY https://github.com/TGSAI/mdio-cpp.git
  GIT_TAG main
)
FetchContent_MakeAvailable(mdio)

# Create an executable target
add_executable(dataset_example src/dataset_example.cc)

# Link the mdio library to the executable
target_link_libraries(dataset_example PRIVATE 
  mdio
  ${mdio_INTERNAL_DEPS}
)