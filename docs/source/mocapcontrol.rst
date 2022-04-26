.. _MocapC:

Mocap control
=============

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
   
   
Starting the turtlebot
----------------------

Next make sure the turtlebot is switched on and the control is running. See :ref:`Turtlebot`. for more info. 
 
Starting an experiment
----------------------

Connect to the iiot PC through ssh again: 

.. code-block:: console

   $ ssh iiot@10.10.133.50

Start a rosdock (docker container with specific ROS version): 

.. code-block:: console

   $ rosdock 
 
(For more information and troubleshooting on rosdock see :ref:`rosdock`.)
In the rosdock container start the experiment with: 

.. code-block:: console

   $ roslaunch yd_turtlebot3_pos_control yd_idlab_control.launch shape:=HS_CW
   
In order to change the experiment change the value of the shape parameter to: 

* HS_CW : High Speed, Clockwise
* 2HS_CCW : High Speed, Counterclockwise 
* LS_CW : Low Speed, Clockwise 
* LS_CCW : Low Speed, Counterclockwise
* GRID: For the grid shape. 
* CIRCLE: For a circle shape. 
* U: For a u-shape 

Other parameter[default value] can be changed :

.. code-block:: console
   $ roslaunch yd_turtlebot3_pos_control yd_idlab_control.launch paremeter:=value
   
Parameters concerning the control of the robot: 

* maxSpeed[1]: Maximum speed allowed in the control of the robot. 
* minSpeed[0.1]: Minum speed used in the control of the robot.
* targetTolerance[0.2]: Distance to target that is acceptable. (Be carefull to reduce this one to much. Tendency for the robot to drive arround the target.)
* angularControlP[2]: The P-gain for the angular velocity. 
* maxAngularSpeed[1]: The max angular velocity. In MOCAP settings this can be set very high. When swithcing to UWB-IMU / UWB-Odom control best to keep a lower value so to avoid slipping and shocks. 
* sampleLength[0.1]: Distance between local waypoints of the control. 
* numberOfLaps[5]: Number of times the robot repeats the trajectory until it stops. 

Parameters concering the trajectories: 

* speed[0.1]: the speed used to calculate the trajectory. [GRID, CICLE, U]
* counterclockwise[0]: Set to 1 if you want to move in the reverse way. [GRID, CICLE, U]
* stopTime[30]: the seconds the robot is standingstil at each waypoint in the grid. E.g. For BLE 70 is used. [ONLY FOR GRID] 
* gridMesh: The distance between waypoints of the grid [ONLY FOR GRID] 

.. warning::
	IF you have the NLOS object in the room make sure the robot starts somewhere close to the center to avoid collision. (The robot has not yet been upgrade to include collision avoidance.) 
	
	You can use the remote control to manouvre the robot aswell, please see :ref:`turtlebotRC` for more information. 

In order to stop the experiment tap ctrl + C in the rosdock shell. 

.. warning::
	For now the trutlebot will repeat the patern infinetly (or atleast until battery runs down) until it is stoped by the user. Works are in the make to automate the stopping as well, but have not been implemented yet on the robot. 

 

