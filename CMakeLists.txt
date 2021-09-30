cmake_minimum_required (VERSION 3.0)
project (LeanOpenGL)

set(CMAKE_CXX_STANDARD 11)
#glfw
link_directories(${PROJECT_SOURCE_DIR}/lib)
include_directories(${PROJECT_SOURCE_DIR}/third_party/glfw-3.3.4/include)
link_libraries(glfw3)

#glad
include_directories(${PROJECT_SOURCE_DIR}/third_party/glad/include)
file(GLOB glad_src ${PROJECT_SOURCE_DIR}/third_party/glad/src/*.c)
add_library(glad ${glad_src})

#project src
include_directories(${PROJECT_SOURCE_DIR}/src)
file(GLOB src ${PROJECT_SOURCE_DIR}/src/*.cpp)
add_executable(LeanOpenGL src/main.cpp)
target_link_libraries(LeanOpenGL glad glfw3)
target_link_libraries(LeanOpenGL "-framework OpenGL -framework Cocoa -framework IOKit -framework CoreVideo")