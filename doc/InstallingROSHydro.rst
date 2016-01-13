Installing ROS Hydro on a PR2
===================================================

Pre-install
------------

1. Upgrade your source list as per "Upgrading your sources lists".

2. ROS Hydro must be installed on your system, and you must be running Ubuntu 12.04 or a similar kernel to that. To do install ROS Hydro, please take a look at these instructions.

Groovy and Hydro both run on the same Ubuntu distribution and that means no major changes must occur to the debians or programs that require interfacing with the linux kernel. Two new debian packages, "pr2-core-hydro" and "basestation-core-hydro" will add the required setup files and links to launch the correct Hydro environment for the PR2.

This means a swap will be available to move between Groovy and Hydro, and it is not of any cost to yourself and it will not effect any Groovy installation on the system if chosen to try it out. To prevent any environment entanglement or complexity, two new commands "robot groovy" and "robot hydro" will swap between environments for you.

Installing the Hydro Debians
-----------------------------

.. code:: bash

	sudo apt-get update
	sudo apt-get install pr2-core-hydro
	sudo apt-get install pr2-core

Installing the PR2 ROS debians
-------------------------------

.. code:: bash

	sudo apt-get install ros-hydro-pr2*

**Note:** Sometimes the package management system on the PR2 or system breaks and will try to uninstall key packages. If ever asked to uninstall pr2-environment or pr2-core files. Do not say yes or the PR2 will be unable to boot and a full re-install will be required.

The start sequence to launch the robot is still the same:

.. code:: bash

	export ROS_ENV_LOADER=/etc/ros/env.sh
	roslaunch /etc/ros/robot.launch

and what code/ROS debians it uses will depend on what environment the robot exists in. "robot groovy" and "robot hydro" will help change that environment back and forth.

