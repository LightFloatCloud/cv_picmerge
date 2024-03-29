cmake_minimum_required(VERSION 3.10)

#set( CMAKE_BUILD_TYPE "Release")

project(CV_picmerge)

if(CMAKE_HOST_WIN32)
    message(STATUS "System is WIN32, path of opencv need to set manually.")
    # set(OpenCV_DIR "E:/Lib/opencv3/build/x64/vc14/lib")
    # set(OpenCV_DIR "E:/Lib/opencv3/build/x64/vc15/lib")
    # set(OpenCV_DIR "E:/Lib/opencv4/opencv/build/x64/vc16/lib")
    ## set(OpenCV_DIR "E:/Lib/opencv4/opencv/build/x64/mingw")
    set(OpenCV_DIR "D:/Lib/opencv/OpenCV4.7_MinGW_build_with_contrib-master")
endif()

set( CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g -O2 -Wall -fexec-charset=GBK")
set( CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11" )
#set(OpenCV_STATIC ON)

if(CMAKE_HOST_WIN32)
    find_package(OpenCV 4 REQUIRED)
else()
    find_package(OpenCV 3 REQUIRED)
endif()

message(STATUS "OpenCV library status:")
message(STATUS "  version: ${OpenCV_VERSION}")
message(STATUS "  libraries: ${OpenCV_LIBS}")
message(STATUS "  libraries path: ${}")
message(STATUS "  include path: ${OpenCV_INCLUDE_DIRS}")


include_directories( ${OpenCV_INCLUDE_DIRS} )

set(EXECUTABLE_OUTPUT_PATH ${CMAKE_SOURCE_DIR}/bin)
add_executable(${PROJECT_NAME} src/main.cpp)
target_link_libraries( ${PROJECT_NAME} ${OpenCV_LIBS} )

