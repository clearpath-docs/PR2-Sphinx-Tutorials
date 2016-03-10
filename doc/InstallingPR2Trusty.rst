Installing ROS Indigo on a PR2
===================================================

This install method assumes you have nothing installed, or wish to re-write
the disk image you currently have on your PR2 computer. C2 is installed
via diskless netboot and runs a non-persistent linux kernel. (e.g lost after turn off)


Pre-install
------------

1. Download Clonezilla and create a USB with Clonezilla on it, you will need it
to then install the PR2 image. Follow these instructions: http://clonezilla.org/downloads.php to get the ISO
and then use Ubuntu Start-up disk creator to create the ISO for Clonezilla

2. Set your BIOS in C1 to boot from a USB. Yes, you will need to connect a keyboard and monitor.
Please see http://clearpathrobotics.com/guides/pr2/ConnectAMonitor

3. Pick your .tar.gz (release files) from http://clearpathrobotics.com/pr2-packages/pr2-releases/ 

4. pr2-3.18.7-rt1 is the first distribution shipped. It has limited functionality.
You can find more about what versions have what functionality on the http://clearpathrobotics.com/pr2-packages/pr2-releases/pr2-3.18.7-rt1-release-notes.txt or
on the website wiki at https://clearpathrobotics.com/guides/pr2/ReleaseNotes. However, as of writing it is the only distribution available.

5. pr2-3.19.0-49-lowlatency should be available by March 10th, 2016.

6. Extract the contents of the .tar.gz and put them onto a USB (copy and paste). Make sure the USB is empty before you do this. You are now ready to install your PR2 Trusty Indigo with Clonezilla!


Installing The .tar.gz contents onto the PR2 Computer:
----------------------------

1. If you have completed above, follow these prompts to get the contents installed:





Updating the contents of your new PR2 Trusty Indigo machine
-----------------------------

To pull new ROS Indigo packages:

.. code:: bash

	sudo apt-get update
	sudo apt-get install ros-indigo-pr2-*

To pull new PR2 Trusty Debian packages:

.. code:: bash

        sudo apt-get update
        sudo apt-get install pr2-*

** Note please do not install the NUC packages on the PR2 if you have a Kinect. Be careful when removing
pr2-environment as it may make your system unusable.
	

Additionally:
-----------------------------

The start sequence to launch the robot has changed:

.. code:: bash

	roslaunch /etc/ros/robot.launch 
        (optional) roslaunch /etc/ros/robot.launch c2:=false

If you have a kinect 2 on your robot:

.. code:: bash

        export KINECT2=true
        (optional) roslaunch /etc/ros/robot.launch 

Note at the time of writing this, c2 was having USB issues this I chose not to enable C2, so you can pass in the parameter c2:=false

