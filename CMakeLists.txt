cmake_minimum_required(VERSION 3.28)
project(OpenGeo VERSION 1.0.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(GDAL CONFIG REQUIRED)

include(${CMAKE_SOURCE_DIR}/include/include.cmake)
include(${CMAKE_SOURCE_DIR}/src/src.cmake)

add_library(${PROJECT_NAME} SHARED ${OPEN_GEO_SOURCES} ${OPEN_GEO_HEADERS} ${OPEN_GEO_HEADERS_P})

target_include_directories(${PROJECT_NAME} PUBLIC
        $<BUILD_INTERFACE:${CMAKE_CURRENT_LIST_DIR}/include/public/>
        $<INSTALL_INTERFACE:include>
)
target_include_directories(${PROJECT_NAME} PRIVATE ${CMAKE_CURRENT_LIST_DIR}/include/private)

target_link_libraries(${PROJECT_NAME} PRIVATE GDAL::GDAL)

include(${CMAKE_SOURCE_DIR}/example/example.cmake)
include(${CMAKE_SOURCE_DIR}/platform/platform.cmake)