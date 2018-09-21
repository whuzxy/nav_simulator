cmake_minimum_required(VERSION 2.8.3)
project(control_plugins)


find_package(catkin REQUIRED COMPONENTS
  gazebo_ros
  control_msgs
)

find_package(gazebo 7 REQUIRED)
find_package(ignition-msgs0 REQUIRED)
find_package(ignition-transport3 REQUIRED)
catkin_package(
 # INCLUDE_DIRS include
 # LIBRARIES gazebo_radar_plugin
 CATKIN_DEPENDS gazebo_plugins gazebo_ros
#  DEPENDS system_lib
)

include_directories(include ${catkin_INCLUDE_DIRS} ${GAZEBO_INCLUDE_DIRS} ${IGNITION-TRANSPORT_INCLUDE_DIRS})
#message("1111111111111111111111111111 ${IGNITION-TRANSPORT_INCLUDE_DIRS}")

add_library(ControlHybridPlugin_4w SHARED ControlHybridPlugin_4w.cc)
target_link_libraries(ControlHybridPlugin_4w ${GAZEBO_LIBRARIES} ${IGNITION-MSGS_LIBRARIES} ${IGNITION-TRANSPORT_LIBRARIES})

add_library(ControlHybridPlugin_2w SHARED ControlHybridPlugin_2w.cc)
target_link_libraries(ControlHybridPlugin_2w ${GAZEBO_LIBRARIES} ${IGNITION-MSGS_LIBRARIES} ${IGNITION-TRANSPORT_LIBRARIES})

#add_library(gazebo_ros_block_laser2 SHARED plugins/gazebo_ros_block_laser.cpp)
#target_link_libraries(gazebo_ros_block_laser2 ${GAZEBO_LIBRARIES} ${catkin_LIBRARIES} ${IGNITION-MSGS_LIBRARIES} ${PCL_LIBRARIES})

catkin_install_python(PROGRAMS nodes/joystick_translator
                       DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})
