cmake_minimum_required(VERSION 2.8.3)
project(chris_turtlebot_bumper2pc)
find_package(catkin REQUIRED COMPONENTS roscpp nodelet pluginlib sensor_msgs kobuki_msgs)

catkin_package(
   INCLUDE_DIRS include
   LIBRARIES chris_turtlebot_bumper2pc_nodelet
   CATKIN_DEPENDS roscpp nodelet pluginlib sensor_msgs kobuki_msgs
)

include_directories(include ${catkin_INCLUDE_DIRS})

add_library(chris_turtlebot_bumper2pc_nodelet src/chris_turtlebot_bumper2pc.cpp)
add_dependencies(chris_turtlebot_bumper2pc_nodelet ${catkin_EXPORTED_TARGETS})
target_link_libraries(chris_turtlebot_bumper2pc_nodelet ${catkin_LIBRARIES})

install(TARGETS chris_turtlebot_bumper2pc_nodelet
        DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
)
install(DIRECTORY include/${PROJECT_NAME}/
        DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
)
install(DIRECTORY plugins
        DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)
install(DIRECTORY launch
        DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)
