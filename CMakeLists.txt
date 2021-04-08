cmake_minimum_required(VERSION 3.17)
project(OpenGL_demo)

set(CMAKE_CXX_STANDARD 14)
# config glfw
option(GLFW_BUILD_DOCS OFF)
option(GLFW_BUILD_EXAMPLES OFF)
option(GLFW_BUILD_TESTS OFF)
add_subdirectory(3rd_party/glfw)

include_directories(3rd_party/glfw/include)

LIST(APPEND LIBS glfw ${GLFW_LIBRARIES})





#config glad
set(GLAD_SRC 3rd_party/glad-c/src/glad.c)
if(NOT WIN32)
    LIST(APPEND LIBS dl)
endif()
include_directories(3rd_party/glad-c/include)

#config glm
include_directories(3rd_party/glm)

set(SOURCE_FILES main.cpp ${GLAD_SRC})
add_executable(OpenGL_demo ${SOURCE_FILES})
target_link_libraries(OpenGL_demo ${LIBS})
#add_executable(OpenGL_demo main.cpp)