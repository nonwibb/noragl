cmake_minimum_required(VERSION 3.0.0)
project(noragl VERSION 0.1.0)

include(CTest)
enable_testing()

find_package(GLEW REQUIRED)
include_directories(${GLEW_INCLUDE_DIRS})
find_package(glfw3 REQUIRED)


set(ALL_LIBS
	glfw
	GLEW
    GL
)

file(GLOB common
    "common/*.hpp"
    "common/*.cpp"
)

file(GLOB shaders
  "${CMAKE_CURRENT_SOURCE_DIR}/shader/*"
)
file(COPY ${shaders} DESTINATION ${CMAKE_CURRENT_BINARY_DIR})

add_executable(noragl main.cpp ${common})
target_link_libraries(noragl ${ALL_LIBS})


set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)
