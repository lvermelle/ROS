# 2- Install ROS Client

These are the steps to install a complete ROS Client.

A ROS Client is the OS working on a remote PC to control the turtlebot.

This installation is nearly the same that the ROS Server Installation.

This tutorial is a shortcut of the tutorial available on http://wiki.ros.org/indigo/Installation/Ubuntu.

(Remote PC = client)

## Prerequisites:
-Ubuntu 14.4 installed on your PC to install the indigo version of ROS.

If your PC is not boot on Ubuntu 14.4, it's recommended to install VirtualBox and create a Ubuntu 14.4 Virtual Machine.

-Internet connection.


## Commands:
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

Network Configuration: this is what differentiate a client and a server

	$ echo export ROS_MASTER_URI=http://IP_OF_LAPTOP:11311 >> ~/.bashrc
	$ echo export ROS_HOSTNAME=IP_OF_PC>> ~/.bashrc
