cmake_minimum_required(VERSION 3.0)

execute_process(COMMAND protoc -I=./ --cpp_out=./ ./demo.proto
WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR})    

include_directories(../src/)
include_directories(../proto/)

set(DEMO_SRC
    main.cpp
    demo.pb.h
    demo.pb.cc        
)

add_executable(tester ${DEMO_SRC})
target_link_libraries(tester ${PROTOBUF_LIBRARY})
target_link_libraries(tester lib_proto_message)