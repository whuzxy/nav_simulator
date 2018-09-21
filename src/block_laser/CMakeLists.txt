cmake_minimum_required(VERSION 2.8.3)
project(block_laser)


find_package(catkin REQUIRED COMPONENTS
  gazebo_ros
  pcl_conversions
  pcl_ros
)

find_package(gazebo 7 REQUIRED)
find_package(ignition-msgs0 REQUIRED)
find_package(ignition-transport3 REQUIRED)
find_package(PCL REQUIRED)
catkin_package(
  INCLUDE_DIRS include
  LIBRARIES block_laser_16
  CATKIN_DEPENDS gazebo_plugins gazebo_ros
#  DEPENDS system_lib
)

include_directories(include ${catkin_INCLUDE_DIRS} ${GAZEBO_INCLUDE_DIRS} ${PCL_INCLUDE_DIRS})

link_directories(${GAZEBO_LIBRARY_DIRS})
add_library(block_laser_16 SHARED src/block_laser_16.cpp)
add_dependencies(block_laser_16 ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
target_link_libraries(block_laser_16 RayPlugin ${GAZEBO_LIBRARIES} ${catkin_LIBRARIES} ${IGNITION-MSGS_LIBRARIES} ${PCL_LIBRARIES})

install(TARGETS block_laser_16
    ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
    LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
)


install(DIRECTORY include/${PROJECT_NAME}/
  DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
  PATTERN ".svn" EXCLUDE
)
