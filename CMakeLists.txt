cmake_minimum_required(VERSION 3.8)
project(rviz_3d_nav_goal_tool)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# Find dependencies
find_package(ament_cmake REQUIRED)
find_package(pluginlib REQUIRED)
find_package(rclcpp REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(tf2_ros REQUIRED)
find_package(tf2_geometry_msgs REQUIRED)
find_package(rviz_common REQUIRED)
find_package(rviz_default_plugins REQUIRED)
find_package(rviz_rendering REQUIRED)
find_package(Qt5 REQUIRED COMPONENTS Core Widgets)

set(CMAKE_AUTOMOC ON)
add_definitions(-DQT_NO_KEYWORDS)

# Define source file
set(${PROJECT_NAME}_SRCS
  src/goal_tool.cpp
  src/pose_tool.cpp
)

# Define header file
set(${PROJECT_NAME}_HDRS
  include/${PROJECT_NAME}/goal_tool.hpp
  include/${PROJECT_NAME}/pose_tool.hpp
)

# Qt's meta-object compiler for ROS2
qt5_wrap_cpp(${PROJECT_NAME}_MOCS ${${PROJECT_NAME}_HDRS})

# Add library to create plugin
add_library(${PROJECT_NAME} SHARED
  ${${PROJECT_NAME}_SRCS}
  ${${PROJECT_NAME}_MOCS}
)

target_link_libraries(${PROJECT_NAME}
  Qt5::Core
  Qt5::Widgets
)

target_include_directories(${PROJECT_NAME} PUBLIC
  include
)

ament_target_dependencies(${PROJECT_NAME}
  pluginlib
  rclcpp
  geometry_msgs
  tf2_ros
  tf2_geometry_msgs
  rviz_common
  rviz_default_plugins
  rviz_rendering
)

pluginlib_export_plugin_description_file(rviz_common rviz_plugin.xml)

install(TARGETS ${PROJECT_NAME}
  ARCHIVE DESTINATION lib
  LIBRARY DESTINATION lib
  RUNTIME DESTINATION bin
)

install(DIRECTORY include/
  DESTINATION include
)

install(FILES rviz_plugin.xml
  DESTINATION share/${PROJECT_NAME}
)

ament_package()