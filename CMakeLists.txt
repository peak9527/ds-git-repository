cmake_minimum_required(VERSION 2.8 FATAL_ERROR)
project(vlpGrabber)
ADD_DEFINITIONS(-std=c++11)

find_package(PCL 1.7 REQUIRED)

include_directories (/usr/local/include)
link_directories (/usr/local/lib)
include_directories(${PCL_INCLUDE_DIRS})
link_directories(${PCL_LIBRARY_DIRS})
add_definitions(${PCL_DEFINITIONS})

find_package(Boost COMPONENTS thread system REQUIRED)
set( BOOST_THREAD_LIBRARY "-lboost_thread")
set( Boost_SYSTEM_LIBRARY "-lboost_system")
set( LPTHREAD "-lpthread")
set( ZMQ_LIBRARIES "-lzmq")
set( JSON_LIBRARIES "-ljsoncpp")

set(SRC_LIST vlpGrabber.cpp)
add_executable(vlpGrabber ${SRC_LIST})
target_link_libraries (vlpGrabber ${PCL_LIBRARIES} ${Boost_SYSTEM_LIBRARY} ${Boost_THREAD_LIBRARY} ${ZMQ_LIBRARIES} ${JSON_LIBRARIES} ${LPTHREAD})


