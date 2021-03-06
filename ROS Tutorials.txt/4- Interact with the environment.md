# 4- Interact with the environment
Though ROS can work in unknown environments, it helps to start with a map of the environment that we’re working in.

In this tutorial we’ll drive TurtleBot once around our office using teleoperation to create a map.
This will give us a map we can reference in other scripts, giving TurtleBot completely autonomous navigation.

## Prerequisites:
- Client and Server installed, configured and working.

## Commands:

#### 1- Create the map
On server: Bringup the robot
Prepare the mapping: 

	$ roslaunch turtlebot_navigation gmapping_demo.launch

On client: Launch the view in 2D of the robot

	$ roslaunch turtlebot_rviz_launchers view_navigation.launch
Launch the keyboard teleoperation to move the robot to discover and create his map: 

	$ roslaunch turtlebot_teleop keyboard_teleop.launch
You must see the robot moving on rviz and implement the map with obstacles or free space.

Once your map is done, open a new terminal on server, and save the map:
	$ rosrun map_server map_saver -f /tmp/my_map
You create a my_map.pgm and my_map.yaml files.

Warning, /tmp/ directory is automatically cleaned (deleted) on every boot. You may want to copy in a other directory if you need want to keep the maps.

#### 2- Use this map in autonomous driving
Now let’s dive into the power of ROS. With ROS we have the ability to move TurtleBot (or any other robot) from one place to another while avoiding both static and dynamic obstacles all with a few lines of code.

Stop everything from the previous tutorials on both server and client. 
On server run:

	$ roslaunch turtlebot_bringup minimal.launch 
to bring the robot and: 

	$ roslaunch turtlebot_navigation amcl_demo.launch map_file:=/tmp/my_map.yaml
to launch your map: you must see "odom received!"

On client, run:

	$ roslaunch turtlebot_rviz_launchers view_navigation.launch --screen

RViz should open your map but the robot may not be at the good place. Select “2D Pose Estimate” arrow to estimate his initial position and orientation.

Then, select "2D Nav Goal” and click the location where you want TurtleBot go.

TurtleBot should now be driving around autonomously based on your goals avoiding obstacles.

#### 3- Return to the base Automaticly
Place TurtleBot anywhere in line of sight up to 3 meters from the docking station.

Bingup the robot on server. In two differents terminals on client: 

	$ roslaunch kobuki_auto_docking minimal.launch --screen
	$ roslaunch kobuki_auto_docking activate.launch --screen
	
