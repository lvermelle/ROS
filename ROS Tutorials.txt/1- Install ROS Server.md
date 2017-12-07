# 1- Install ROS Server
These are the steps to install a complete ROS Server
A ROS Server is the OS working on the laptop connected to the robot
This tutorial is a shortcut of the tutorial available on http://wiki.ros.org/indigo/Installation/Ubuntu.

(Laptop = server)

## Prerequisites:
-Ubuntu 14.4 installed on the laptop to install the indigo version of ROS.

-Internet connection.

You will only work on terminal so you can access to the laptop on ssh if you prefer. Both computers must be on the same network.

## Commands:
Install openssh-server on the laptop

	$ sudo apt-get install openssh-server
Connect on ssh from your pc (-X allows display, usefull for the future)

	$ ssh -X <laptop-name>@<laptop-ip>

Setup your computer to accept software from packages.ros.org

	$ sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

Set up your keys

	$ sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 421C365BD9FF1F717815A3895523BAEEB01FA116

Update Debian packages and install the full package of ros-indigo

	$ sudo apt-get update
	$ sudo apt-get install ros-indigo-desktop-full

Rosdep enables you to easily install system dependencies for source you want to compile

	$ sudo rosdep init
	$ rosdep update

Add ROS environment variables to your bash session

	$ echo "source /opt/ros/indigo/setup.bash" >> ~/.bashrc
	$ source ~/.bashrc

Add this tool to easily download many source trees for ROS packages

	$ sudo apt-get install python-rosinstall

Install Chrony: a tool for synchronization

	$ sudo apt-get install chrony
	$ sudo ntpdate ntp.ubuntu.com

Install Kinect Driver

	$ mkdir ~/kinectdriver 
	$ cd ~/kinectdriver 
	$ git clone https://github.com/avin2/SensorKinect 
	$ cd SensorKinect/Bin/
	$ tar xvjf SensorKinect093-Bin-Linux-x64-v5.1.2.1.tar.bz2
	$ cd Sensor-Bin-Linux-x64-v5.1.2.1/
	$ sudo ./install.sh

Network Configuration

	$ echo export ROS_MASTER_URI=http://localhost:11311 >> ~/.bashrc
	$ echo export ROS_HOSTNAME=IP_OF_LAPTOP >> ~/.bashrc

Connect the Laptop to the robot via usb and bring up the robot:

	$ roslaunch turtlebot_bringup minimal.launch 
	
	
If everything is well configured, you must hear the turtlebot bringing up.
Let this terminal running.




