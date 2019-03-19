cmake_minimum_required(VERSION 3.10)
project(FMI4cppTest)
set(CMAKE_CXX_STANDARD 17)

find_package(FMI4cpp CONFIG REQUIRED)

add_executable(example example.cpp)
target_link_libraries(example FMI4cpp::FMI4cpp)

file(COPY ControlledTemperature.fmu DESTINATION ${CMAKE_CURRENT_BINARY_DIR})

enable_testing()
add_test(NAME example
      WORKING_DIRECTORY ${CMAKE_BINARY_DIR}/bin
      COMMAND example)
