cmake_minimum_required(VERSION 3.15)

project(
  qtc-cmake-error
  VERSION 1.1
  LANGUAGES CXX)

# Project initialization
# ##############################################################################
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

list(APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake/)
include(InstallDependency)
include(CheckSubmodule)

# Qt
# ##############################################################################
find_package(Qt6 REQUIRED COMPONENTS Core)

add_subdirectory(3rdparty)

set(PROJECT_SOURCES src/main.cpp)

add_executable(test_app ${PROJECT_SOURCES})
target_link_libraries(test_app Qt6::Core)
install(TARGETS test_app)

add_custom_target(
  test_app_run ALL
  COMMAND test_app
  COMMENT "Test run of test_app"
  SOURCES ${PROJECT_SOURCES}
)
