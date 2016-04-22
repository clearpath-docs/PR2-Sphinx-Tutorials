PR2 Developer Environment
=========================== 

You're all ready to set up the developer environment. What is required? Just a laptop. That's right. Unless you want to install source code directly onto the PR2. I'll go over that too. That brings us two sections for this tutorial.

1.  Setting up a PR2 ROS Developer Environment on your Laptop And PR2
2.  Setting up a PR2 Debian Development Environment on your Laptop And PR2

Setting up a PR2 Developer Environment on your laptop
-------------------------------------------------------

Assuming ROS is installed. If not, see this: http://wiki.ros.org/ROS/Installation. At the time of this tutorial, the PR2 works with up to Hydro and still Groovy. Groovy will be EOL'd soon, so it's safe to assume you can develop in ROS Hydro for a while. Note: This tutorial is for developing PR2 ROS Packages. The PR2 Debian packages tutorial can be found on (3).

1. Make a pr2_hydro_packages Catkin workspace. This will be used to house all of the source code for the PR2. Firstly, the directories are created and then the source directory is initialized to be a catkin workspace. There should then be a CMakeLists.txt symlink file in there.

.. code:: bash

  cd ~
 mkdir pr2_hydro_packages
 cd pr2_hydro_packages
 mkdir src
 cd src
 catkin_init_workspace
 cd ~

2. In what I'd like to call the staging area, clone the rosinstall file that will grab all of the relevant PR2 packages for development.

.. code:: bash

	cd ~/pr2_hydro_packages
	git clone https://github.com/PR2/pr2_developer_kit
	rosinstall .rosinstall

3. Move the downloaded pr2 packages into the src workspace

.. code:: bash

	mv * src/

4. Make these packages via catkin. As a developer, be aware of the three types of catkin_make. If one of these fails, the build will fail at release time on the build server, so it is best to always do all three when making/modifying a package to get full coverage.

.. code:: bash

 catkin_make
 catkin_make --install
 catkin_make test
 catkin_make --isolated

5. There you have it! All of your PR2 packages should be installed via source on your laptop. The usage is the exact same as how you would use them if installed via the package management system. There is one thing however...


6. Setting your environment to use the source packages. You must do this or else ROS will continue to use packages from the /opt/ros/distro directory. Run this command from the ~/pr2_hydro_packages directory.

.. code:: bash

	source devel/setup.bash

7. For example, use the code:

.. code:: bash

	roslaunch pr2_gazebo pr2_empty_world.launch

If you have a PR2, the instructions are the same assuming you're in the home directory and it is connected to the internet.

Setting up a PR2 Debian Development Environment 
-------------------------------------------------

By this point you should be familiar with the PR2 ROS code and understand that it is accessible via apt-get from the ROS servers or by source from the github servers. Currently, there are a couple of locations of where to get the debian code.

It used to exist on SVN/Trac here https://code.ros.org/trac/pr2debs/browser under trunk. This repository also contains the installer. I will discuss now the way of modifying the PR2's debian code by scratch.

1. Firstly, install the code from the github at https://github.com/pr2-debs/ and find a directory to put it into

.. code:: bash

	cd ~ && mkdir pr2_debian_packages
	cd pr2_debian_packages

2. Install the pr2's debian packages by cloning them onto your system. These are the debian files used for generic PR2's. The specific debs like pr2-precise have additional debs and modifications that make it compatible for precise. For indigo, there will be a pr2-trusty.

.. code:: bash

	git clone https://github.com/pr2-debs/pr2

3. If you're on 12.04, install the pr2-precise debians as well.

.. code:: bash

	git clone https://github.com/pr2-debs/pr2-precise

4. Note that the PR2 Debian development environment also has code for the basestation and test stations. Install the rest of these, including the installer. The installer will be talked about in a moment.

.. code:: bash

	git clone https://github.com/pr2-debs/wg-test-precise (This hosts the debian packages required for installing a WG Test station that are based off of 12.04)
	git clone https://github.com/pr2-debs/wg-test (Same as above, but generic packages)
	git clone https://github.com/pr2-debs/shared-precise (Packages that exist across basestation, wg-test, and PR2)
	git clone https://github.com/pr2-debs/shared (Same as above but not specific to precise)
	git clone https://github.com/pr2-debs/basestation-precise (Packages that exist only on the basestation)
	git clone https://github.com/pr2-debs/basestation (Same as above.. etc)
	git clone https://github.com/pr2-debs/other (Other packages that don't fit in the above categories)
	git clone https://github.com/pr2-debs/installer-precise (The installer for Ubuntu 12.04 basestation)
	git clone https://github.com/pr2-debs/installer (The installer for the basestation)

**Key point**: The installer's output is a DVD ISO that has all of the PR2's required packages and the basestations required packages. It is used to initialize a basestation, of which the PR2 then netboot installs itself from the basestation. No direct installation of the PR2 occurs.

5. A good tutorial for using/making/modifying the installers exists here https://pr2s.clearpathrobotics.com/wiki/Maintenance/Installer.

Building And Modifying The System Debs
----------------------------------------

Originally, when I first built the PR2's debs again from source I followed this tutorial written by Austin Hendrix https://pr2s.clearpathrobotics.com/wiki/Maintenance/DebOverview to get a good overview of what was going on. https://pr2s.clearpathrobotics.com/wiki/Maintenance/SystemDebs has the host of tutorials that walk you through building the debs. The process is the same, however the code is taken from Github and not SVN, and has not quite been automated yet. In the next section Building The System Debs I will cover all that you need to know for that.


