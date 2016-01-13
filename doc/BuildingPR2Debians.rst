Building and Modifying The PR2 Debians
========================================

There are other tutorials located here that may help but should however be considered legacy tutorials as there are some things that no longer work.

1.  The repositories are no longer existant.
2.  The code no longer exists on the SVN.
3.  Uploading the debians to a reprepro server is a bit different because the server is an Amazon EC2 instance. Find the legacy tutorials here https://pr2s.clearpathrobotics.com/wiki/Maintenance/SystemDebs.

Following the PR2 Developer Environment tutorial will get you the debian code on your computer. Following onto that, there should be a directory called pr2_debian_packages where all of the git code was cloned into.


Building The PR2 Debians From Source
--------------------------------------

To build the packages from source run the builddebs script inside of the directory of your choice. This will create debian packages for all of the subdirs inside of that pkg.

.. code:: bash

	cd ~/pr2_debian_packages
	cd pr2
	sudo ./builddebs

Another example of building the basestation debians

.. code:: bash

	cd basestation-precise
	sudo ./builddebs

The debians will all have .deb file extensions.


Understanding Where The Debian Packages Go
-------------------------------------------

The debian packages for the PR2 eventually get copied into a queue of a reprepro directory. This directory then is held for staging while they are reviewed, and eventually accepted into a development repository. (pr2-dev). For example, look at the server pr2packages.clearpathrobotics.com. It is an NGinx file index of a reprepro repository hosted on an Amazon EC2 instance. 

Upon arrival to the site, notice there is the pr2, pr2-dev, and pr2-releases repositories. The pr2 repository is where all of the pr2 debian packages are held that make it pass acceptance testing in the pr2-dev repository. The pr2-releases repository is where a full working version of the pr2 debian packages are held. Note that this includes everything from wg-test, other, basestation, shared, and pr2.

Inside the pr2-dev repository, where most of the action happens, click into the Ubuntu repository and there you will see the setup files for a reprepro repository. The queue holds all of the packages that have yet to be merged or (in this case, haven't been cleaned up). The pool is where the accepted development packages are. A user will be able to, if they set their sources lists up, download and install the debian packages inside of the pr2-dev section. This is where it becomes real! You have serious reponsibility at this point if you are serving packages to someone as you will modify their system in hopefully a positive way.

Eventually, when a user installs them, the files are unpacked and installed onto their system to where the debian files specify them to be. That is the entire delivery and distribution process of a debian package.

Modifying A Debian Package 
----------------------------

Lets say you wish you modify the contents of a debian package. There's some file on the users computer that needs a command added to its script to make it easier for the user to use the software system you've created for them. How can you do that? You'll have to go into the source code of the debian package and modify its contents.

1. Traverse into the directory of the pr2's robot.py script

.. code:: bash

	cd ~/pr2_debian_packages/pr2-precise/pr2-core/root/usr/lib/

2. Notice that the debian package will put files directly into the /root/usr/lib directory if they are placed there inside the deb file. Open the robot.py with your favourite editor

.. code:: bash

	gedit robot.py

3. Modify it as you see fit. Change a string of an output. Add a new command. Just make some changes.

4. Now modify the changes list and update it with a new version line. This is done manually to bypass the annoyance of the builddebs script because I have been too busy to actually change it to not have to do this step.

.. code:: bash

	sudo gedit ~/pr2_debian_packages/pr2-precise/pr2-core/changelog
	dch 

5. After dch, which stands for debian changelog, open it with nano (2) and then modify the version number. In the case of pr2-core, it was at 0.5.42 and so I updated it to 0.5.43. Save the file and then re-build the package:

.. code:: bash

	cd .. 
	sudo dpkg-buildpackage -us -uc

6. There you have it! Look in the above directory once the package is done building to find your new 0.5.43 deb. To check if it is there:

.. code:: bash

	>cd ..
	ls * | grep 0.5.43

