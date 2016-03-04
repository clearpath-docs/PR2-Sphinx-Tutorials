Installing ROS Indigo on a PR2
===================================================

Pre-install
------------

1. Upgrade your source list as per "Upgrading your sources lists".

2. Ubuntu Trusty with Kernel 3.19-0.49-lowlatency (or above) must be installed on your system. To install the PR2 ROS Indigo packages, please take a look at these instructions.


Installing the Hydro Debians
-----------------------------

.. code:: bash

	sudo apt-get update
	sudo apt-get install pr2-core-indigo
	sudo apt-get install pr2-core

Installing the PR2 ROS debians
-------------------------------

.. code:: bash

	sudo apt-get install ros-indigo-pr2*


The start sequence to launch the robot has changed:

.. code:: bash

	roslaunch /etc/ros/robot.launch 
        (optional) roslaunch /etc/ros/robot.launch c2:=false

If you have a kinect 2 on your robot:

.. code:: bash

        export KINECT2=true
        (optional) roslaunch /etc/ros/robot.launch 

Note at the time of writing this, c2 was having USB issues this I chose not to enable C2, so you can pass in the parameter c2:=false

