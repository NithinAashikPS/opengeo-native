cmake_minimum_required(VERSION 3.28)
project(OpenGeoGLFW VERSION 1.0.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(glfw3 CONFIG REQUIRED)

set(
        SOURCES
        ${CMAKE_CURRENT_LIST_DIR}/src/OpenGeo/GLFWRendererBackend.cpp
)

set(
        HEADERS
        ${CMAKE_CURRENT_LIST_DIR}/include/OpenGeo/GLFWRendererBackend.h
)

add_library(${PROJECT_NAME} SHARED ${SOURCES} ${HEADERS})

target_include_directories(${PROJECT_NAME} PUBLIC
        $<BUILD_INTERFACE:${CMAKE_CURRENT_LIST_DIR}/include/>
        $<INSTALL_INTERFACE:include>
)

target_link_libraries(${PROJECT_NAME} PRIVATE glfw)
