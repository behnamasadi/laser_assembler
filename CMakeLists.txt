cmake_minimum_required(VERSION 2.8.3)
project(laser_assembler)
set(CMAKE_BUILD_TYPE Debug)


######################################################################find_package##################################################################
find_package(cmake_modules REQUIRED)
find_package(catkin REQUIRED COMPONENTS laser_geometry roscpp tf)
find_package(Eigen REQUIRED)
find_package(PCL 1.7 REQUIRED COMPONENTS common apps)


#this will put everything in the devel folder
catkin_package()
######################################################################include_directories##################################################################


#include_directories(include ${catkin_INCLUDE_DIRS} ${GAZEBO_INCLUDE_DIRS} ${SDFormat_INCLUDE_DIRS})
#include_directories(${PCL_INCLUDE_DIRS})
include_directories(${PCL_INCLUDE_DIRS} ${EIGEN_INCLUDE_DIRS} ${catkin_INCLUDE_DIRS} ${PROJECT_SOURCE_DIR}/include)

######################################################################add_definitions#####################################################################
add_definitions(${PCL_DEFINITIONS})




MESSAGE("######################################################################PCL#####################################################################")
MESSAGE("PCL_FOUND:" ${PCL_FOUND})
MESSAGE("PCL_INCLUDE_DIRS:" ${PCL_LIBRARY_DIRS})
MESSAGE("PCL_LIBRARIES:" ${PCL_LIBRARIES})
MESSAGE("PCL_LIBRARY_DIRS:" ${PCL_LIBRARY_DIRS})
MESSAGE("PCL_VERSION:" ${PCL_VERSION})
MESSAGE("PCL_COMPONENTS:" ${PCL_COMPONENTS})
MESSAGE("PCL_DEFINITIONS:" ${PCL_DEFINITIONS})


MESSAGE("######################################################################catkin#####################################################################")
MESSAGE("catkin_LIBRARIES: " ${catkin_LIBRARIES})



add_executable(laser_scan_to_pointcloud src/laser_scan_to_pointcloud.cpp )
target_link_libraries(laser_scan_to_pointcloud  ${catkin_LIBRARIES}  ${PCL_LIBRARIES}  )


add_executable(laser_assembler_service_caller src/laser_assembler_service_caller.cpp )
target_link_libraries(laser_assembler_service_caller  ${catkin_LIBRARIES}  ${PCL_LIBRARIES}  )
