cmake_minimum_required(VERSION 3.8)
project(micro_pubsub)

list(APPEND CMAKE_PREFIX_PATH "/opt/ros/humble")

find_package(ament_cmake REQUIRED)
find_package(rcl REQUIRED)
find_package(rclc REQUIRED)
find_package(std_msgs REQUIRED)
find_package(rmw_microxrcedds REQUIRED)

message(STATUS "rclc_DIR: ${rclc_DIR}")

add_executable(publisher src/micro_publisher.c)
ament_target_dependencies(publisher
  rcl
  rclc
  std_msgs
  rmw_microxrcedds)

add_executable(subscriber src/micro_subscriber.c)
ament_target_dependencies(subscriber
  rcl
  rclc
  std_msgs
  rmw_microxrcedds)

install(TARGETS
        publisher
        subscriber
        DESTINATION lib/${PROJECT_NAME})

ament_package()
