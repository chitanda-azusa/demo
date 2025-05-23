cmake_minimum_required(VERSION 3.9)
project(demo LANGUAGES C CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_VISIBILITY_PRESET hidden)
set(CMAKE_VISIBILITY_INLINES_HIDDEN ON)

include_directories(${CMAKE_SOURCE_DIR})

add_executable(demo "")
target_sources(demo
  PRIVATE
    "main.cc"
    "controller/HelloController.cc"
)

include(cmake/CPM.cmake)

CPMAddPackage(
    NAME drogon
    VERSION 1.9.10
    GITHUB_REPOSITORY drogonframework/drogon
    GIT_TAG v1.9.10
)

target_link_libraries(${PROJECT_NAME} PRIVATE drogon)
