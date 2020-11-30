cmake_minimum_required(VERSION 2.8.3)
project(uins)

find_package(catkin REQUIRED COMPONENTS 
             roscpp 
             roslint 
             serial 
             sensor_msgs
             )

catkin_package(
  INCLUDE_DIRS include
  CATKIN_DEPENDS message_runtime
  )

include_directories(include
  ${catkin_INCLUDE_DIRS}
)

add_executable(uins_parse_node src/main.cpp src/comms.cpp src/uins_parser.cpp)

target_link_libraries(uins_parse_node ${catkin_LIBRARIES} )



install(TARGETS uins_parse_node
    RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
