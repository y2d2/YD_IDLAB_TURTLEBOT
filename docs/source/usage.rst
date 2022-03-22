Usage
=====

.. _installation:

Installation
------------

To use Lumache, first install it using pip:

.. code-block:: console

   (.venv) $ pip install lumache

Creating recipes
----------------

To retrieve a list of random ingredients,
you can use the ``lumache.get_random_ingredients()`` function:

.. autofunction:: lumache.get_random_ingredients

The ``kind`` parameter should be either ``"meat"``, ``"fish"``,
or ``"veggies"``. Otherwise, :py:func:`lumache.get_random_ingredients`
will raise an exception.

.. autoexception:: lumache.InvalidKindError

For example:

>>> import lumache
>>> lumache.get_random_ingredients()
['shells', 'gorgonzola', 'parsley']


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

1) To connect qualisys with ROS: 
.. code-block:: console
   $ roslaunch mocap_qualisys qualisys.launch  server_address:=10.10.193.16
   
 
2) To connect the UWB to ROS: 
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
   $ roslaunch turtlebot3_

  


   $ roslaunch mocap_qualisys qualisys.launch  server_address:=10.10.193.16
