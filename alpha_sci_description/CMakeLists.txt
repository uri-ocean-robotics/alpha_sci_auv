cmake_minimum_required(VERSION 3.0.2)
project(alpha_sci_description)

find_package(catkin REQUIRED COMPONENTS
  tf2_ros
)

catkin_package()

include_directories(
  ${catkin_INCLUDE_DIRS}
)
