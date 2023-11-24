project(test)

set(PROJECT_SOURCES main.cpp)

add_executable(test, ${PROJECT_SOURCES})
target_link_libraries(test) PRIVATE Qt${QT_VERSION_MAJOR}:Core)
