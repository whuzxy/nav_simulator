cmake_minimum_required(VERSION 2.8.3)
project(car_sim)


set (PRIUSCUP_MAJOR_VERSION 0)
set (PRIUSCUP_MINOR_VERSION 1)
set (PRIUSCUP_PATCH_VERSION 0)
set (PRIUSCUP_VERSION_FULL ${PRIUSCUP_MAJOR_VERSION}.${PRIUSCUP_MINOR_VERSION}.${PRIUSCUP_PATCH_VERSION})

find_package(catkin REQUIRED COMPONENTS
  gazebo_ros
  prius_msgs
  pcl_conversions
  pcl_ros
)

find_package(gazebo 7 REQUIRED)
find_package(ignition-msgs0 REQUIRED)
find_package(ignition-transport3 REQUIRED)
find_package(PCL REQUIRED)
catkin_package(
 # INCLUDE_DIRS include
 # LIBRARIES gazebo_radar_plugin
 CATKIN_DEPENDS gazebo_plugins gazebo_ros
#  DEPENDS system_lib
)

include_directories(include ${catkin_INCLUDE_DIRS} ${GAZEBO_INCLUDE_DIRS} ${PCL_INCLUDE_DIRS})

add_library(myPriusHybridPlugin_4w SHARED plugins/PriusHybridPlugin_4w.cc)
target_link_libraries(myPriusHybridPlugin_4w ${GAZEBO_LIBRARIES} ${IGNITION-MSGS_LIBRARIES} ${IGNITION-TRANSPORT_LIBRARIES})

add_library(myPriusHybridPlugin_2w SHARED plugins/PriusHybridPlugin_2w.cc)
target_link_libraries(myPriusHybridPlugin_2w ${GAZEBO_LIBRARIES} ${IGNITION-MSGS_LIBRARIES} ${IGNITION-TRANSPORT_LIBRARIES})

#add_library(gazebo_ros_block_laser2 SHARED plugins/gazebo_ros_block_laser.cpp)
#target_link_libraries(gazebo_ros_block_laser2 ${GAZEBO_LIBRARIES} ${catkin_LIBRARIES} ${IGNITION-MSGS_LIBRARIES} ${PCL_LIBRARIES})

catkin_install_python(PROGRAMS nodes/joystick_translator
                       DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})
