cmake_minimum_required(VERSION 2.8.3)
project(ethzasl_gridmap_2d)

find_package(catkin REQUIRED COMPONENTS roscpp nav_msgs)

# required in Indigo
find_package(cmake_modules REQUIRED)
find_package(Eigen REQUIRED)

catkin_package(
	INCLUDE_DIRS include
	LIBRARIES ${PROJECT_NAME}
	CATKIN_DEPENDS roscpp nav_msgs
	DEPENDS eigen3
)

set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)

include_directories(include ${Eigen_INCLUDE_DIRS})

add_library(ethzasl_gridmap_2d src/grid-map.cpp)


# Mark executables and/or libraries for installation
install(TARGETS ethzasl_gridmap_2d
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

# Mark cpp header files for installation
install(DIRECTORY include/${PROJECT_NAME}/
  DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
  FILES_MATCHING PATTERN "*.h"
  PATTERN ".svn" EXCLUDE
)
