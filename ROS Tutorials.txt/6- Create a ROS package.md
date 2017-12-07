# 6 Create a ROS package

This tutorial will help you to create a ROS package.
A package contains algorithms in python or c++ to apply on the robot.

The difference between a package and a simple script (like goforward.py in tutorial 5) is that the code included in the package need more librairies and is more complex. 
You will create a package when you need a code which needs to access lot of ros librairies.

The catkin_ws folder is a workspace containing one package. The utility of this package is described in the catkin_ws/README.txt file. 

## Prerequisites:
- Client and Server installed, configured and working.

## Commands:
This part is to do on the client.

#### 1/ Create a new Catkin workspace (maybe you already have one installed on the client)

	$ source /opt/ros/indigo/setup.bash
	$ mkdir -p ~/catkin_ws/src
	$ cd ~/catkin_ws
	$ catkin_make
	$ source devel/setup.bash


#### 2/ Create a new package

	$ cd ~/catkin_ws/src
	$ catkin_create_package <package_name> std_msgs rospy roscpp
	$ cd ~/catkin_ws
	$ catkin_make
	$ . ~/catkin_ws/devel/setup.bash


#### 3/ Insert your code in the package

	$ cp <your_code.cpp/py> ~/catkin_ws/src/<package_name>/src/


#### 4/ Modify the package.xml and CmakeLists.txt files to compile correctly

	$ nano ~/catkin_ws/src/<package_name>/package.xml

Uncomment the following lines

	<buildtool_depend>catkin</buildtool_depend>
	<build_depend>roscpp</build_depend>
	<build_depend>rospy</build_depend>
	<build_depend>std_msgs</build_depend>
	<exec_depend>roscpp</exec_depend>
	<exec_depend>rospy</exec_depend>
	<exec_depend>std_msgs</exec_depend>

	$ nano ~/catkin_ws/src/<package_name>/CMakeLists.txt

Uncomment and complete the following lines

	find_package(catkin REQUIRED COMPONENTS
	rospy
	roscpp
	std_msg
	...
	add_executable(<executable_name> src/<your_code.cpp/py>)
	target_link_library(<executable name> ${catkin_LIBRARIES}

#### 5/ Build and run Package

	$ cd ~/catkin_ws
	$ catkin_make

Modify your code <your_code.cpp/py> if there is errors
If there's no error: 

	$ rosrun <package name> <executable name>


If you need an example of a operationnal code: see the /catkin_ws/README.md file.
