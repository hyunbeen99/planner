cmake_minimum_required(VERSION 3.0.2)
project(planner)

add_compile_options(-std=c++11)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  rospy
  std_msgs
  sensor_msgs
  geometry_msgs
  ackermann_msgs
  pcl_conversions
  pcl_ros
)

# add_message_files(
#   FILES
#   Message1.msg
#   Message2.msg
# )

## Generate services in the 'srv' folder
# add_service_files(
#   FILES
#   Service1.srv
#   Service2.srv
# )

## Generate actions in the 'action' folder
# add_action_files(
#   FILES
#   Action1.action
#   Action2.action
# )

## Generate added messages and services with any dependencies listed here
generate_messages(
DEPENDENCIES sensor_msgs ackermann_msgs)
# generate_dynamic_reconfigure_options(
#   cfg/DynReconf1.cfg
#   cfg/DynReconf2.cfg
# )
catkin_package()
include_directories(
include
  ${catkin_INCLUDE_DIRS}
)
#add_library(${PROJECT_NAME}
#   src/${PROJECT_NAME}/planner.cpp
# )

add_executable(planner src/planner.cpp)
# add_dependencies(${PROJECT_NAME}_node ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
target_link_libraries(planner ${catkin_LIBRARIES})
