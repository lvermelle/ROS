# 5- Run easy scripts

In this part, we will see how to use easy python algorithms

## Prerequisites:
- Client and Server installed, configured and working.

## Commands:
Bringup the robot on server

On client, import somes algorithms:

	$ mkdir ~/tutorial
	$ cd ~/tutorial/
	$ git clone https://github.com/markwsilliman/turtlebot/
	$ cd turtlebot

You can see all the algorithms available with 

	$ ls
You can see the code of these algorithms ($ nano <algo>.py), modify it and run it on the turtlebot: for examples:

	$ python goforward.py
Ctrl+C to stop

	$ python kobuki_batery.py
Ctrl+C to stop

	$ python take_photo.py
The photo is saved in the directory as "photo.png". To see it:

	$ eog photo.png 

Edit the go_to_specific_point_on_map.py file to modify the points where you want turtlebot go. 
To get interresting points, get coordinates with a cursor on rviz while creating your map in tutorial 4- Interac with its environment.
Then run the code:

	$ python go_to_specific_point_on_map.py


## Your turn:
You can take parts of these codes to create your own code.
But if you need the exange informations with turtlebot for example, you will need to call more librairies. 
And to write these codes more complex, you will need to create a package.

