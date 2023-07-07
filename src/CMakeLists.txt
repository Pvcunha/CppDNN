cmake_minimum_required(VERSION 2.8)

project(EigenDNN)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++0x")

find_package(Eigen3 3.3 REQUIRED NO_MODULE)

set(CMAKE_BUILD_TYPE Release)

# Add source files for the library
set(SRC_FILES
    dummy.cpp
    # Add more source files as needed
)

# Create the shared library target
add_library(eigendnn SHARED ${SRC_FILES})

# Include directories for the library target
target_include_directories(eigendnn PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}
)

# Link the library with Eigen3
target_link_libraries(eigendnn Eigen3::Eigen)

# Install the shared library
install(TARGETS eigendnn
    LIBRARY DESTINATION /usr/local/lib
)

# Install the header files
install(FILES ${HEADERS}
    DESTINATION /usr/local/include/CppDNN
)
