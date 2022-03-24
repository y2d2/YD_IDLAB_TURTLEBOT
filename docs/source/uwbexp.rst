UWB Experiments
===============

Control of the robot
--------------------
For now only Mocap control has been implemented.
Make sure all the steps of :ref: 'MocapC'. are covered. 

Start the UWB ros node
----------------------
To connect the UWB to ROS: 

.. code-block:: console

	$ roslaunch mqtt_ros_bridge nuc_bridge.launch 


Starting the recordings
-----------------------

Start another rosdock (for more info :ref: 'rosdock'.) container by specifing the name: 

.. code-block:: console

   $ rosdock -n monitor
   
Navigate to the shared folder, between the rosdock and the host pc, in the rosdock session. (On the rosdock the container is located in root and called "sharedDrive".) If the IIOT pc is the host the shared folder is located in the home directory of the iiot user in ~/rosdockDrives/sharedDrive)

.. code-block:: console

   $ cd   /sharedDrive
   
It is a good idea to create a new folder with the experiments of the day. (eg. 2022_03_24_NLOS_EXPERIMENTS) and save the results in this folder. 


In order to capture all the signals (-a option) and give it prefix  through the -o option for rosbag record command: 
.. code-block:: console

   $ rosbag record -a -o LS_CW_TWR_NOCIR_NLOS
   
In order to use the data navigate to the shared folder on the host pc (NOT in the rosdock). 

   
