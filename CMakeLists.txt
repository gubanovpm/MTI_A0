cmake_minimum_required(VERSION 3.10.0)
project(MTI_A0 VERSION 1.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)
set(PROJECT_ROOT_DIR ${CMAKE_SOURCE_DIR})
set(CMAKE_MODULE_PATH ${PROJECT_ROOT_DIR}/CMake/Modules)
message(STATUS ${CMAKE_MODULE_PATH})

find_package(GMP REQUIRED)

INCLUDE_DIRECTORIES(
  ${GMP_INCLUDES}
)

if(UNIX AND NOT APPLE)
  set(OS_TYPE "LINUX")
else()
  if (MSVC OR MSYS OR MINGW)
    set(OS_TYPE "WINDOWS")
  else()
    set(OS_TYPE "UNKNOWN")
  endif()
endif ()

add_subdirectory(sources)
add_subdirectory(Network)
add_subdirectory(Crypto)

