################################################################################
# Set minimum required version of cmake, project name and compile options
################################################################################
cmake_Minimum_required(VERSION 2.8.3)
project(feetech_lib)

################################################################################
# Find catkin packages and libraries for catkin and system dependencies
################################################################################
find_package(catkin REQUIRED COMPONENTS
  roscpp
  rospy
  std_msgs
)

################################################################################
# Declare catkin specific configuration to be passed to dependent projects
################################################################################
catkin_package(
 INCLUDE_DIRS include
 LIBRARIES feetech_lib
 CATKIN_DEPENDS roscpp rospy std_msgs
)

################################################################################
# Build
################################################################################
include_directories(
  ${PROJECT_SOURCE_DIR}/include/feetech_lib
  ${catkin_INCLUDE_DIRS}
)

file(GLOB hdrs include/feetech_lib/*.h)
file(GLOB srs src/*.cpp)

add_library(feetech_lib ${hdrs} ${srs})
add_dependencies(feetech_lib ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})

target_link_libraries(feetech_lib
  ${catkin_LIBRARIES}
)
