cmake_minimum_required(VERSION 2.8.3)
project(blort_ros_msgs)

find_package(catkin REQUIRED COMPONENTS geometry_msgs message_generation std_msgs sensor_msgs)

add_message_files(
  DIRECTORY msg
  FILES
  NameTypeValue.msg
  ObjectPoseList.msg
  ObjectPose.msg
  TrackerConfidences.msg
  TrackerResults.msg
)

add_service_files(
  DIRECTORY srv
  FILES
  EstimatePose.srv
  RecoveryCall.srv
  SetCameraInfo.srv
  TrackerCommand.srv
)

generate_messages(
 DEPENDENCIES geometry_msgs sensor_msgs
)

include_directories(include ${catkin_INCLUDE_DIRS})

catkin_package()

install(DIRECTORY include/${PROJECT_NAME}/
  DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
  FILES_MATCHING PATTERN "*.h")
