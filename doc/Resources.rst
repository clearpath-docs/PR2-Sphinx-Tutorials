Resources
===========

This page should be the first page landed on if you are a new-comer or wanting to be directed to reading resources, tutorials, exercises, or explanations. The resources will be readings and places you can go to find more information about why and how the structures are implemented. It will not explain the specific implementation, but it will give a general idea of the concepts used to derive that implementation. I will try to cover most of the things used in the day-to-day activities while servicing the PR2's software. All in all, these are all responsibilities of the OSSE engineer. You must maintain, make announcements, document, develop, and release resources pertaining to everything below, and reading everything here is essential to excelling and succeeding in this position


Understanding Debian Packages
------------------------------

*  `What is a debian package <https://www.debian.org/doc/manuals/debian-faq/ch-pkg_basics.en.html>`_ 
*  `How to make a debian package from source <https://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html>`_

.. note:: A debian package installs files and modifies the structure of the system that it is installed on. To make a debian package, include a debian sub-folder in that directory. The debian sub-folder will contain files that document things about that debian package such as its version, how it is to be distributed, what files to include, what commands to run before and after installation. The command that makes it, e.g "dpkg-buildpackage" should be run inside the directory that you want to turn into a debian package. Parameters to this command can also generate the source debian packages (.dsc files). 

Understanding The PR2 Github Repos
-----------------------------------

*  `Quick 15 minute tutorial to learn git <https://try.github.io/levels/1/challenges/1>`_
*  https://github.com/PR2/ is the repository for the PR2 ROS packages. It contains the source code for ROS packages. In each package, there will be a package.xml and a CMakeLists.txt. If there is a repository that also has a folder with the same name as that repository, then this repository contains a metapackage. A metapackage is a collection of packages.
*  https://github.com/pr2-debs/ is the repository for the PR2 Debian packages. It contains the source debian packages. To make modifications to someone's PR2 system debian packages, modify these and upload them to the PR2's system debian repository.
*  https://github.com/pr2-gbp/ is the release repository for the https://github.com/PR2/ ROS packages. Some packages may be released in https://github.com/ros-gbp/.
 
To understand these repositories, understand that they were originally hosted on SVN and were ported over during the WG->CpR transition. These can be found at https://code.ros.org/trac/pr2debs/browser/trunk for the system debians for the PR2. 

It includes all the packages and the source for the installer for the basestation.

Understanding The ROS Package Release Process
-----------------------------------------------

*  Read the `bloom documentation <http://bloom.readthedocs.org/en/0.5.7/>`_ and know what packages should be released (PR2 Packages). 
*  Read the `ROS wiki page on bloom <https://support.clearpathrobotics.com/hc/admin/articles/%20http:/wiki.ros.org/bloom>`_.
*  The Build farm will tell you what packages have been released, the `BuildFarm for Hydro <http://www.ros.org/debbuild/hydro.html>`_ 
*  To test a released package and see if it can be compiled/ a debian be created, use the `prerelease server <http://prerelease.ros.org/select_distro>`_. 
*  Documentation on how to use the pre-release can be found `here <http://wiki.ros.org/bloom/Tutorials/PrereleaseTest>`_. 

Understand that before a package is released, there are three commands that will help testing locally: (1) catkin_make test, (2) catkin_make install, and (3) catkin_make --isolated. All of these should be run during compilation to capture all the bugs. See the catkin documentation to make sure your dependencies are set up correctly. 

Understanding The Catkin Build Process
----------------------------------------

*  `The official catkin documentation <http://docs.ros.org/hydro/api/catkin/html/>`_
*  `Catkin ROS documentation <http://wiki.ros.org/catkin>`_
*  `Migrating notes from Groovy to Hydro <http://wiki.ros.org/hydro/Migration>`_
*  JBohren's excellent catkin guides: `Intro <http://jbohren.com/articles/gentle-catkin-intro>`_, `Modular ROS Packages <http://jbohren.com/articles/modular-ros-packages/>`_

Understanding The PR2 System Debian Repository
-------------------------------------------------

This is the second repository you should know about. The PR2 software exists on two repositories. The `ROS repository <https://github.com/PR2>`_ and the `system repository <http://pr2packages.clearpathrobotics.com/>`_. The Ubuntu Amazon EC2 Instance hosts a Nginx webserver that indexes the reprepro files and reprepro indexes and maintains the package management. To take this over and understand what is going on, I suggest reading about Amazon EC2, adding ssh-keys (to login to the EC2 server), Nginx, and reprepro. The packages are also signed, and so GPG and package signing should be understood.

*  `Reprepro <https://wikitech.wikimedia.org/wiki/Reprepro>`_: In short for this, you will have to know how to officially add a debian package to a repository, to stage a package, to remove, and to export the packages. Exporting the packages makes them publicly available. Importing them adds them to the package management system. Removing them removes them from the system. Staging them holds them in a directory that will be merged later into the package management system.
*  `Nginx <https://www.linode.com/docs/websites/nginx/basic-nginx-configuration>`_. Nginx is a web server just like Apache2, but I found it to be much simpler and it looks nicer as well. The bugs are also more conclusive. 
*  `SSH Keys <https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2>`_. you will have to add the .pem key to your keys list to access the EC2 instance. 
*  Using an `Amazon EC2 Server <http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EC2_GetStarted.html>`_. It's good to get the gist of whats going on. 
*  `Understanding GPG signing <https://wiki.debian.org/Keysigning>`_. 

Useful Knowledge Bases For The PR2's Software
------------------------------------------------

In short, the ROS wiki has many tutorials on administrating the PR2 (The stuff a person providing software support should know) http://wiki.ros.org/pr2_robot/Tutorials .

PR2 software usage documentation is best found by going to wiki.ros.org/package_name where package_name is the name of the package you want details about.

This page, under header "High-level-capabilities" provides good links towards info on the PR2. http://wiki.ros.org/Robots/PR2

What is EtherCAT?
-------------------

*  `An example of running the PR2 etherCAT <http://wiki.ros.org/pr2_etherCAT/Tutorials/Running>`_
*  `Ethercat hardware tutorials and documentation <http://wiki.ros.org/ethercat_hardware>`_ and the `tutorials related to the hardware <http://wiki.ros.org/ethercat_hardware/Tutorials>`_ 
*  Essentially, etherCAT is like ethernet but with less wires. It is no different in paradigm than debugging an ethernet network.
*  Ethercat overview from `their website <http://www.tech-faq.com/ethercat.html>`_ 

The Original PR2 Wiki
-------------------------

*  Clearpath Robotics is soon moving towards deprecating the PR2 support wiki in favor for hosting the resources entirely on the Clearpath Robotics website.
*  The old wiki (PR2 Support) is hosted `here <http://pr2s.clearpathrobotics.com/wiki/>`_ 


The Clearpath PR2 Documentation
---------------------------------

*  Of particular interest is the `downloads page <http://www.clearpathrobotics.com/pr2/downloads/>`_
*  and the new `knowledge base page <https://support.clearpathrobotics.com/hc/en-us/categories/200217239-PR2>`_ 

The PR2 Manual
----------------

A powerful `resource originating from the WG days <http://www.clearpathrobotics.com/wp-content/uploads/2014/08/pr2_manual_r321.pdf%20>`_ that describes how the technical side of the PR2 works. 

Existing PR2 Debian Repositories
-----------------------------------

*  This is the most modern packages repository for the PR2. It hosts all the system debians but at the moment they only exist on the pr2-dev branch. After the Hydro release Dec 1, full installs will be available from the 0.6.2 pr2-release branch 
*  http://packages.willowgarage.com once was the main source of software for the PR2 realm. It no longer works since the server went offline. Ilia brought it back up and hosted it on a S3, however S3 treats filenames weird and this broke the repo. http://packages.willowgarage.s3-website-us-east-1.amazonaws.com 