project(flappy)
cmake_minimum_required(VERSION 3.1.2)

# pull in the generated conan cmake
include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup(TARGETS)

add_executable(${PROJECT_NAME} 
  main.cpp
  GameOver.cpp
  GameOver.h
  Pipes.cpp
  Pipes.h
  Points.cpp
  Points.h
)
target_link_libraries(${PROJECT_NAME}
  ${CONAN_TARGETS})

add_custom_command(TARGET ${PROJECT_NAME} POST_BUILD
   COMMAND ${CMAKE_COMMAND} -E copy_directory
  "${PROJECT_SOURCE_DIR}/images/"
  "${CMAKE_BINARY_DIR}/bin/images"
)

add_custom_command(TARGET ${PROJECT_NAME} POST_BUILD
   COMMAND ${CMAKE_COMMAND} -E copy_directory
  "${PROJECT_SOURCE_DIR}/audio/"
  "${CMAKE_BINARY_DIR}/bin/audio"
)
