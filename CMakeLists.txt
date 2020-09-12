cmake_minimum_required(VERSION 3.0.2)
project(dynamic_tutorials)

find_package(catkin REQUIRED COMPONENTS
  dynamic_reconfigure
  roscpp
  rospy
)


# dynamic_reconfigure
generate_dynamic_reconfigure_options(
  cfg/Tutorials.cfg
)

catkin_package(
  CATKIN_DEPENDS
  dynamic_reconfigure
  roscpp
  rospy
)

include_directories(
  include
  ${catkin_INCLUDE_DIRS}
)

add_executable(dynamic_tutorials
  src/server.cpp
)
target_link_libraries(dynamic_tutorials
  ${catkin_LIBRARIES}
)

add_dependencies(dynamic_tutorials ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
#add_dependencies(dynamic_tutorials dynamic_tutorials_gencfg)
