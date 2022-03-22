Usagetest
=========

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

Connect to the turtlebot through ssh (Be carefull IP adress might change since it is not a fixed one.) : 

.. code-block:: console

   $ ssh ubuntu@10.10.135.10

Use the password: turtlebot
  
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

   $ $rosdock 
   
In the rosdock container start the experiment with: 

.. code-block:: console

   $ $rosdock roslaunch yd_turtlebot3_pos_control yd_idlab_control.launch shape:=HS_CW
   
In order to change the experiment change the value of the shape parameter to: 
HS_CW : High Speed, Clockwise
HS_CCW : High Speed, Counterclockwise 
LS_CW : Low Speed, Clockwise 
LS_CCW : Low Speed, Counterclockwise
GRID: For the grid shape. 

!!! IF you have the NLOS object in the room make sure the robot starts somewhere close to the center to avoid collision. (The robot has not yet been upgrade to include collision avoidance.) 


In order to stop the experiment tap ctrl + C in the rosdock shell. 
   $ roslaunch mocap_qualisys qualisys.launch  server_address:=10.10.193.16
