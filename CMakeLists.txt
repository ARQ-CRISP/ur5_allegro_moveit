cmake_minimum_required(VERSION 2.8.3)
project(ur5_allegro_moveit)

## Compile as C++11, supported in ROS Kinetic and newer
add_compile_options(-std=c++11)

find_package(catkin REQUIRED
  COMPONENTS
    moveit_core
    moveit_visual_tools
    moveit_ros_planning
    moveit_ros_planning_interface
    geometry_msgs
)

# For YouCompleteMe
set( CMAKE_EXPORT_COMPILE_COMMANDS ON )

catkin_package(
  CATKIN_DEPENDS
    moveit_core
    moveit_visual_tools
    moveit_ros_planning
    moveit_ros_planning_interface
    geometry_msgs
)

include_directories(
  include
  ${catkin_INCLUDE_DIRS}
)


add_executable(merged_joint_states
  src/js_merger_node.cpp
)

target_link_libraries(merged_joint_states
  ${catkin_LIBRARIES}
)


install(DIRECTORY launch DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
  PATTERN "setup_assistant.launch" EXCLUDE)
install(DIRECTORY config DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})


include_directories( ${catkin_INCLUDE_DIRS} )
