UWB Experiments
===============

Control of the robot
--------------------
Two modes of operation have been implemented for now for the Turtelebot: 

#. Through the mocap: Make sure all the steps of :ref:`MocapC` are covered before to continue here. 
#. Through the remote control (RC): Make sure to follow te steps as detailed in :ref:`turtlebotRC`.

Both modes of operation can run in parallel, it suffices to switch from one mode to the other using the RC. 

Start the UWB ros node
----------------------
To connect the UWB to ROS: 

.. code-block:: console

	$ roslaunch mqtt_ros_bridge nuc_bridge.launch 


Starting the recordings
-----------------------

Start another rosdock ( :ref:`rosdock`.) container by specifing the name: 

.. code-block:: console

   $ rosdock -n monitor
   
Navigate to the shared folder, between the rosdock and the host pc, in the rosdock session. (On the rosdock the container is located in root and called "sharedDrive".) If the IIOT pc is the host the shared folder is located in the home directory of the iiot user in ~/rosdockDrives/sharedDrive)

.. code-block:: console

   $ cd   /sharedDrive
.. warning::
.. note::
	It is a good practisch to create a new folder with the experiments of the day, that is marked by the date and a meaningfull title of the experiment: (eg. 2022_03_24_NLOS_EXPERIMENTS) and save the results in this folder. 


In order to capture all the signals (-a option) and give it prefix  through the -o option for rosbag record command: 

.. code-block:: console

   $ rosbag record -a -o LS_CW_TWR_NOCIR_NLOS
   
In order to use the data navigate to the shared folder on the host pc (NOT in the rosdock). 

.. note::
	It may occure the data is owned by the root of the rosdock (user that recorded the data.) and not the iiot user of the host machine. 
	In order to fix this in on the host machine change the ownership of the folder.
   	
   	.. code-block:: console

   		$ sudo chown iiot:iiot -R ~/rosdockDrives/sharedDrive
