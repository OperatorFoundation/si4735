cmake_minimum_required(VERSION 3.25)
project(si4735)
set(CMAKE_CXX_STANDARD 17)

set(LIB ${CMAKE_SOURCE_DIR}/libraries)
set(SI4735_DIR ${LIB}/SI4735)
set(IOTA_CPP_DIR ${LIB}/iota-cpp)
set(IOTA_ARDUINO_DIR ${LIB}/iota-arduino)
set(ION_CPP_DIR ${LIB}/ion-cpp)
set(ION_ARDUINO_DIR ${LIB}/ion-arduino)
set(TRANSMISSION_CPP_DIR ${LIB}/transmission-cpp)
set(SI4735_ARDUINO_DIR ${LIB}/si4735-arduino)

add_subdirectory("libraries/si4735-arduino")
