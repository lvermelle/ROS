# Catkin_ws
This catkin_ws folder was create as the step "6- Create a ROS package" of the tutorials explains.

This workspace contains a package (catkin_ws/src/OdomPkg) wich contains a c++ script (catkin_ws/src/OdomPkg/src/Odom.cpp).

## What for?
This code was create to get datas of turtlebot as the speed of its wheels or the position determined by its gyrometer during an experiment. Theses datas are saved in a datafile.txt at the end of the script.

The work linked to this code is the work of the researcher Joao Baptista PINO NETO, INRIA Lille. He's working on prediction and deadrecogning.

## How?
Odom.cpp use 3 functions to move the robot (goforward, turn_right and turn_left); read somes informations of the robot with the functions : showImuCallback, showOdomCallback and showSensorsCallback. Finaly, it saves somes interresting selected datas with the stores functions.

This package and this code can be modified to get more informations about the state of the robot during an experiment.
The datafile.txt is useful to analyse the datas after the experiment.

To modify this code or to create a new one in the same package: please refer to the tutorial: 6- Create a ROS package.

To test the code Odom.cpp from OdomPkg on a robot, open a new terminal on the client, go to /catkin_ws/ folder and run:
	$ catkin_make
	$ rosrun OdomPkg getOdomAndSaveIt

(don't forget to bringup the robot on the server before:)

	$ roslaunch turtlebot_bringup minimal.launch

