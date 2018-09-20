cmake_minimum_required(VERSION 2.8.3)
project(diff_robot)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
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

