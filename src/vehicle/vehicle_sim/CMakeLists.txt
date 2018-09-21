cmake_minimum_required(VERSION 2.8.3)
project(vehicle_sim)

find_package(catkin REQUIRED COMPONENTS
  geometry_msgs
  roscpp
  rviz
  tf
  urdf
  xacro
)



catkin_package(

)


include_directories(
  ${catkin_INCLUDE_DIRS}
)