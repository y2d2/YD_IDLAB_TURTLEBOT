Usage
=====

Setting IIOT PC.
----------------

Make sure qualisys is running on the qualisys laptop. 

First connect to the IIOT pc through  ssh. :
 
.. code-block:: console

   $ ssh iiot@10.10.133.50

Afterwhich you can start roscore: 

.. code-block:: console

   $ roscore

Make several more ssh connection with the IIOT PC and start following commands in seperate ssh sessions: 
To connect qualisys with ROS: 

.. code-block:: console

   $ roslaunch mocap_qualisys qualisys.launch  server_address:=10.10.193.16
   
 
To connect the UWB to ROS: 

.. code-block:: console

	$ roslaunch mqtt_ros_bridge nuc_bridge.launch 


Setting up the Turtlebot
------------------------
Before to switch on the turtlebot disconnect the UWB tag. (a udev rule has to be maid). 

Connect to the turtlebot through ssh (Be carefull IP adress might change since it is not a fixed one.) : 

.. code-block:: console

   $ ssh ubuntu@10.10.135.10

Use the password: turtlebot

It can take a bit of time. In case you are worrying you can keep an eye on the ping: 
.. code-block:: console

   $ ping 10.10.135.10
   
Run the following command on the turtlebot to setup all the systems: 

.. code-block:: console

   $ roslaunch turtlebot3_bringup turtlebot3_robot.launch
   

Starting an experiment
----------------------

Connect to the iiot PC through ssh again: 

.. code-block:: console

   $ ssh iiot@10.10.133.50

Start a rosdock  (docker container with specific ROS version): 

.. code-block:: console

   $ rosdock 
   
In the rosdock container start the experiment with: 

.. code-block:: console

   $ roslaunch yd_turtlebot3_pos_control yd_idlab_control.launch shape:=HS_CW
   
In order to change the experiment change the value of the shape parameter to: 
#. HS_CW : High Speed, Clockwise
#. 2HS_CCW : High Speed, Counterclockwise 
#. LS_CW : Low Speed, Clockwise 
#. LS_CCW : Low Speed, Counterclockwise
#. GRID: For the grid shape. 

!!! IF you have the NLOS object in the room make sure the robot starts somewhere close to the center to avoid collision. (The robot has not yet been upgrade to include collision avoidance.) 

In order to stop the experiment tap ctrl + C in the rosdock shell. 

In order to close the rosdock session use the exit command: 

.. code-block:: console

   $ exit

for more information on the rosdock please see the rosdock documentation part. 

Starting the recordings
-----------------------

Start another rosdock container with a specific name : 

.. code-block:: console

   $ rosdock -n monitor
   
navigate to the shared folder between the rosdock and the host pc. (On the rosdock the container is located in root and called "sharedDrive".) If the IIOT pc is the host the shared folder is located in the home directory of the iiot user in ~/rosdockDrives/sharedDrive)

.. code-block:: console

   $ cd   /sharedDrive
   
It is a good idea to create a new folder with the experiments of the day. (eg. 2022_03_24_NLOS_EXPERIMENTS) and save the results in this folder. 


In order to capture all the signals (-a option) and give it prefix  through the -o option for rosbag record command: 
.. code-block:: console

   $ rosbag record -a -o LS_CW_TWR_NOCIR_NLOS
   
In order to use the data navigate to the shared folder on the host pc (NOT in the rosdock). 

   
   
