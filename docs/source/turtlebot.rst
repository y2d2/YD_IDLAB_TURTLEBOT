Turtlebot
=========
robotis_: https://emanual.robotis.com/docs/en/platform/turtlebot3/overview/

In this section the basics are covered to operate the turtelbot for the experiments. 
In case more detail is need please visit: robotis_ .

Starting the Turtlebot
----------------------
Before to switch on the turtlebot disconnect the UWB tag. (a udev rule has to be maid). 
Connect the battery to the robot and switch on the main powerswitch.

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
   
Use ctrl + c to close the ros session.

to reboot use: 

.. code-block:: console

   $ sudo reboot
   
Battery
-------

When the battery level is to low the turtlebot will stop and start to beep. 
In this case it is important to close off the turtlebot and change the battery as soon as possible. 

closing an the Turtlebot
------------------------
type ctrl + c to close the ros session

To shut down the turtelbot use: 

.. code-block:: console

   $ sudo poweroff
   
once the turtlebot is closed the main powerswitch can be switched off 
   

