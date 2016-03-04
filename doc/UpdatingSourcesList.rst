Updating the Sources List for PR2 Debian Packages
===================================================

There are two working debian package servers for the PR2. When packages.willowgarage.com went down, there was a lot of confusion as to where to update/upgrade from. By having two repositories at this moment, we hope to eliminate the possibility that both are down and the community is unable to use the PR2 platform. In the future, we will have set up a back-up of the pr2packages.clearpathrobotics.com repository as well.

The first one is the official Clearpath Robotics PR2 package server located at http://pr2packages.clearpathrobotics.com and those packages can be accessed by adding into your /etc/apt/sources.list.d/pr2debs.list two lines:

Get your key first:

.. code:: bash

        sudo wget http://clearpathrobotics.com/pr2-packages/ubuntu/pr2packages.gpg | sudo apt-key add

Add sources to your /etc/apt/sources.list.d/pr2-debs.list

.. code:: bash

	deb http://clearpathrobotics.com/pr2-packages/ubuntu trusty pr2
	deb http://clearpathrobotics.com/pr2-packages/ubuntu trusty main

For Groovy installations and Hydro installations of the PR2, you will want this link:

.. code:: bash

	deb http://packages.namniart.com/repos/pr2/pr2-0.6.1/ubuntu/ precise pr2
	deb http://packages.namniart.com/repos/pr2/pr2-0.6.1/ubuntu/ precise main

These files will install all of the system related debians for the PR2's and basestations. For installing the PR2 ROS Debians, please see http://wiki.ros.org/Robots/PR2/hydro or the respective tutorial on the PR2 Clearpath website.

For installing the basestation debians, please do the above but with 'basestation' in place of the 'pr2' specifier in the debian line, as so:

.. code:: bash

	deb http://clearpathrobotics.com/pr2-packages/ubuntu trusty basestation
	deb http://clearpathrobotics.com/pr2-packages/ubuntu trusty main

Reminder: the packages.namniart.com repository does not have any of the new hydro debians in them, nor the Indigo, or Kinect 2 packages in them.
