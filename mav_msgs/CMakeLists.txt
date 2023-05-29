cmake_minimum_required(VERSION 3.16.2)
project(mav_msgs)

find_package(ament_cmake REQUIRED)
find_package(std_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(trajectory_msgs REQUIRED)
find_package(nav_msgs REQUIRED)
find_package(rcl_interfaces REQUIRED)

include_directories(include)

rosidl_generate_interfaces(${PROJECT_NAME}
  
  msg/Actuators.msg
  msg/AttitudeThrust.msg
  msg/RateThrust.msg
  msg/RollPitchYawrateThrust.msg
  msg/TorqueThrust.msg
  msg/Status.msg
  msg/FilteredSensorData.msg
  msg/GpsWaypoint.msg
  
  DEPENDENCIES 
  std_msgs
  geometry_msgs
  nav_msgs
  rcl_interfaces
  builtin_interfaces 
)
ament_package()

install(
  DIRECTORY include/${PROJECT_NAME}/
  DESTINATION include/${PROJECT_NAME}/
  FILES_MATCHING PATTERN "*.h" 
)
