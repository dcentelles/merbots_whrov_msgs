cmake_minimum_required(VERSION 2.8.3)
project(merbots_whrov_msgs CXX C)

## Add support for C++11, supported in ROS Kinetic and newer
add_definitions(-std=c++11)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED COMPONENTS
    std_msgs
    std_srvs
    message_generation
    actionlib_msgs
)

add_action_files(
  DIRECTORY action
  FILES 
	MoveOrder.action 
	Order.action
)

## Declare ROS messages and services
add_message_files(DIRECTORY msg FILES
        hrov_settings.msg
        image_settings.msg
        protocol_settings.msg
        movement.msg
        position.msg
	state.msg
        )


generate_messages(
  DEPENDENCIES
  std_msgs
  actionlib_msgs
)

catkin_package(
  CATKIN_DEPENDS
      roscpp std_msgs
      message_runtime
      actionlib_msgs
)

###########
## Build ##
###########

include_directories(
  ${catkin_INCLUDE_DIRS}
)
