cmake_minimum_required(VERSION 3.15)

project(
  qtc-cmake-error
  VERSION 1.1
  LANGUAGES CXX)

# Project initialization
# ##############################################################################
set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_INCLUDE_CURRENT_DIR ON)

list(APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake/)
include(InstallDependency)
include(CheckSubmodule)

# Qt
# ##############################################################################
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

find_package(
  Qt6
  COMPONENTS Widgets
  REQUIRED)

# 3rdparty
# ##############################################################################
add_subdirectory(3rdparty)

# Post-initialization
# ##############################################################################
# Need to be done *after* compiling 3rd parties
if(MSVC)
  add_compile_options(/W3 /WX)
else()
  add_compile_options(-Wall -Wextra -Werror -Wno-error=comment)
endif()
# Set tests here, as it was disabled before
enable_testing()

add_subdirectory(src)

add_custom_target(
  test_run ALL
  COMMAND test
  COMMENT "do something")
