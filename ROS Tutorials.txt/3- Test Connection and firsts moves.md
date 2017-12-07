# 3- Test Connection and firsts moves

Test the connection between client and server and run your firsts scripts on turtlebot.

On this part, somes commands must be done on the server, others on the client: be careful.
( Laptop = server / Remote PC = client )

## Prerequisites:
- Client and Server installed and configured

## Commands:

####1- Bringup the robot if you didn't: 
Verify that the laptop is connected to the robot via usb; then on the server:

	$ roslaunch turtlebot_bringup minimal.launch
You must hear the robot bringing up.
Let this terminal running.

####2- Verify the connection:
On client:

	$ rostopic list
If you don't see list of topics, check the value of ROS_MASTER_URI in the bashrc file of the client.
If you see "ERROR: Unable to communicate with master!", the robot isn't bring up.

		$ rostopic echo /diagnostics
	If you don't see list of characteristics, check the value of ROS_HOSTNAME in the bashrc file of the server.


####3- Send message from Client to Server:
On client:	

	$ rostopic pub -r10 /hello std_msgs/String "hello"
On server:

	$ rostopic echo /hello
If you recieve hello messages, everything is well configured.


####4- Move the robot from client with keyboard:
On server: Bringup the robot 
On client, run this: 

	$ roslaunch turtlebot_teleop keyboard_teleop.launch
Then use keyboard to move the robot.

####5- Test the Kinect
Bringup the robot on server

Open a new terminal on server and run this to launch the camera:	

	$ roslaunch openni_launch openni.launch
If you see "[INFO][#]: No devices connected.... waiting for devices to be connected", verify the installation of the Kinect driver in part 1- Install ROS Server.
If you have more problems, refer to this website: http://learn.turtlebot.com/2015/02/01/8/

On client, open a new termianl and run this to view the image data:

	$ rosrun image_view image_view image:=/camera/rgb/image_color
or 		
	$ rosrun image_view image_view image:=/camera/depth/image


	
