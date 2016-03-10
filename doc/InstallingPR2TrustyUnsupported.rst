Installing PR2 Trusty on An Unsupported Computer
===================================================

Pre-install
------------

1. Download a distribution of Ubuntu server, or Ubuntu desktop. If you choose to use Ubuntu desktop on your PR2, note that you can skip to step 13 in installation steps.

2. Obtain a USB, 8GB+ in size.

3. Obtain a working internet connection and plug the ethernet cable into the wan0 port on the PR2.

4. Pick a username and password for your robot and write it down.

5. Change your BIOS settings to be bootable from USB on C1.

6. Change your BIOS settings on C2 so that it is booting from lan, so that the bios boot time is increased to 30+ seconds in order to hit the netboot trigger.

7. Realize that you will need at least four USB connections for C2 and two network ports. 

8. Realize that you will need 6 network ports, three USB ports, and a VGA/Video card for C1. You will also need a bluetooth chip and a wireless chip, integrated or external.

9. Since you are using different hardware, you will need to change things in the existing distribution of the PR2 ubuntu-trusty branches from https://github.com/pr2-debs. This list is extensive, and I may have missed some things:
- The accepted mac address for the netboot procedure
- The mac addresses used in the udev rules for network ports 
- Potentially, the kernel if the kernel you installed is incompatible with your hardware (Note: use a realtime kernel e.g linux-image-3.19.0-49-lowlatency)
- I won't cover here how to do these things (yet). But I may make commands to do this easier..

9.5 Install OpenSSH so you can ssh into the robot once it is plugged into the robot, either through the service port or via the lan ports in the back router of PR2

10. The wireless AP settings will need to be configured if you wish to use an AP that is different than the one currently used in the PR2

11. Once you have completed above, you can put the computers inside the PR2 and hook-up all of the cables. Diagrams for how to wire the backside of the PR2 can be seen below.

Note: you will be able to use ROS Jade and ROS Indigo with the PR2 after you have completed all of the steps above. Some of the packages may not work, in that case
carefully ensure you have made your hardware compatible with the PR2 Debian package software suite.


Installing the PR2 Debians
-----------------------------

Add sources lists to point towards the Clearpath Robotics servers on the PR2: (alternatively, you can setup your own Jenkins/Packages server if you wish to build from source)


sudo sh -c 'echo "deb http://www.clearpathrobotics.com/pr2-packages/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/pr2trusty.list'


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

