#
# Test main for testing.
#
cmake_minimum_required( VERSION 2.8.11 FATAL_ERROR )
project(mavlink_commproto_send)

# Build the library with this application, otherwise we would need to make the 
# library for them...
#add_subdirectory(CommProtocol/)

include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../CommProtocol/CommProto/include/)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/../CommProto-MessageStandards2017/packets/cpp/)


# Add the exe
add_executable(mavlink_commproto_send
 ${CMAKE_CURRENT_SOURCE_DIR}/test_send_command.cpp)

target_link_libraries(mavlink_commproto_send CommProtocol-Static)
target_link_libraries(mavlink_commproto_send cryptopp-static)
target_link_libraries(mavlink_commproto_send libxbee3)

 #Mario? this is probably not right
if (CMAKE_VERSION VERSION_GREATER 2.8.11)  
  set(CMAKE_CXX_FLAGS ${CMAKE_CXX_FLAGS} " -pthread")
else()
  set(CMAKE_CXX_FLAGS ${CMAKE_CXX_FLAGS} " -std=c++11 -pthread")
endif()

# Property to set for C++ 11 standard.
set_property(TARGET mavlink_commproto_send PROPERTY CXX_STANDARD 11)


