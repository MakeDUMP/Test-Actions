# -----------------------------------------------------------------------------
# Project
# -----------------------------------------------------------------------------
cmake_minimum_required(VERSION 3.15..3.20)
project(app)

set(PROJECT_COMPILE_FEATURES cxx_std_17)
# set(PROJECT_COMPILE_OPTIONS ${PROJECT_COMPILE_OPTIONS} -Wall)
set(PROJECT_COMPILE_DEFINES)
set(PROJECT_LINK_LIBRARIES)

set(PROJECT_INCLUDE_DIRS ${PROJECT_SOURCE_DIR}/src)
set(PROJECT_INCLUDES)
set(PROJECT_SOURCES
    ${PROJECT_SOURCE_DIR}/src/main.cpp
)

# -----------------------------------------------------------------------------
# Executable Application
# -----------------------------------------------------------------------------
add_executable(${PROJECT_NAME})
target_sources(${PROJECT_NAME} PUBLIC ${PROJECT_SOURCES})
# set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR})

target_include_directories(${PROJECT_NAME} PUBLIC ${PROJECT_INCLUDE_DIRS})
target_compile_features(${PROJECT_NAME} PUBLIC ${PROJECT_COMPILE_FEATURES})
target_compile_definitions(${PROJECT_NAME} PUBLIC ${PROJECT_COMPILE_DEFINES})
target_compile_options(${PROJECT_NAME} PUBLIC ${PROJECT_COMPILE_OPTIONS})
target_link_libraries(${PROJECT_NAME} ${PROJECT_LINK_LIBRARIES})

set_property(TARGET ${PROJECT_NAME} PROPERTY MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
  
# if(UNIX)
#     set(CMAKE_SKIP_RPATH on) # отключим установку путей поиска Shared Library's
#     target_link_options(${PROJECT_NAME} PUBLIC "$<$<CONFIG:Release>:-s>" "-rpath .") # выставим путь поиска '.'
# endif()
