cmake_minimum_required(VERSION 3.0 FATAL_ERROR)
project(QtAwesome VERSION 4.7)
set(QTAWESOME_SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR})

#Configure the project
set(CMAKE_DISABLE_IN_SOURCE_BUILD ON)

if(NOT CMAKE_CXX_STANDARD)
    set(CMAKE_CXX_STANDARD 11)
    set(CMAKE_CXX_STANDARD_REQUIRED ON)
endif()

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

if(CMAKE_VERSION VERSION_LESS "3.7.0")
    set(CMAKE_INCLUDE_CURRENT_DIR ON)
endif()

if(MSVC)
    set(CMAKE_WINDOWS_EXPORT_ALL_SYMBOLS TRUE)
endif()

option(QTAWESOME_BUILD_SAMPLE "Build sample" OFF)

#install var
set(include_dest "include/QtAwesome-${QMidi_VERSION}")
set(lib_dest "lib/QtAwesome-${QtAwesome_VERSION}")

# add subdirs
add_subdirectory(QtAwesome)
if(${QTAWESOME_BUILD_SAMPLE})
    add_subdirectory(QtAwesomeSample)
endif()

# install
install(FILES QtAwesome-config.cmake DESTINATION ${lib_dest})
install(EXPORT QtAwesome DESTINATION ${lib_dest})
