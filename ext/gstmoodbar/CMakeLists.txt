cmake_minimum_required(VERSION 2.8.11)

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wall")
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} --std=c++11 -U__STRICT_ANSI__ -Wall -Woverloaded-virtual -Wno-sign-compare -Wno-deprecated-declarations -Wno-unused-local-typedefs -fpermissive")

include_directories(${CMAKE_CURRENT_BINARY_DIR} ${CMAKE_CURRENT_SOURCE_DIR})

include_directories(${GLIB_INCLUDE_DIRS})
include_directories(${GOBJECT_INCLUDE_DIRS})
include_directories(${GSTREAMER_INCLUDE_DIRS})
include_directories(${FFTW3_INCLUDE_DIR})

set(SOURCES gstfastspectrum.cpp gstmoodbarplugin.cpp)

add_library(gstmoodbar STATIC ${SOURCES})

target_link_libraries(gstmoodbar
  ${GOBJECT_LIBRARIES}
  ${GLIB_LIBRARIES}
  ${GSTREAMER_LIBRARIES}
  ${GSTREAMER_AUDIO_LIBRARIES}
  ${GSTREAMER_BASE_LIBRARIES}
  ${FFTW3_FFTW_LIBRARY}
)

target_link_libraries(gstmoodbar Qt5::Core)
