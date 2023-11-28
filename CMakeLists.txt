cmake_minimum_required(VERSION 2.6)

project(VoxelGame)

file(GLOB_RECURSE HEADERS ${CMAKE_CURRENT_SOURCE_DIR}/src/*.hpp)
file(GLOB_RECURSE SOURCES ${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp)

set_property(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR} PROPERTY VS_STARTUP_PROJECT ${PROJECT_NAME})

find_package(OpenGL REQUIRED)
include_directories(${OPENGL_INCLUDE_DIRS})

set(GLFW_BUILD_DOCS OFF CACHE BOOL "GLFW lib only")
set(GLFW_INSTALL OFF CACHE BOOL  "GLFW lib only")

add_subdirectory(libs/glfw)
add_subdirectory(libs/glew)
     
add_executable(${PROJECT_NAME} ${HEADERS} ${SOURCES})

#target_include_directories(${PROJECT_NAME} PUBLIC libs/glew/include)

target_link_libraries(${PROJECT_NAME} ${OPENGL_LIBRARIES} glfw libglew_static)