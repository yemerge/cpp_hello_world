cmake_minimum_required(VERSION 3.11)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

set(CMAKE_VERBOSE_MAKEFILE ON)

project(
    UTILS
    LANGUAGES CXX
    VERSION 1.0.0
    DESCRIPTION ""
    HOMEPAGE_URL "https://github.com/yemerge/cpp_hello_world"
)

message(STATUS)
message(STATUS "Started all process in ${PROJECT_NAME} CMakeLists.txt.")
message(STATUS)

set(CPP_COMFILE_FLAGS_MSVC /W4 /WX /permissive-)
set(CPP_COMFILE_FLAGS_OTHERS -Wall -Wpedantic -Wextra -Werror)

if(NOT CPP_COMFILE_FLAGS)
  if(CMAKE_CXX_COMPILER_ID STREQUAL "MSVC")
    set(CPP_COMFILE_FLAGS ${CPP_COMFILE_FLAGS_MSVC})
  else()
    set(CPP_COMFILE_FLAGS ${CPP_COMFILE_FLAGS_OTHERS})
  endif()
endif()

# ! Set the path variables
# ! set(${PROJECT_NAME}_SOMETHING_PATH ${${PROJECT_NAME}_PATH}/something)
set(${PROJECT_NAME}_ROOT_PATH ${CMAKE_CURRENT_SOURCE_DIR})
set(${PROJECT_NAME}_SOURCE_PATH "${${PROJECT_NAME}_ROOT_PATH}/src")
set(${PROJECT_NAME}_INCLUDE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/include")
# set(${PROJECT_NAME}_INCLUDE_PATH "${${PROJECT_NAME}_ROOT_PATH}/include")
# set(${PROJECT_NAME}_PARENT_INCLUDE_PATH "${${PROJECT_NAME}_ROOT_PATH}/include")

# ! Message for the project information
message(STATUS "---------------Procject information---------------")
message(STATUS "PROJECT_NAME: ${PROJECT_NAME}")
message(STATUS "${PROJECT_NAME}_VERSION: ${PROJECT_VERSION}")
message(STATUS "${PROJECT_NAME}_DESCRIPTION: ${PROJECT_DESCRIPTION}")
message(STATUS "${PROJECT_NAME}_HOMEPAGE_URL: ${PROJECT_HOMEPAGE_URL}")
message(STATUS "")

# ! message(STATUS "${PROJECT_NAME}_SOMETHING_PATH: ${${PROJECT_NAME}_SOMETHING_PATH}")
message(STATUS "---------------Procject path information---------------")
message(STATUS "${PROJECT_NAME}_ROOT_PATH: ${${PROJECT_NAME}_ROOT_PATH}")
message(STATUS "${PROJECT_NAME}_INCLUDE_PATH: ${${PROJECT_NAME}_INCLUDE_PATH}")
message(STATUS "${PROJECT_NAME}_SOURCE_PATH: ${${PROJECT_NAME}_SOURCE_PATH}")
message(STATUS "${PROJECT_NAME}_PARENT_INCLUDE_PATH: ${${PROJECT_NAME}_PARENT_INCLUDE_PATH}")
message(STATUS "")

set(${PROJECT_NAME}_SOURCE_FILES
  src/utils.cpp
  # ! Add source files here
)
message(STATUS "${PROJECT_NAME}_aaa: ${PROJECT_NAME}_SOURCE_FILES")

# ! If you want to make a library, use the following code
add_library(${PROJECT_NAME} STATIC
  ${${PROJECT_NAME}_SOURCE_FILES}
)
message(STATUS "${PROJECT_NAME}_bbb: ${PROJECT_NAME} STATIC ${${PROJECT_NAME}_SOURCE_FILES}")

# ! If you want to add include directories and link libraries, use the following code
target_include_directories(${PROJECT_NAME} PUBLIC
  ${${PROJECT_NAME}_INCLUDE_PATH}

  # ! Add include path here
)
message(STATUS "${PROJECT_NAME}_ccc: ${PROJECT_NAME} PUBLIC ${${PROJECT_NAME}_INCLUDE_PATH}")

target_compile_options(${PROJECT_NAME} PRIVATE
  ${CPP_COMFILE_FLAGS}
)
message(STATUS "${PROJECT_NAME}_ddd: ${PROJECT_NAME} PRIVATE ${CPP_COMFILE_FLAGS}")

message(STATUS)
message(STATUS "Finished all process in ${PROJECT_NAME} CMakeLists.txt.")
message(STATUS)
