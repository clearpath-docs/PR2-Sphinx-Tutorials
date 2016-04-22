Debugging the PR2's Software 
===============================

When looking for specific files on the PR2 or any system, or something related to a keyword:

.. code:: bash

	locate checkethercat.sh 

When looking through files, you can use grep to find the lines relative to what you're looking for to save you time

.. code:: bash

	cat checkethercat.sh | grep /dev/

Some common techniques for debugging the PR2:
----------------------------------------------

*  Firstly, read the Support Wiki FAQ which has some interesting information. 
*  Understand some common ROS debugging techniques ROS Debugging

Debugging the ethercat network and running the script
------------------------------------------------------

checkethercat.sh will present any problems with the ethercat network.
The motorconf function and knowledge of the ethercat_hardware package will also help here.

Debugging the entire PR2 system with pr2-systemcheck
-----------------------------------------------------

The pr2-systemcheck function should be run after the command robot stop. It will give you a full diagnosis of the system.

.. code:: bash

	sudo pr2-systemcheck

Using the PR2 motor actuator diagnostic tool to find bugs and to help PR2 users give us a good idea of whats wrong

PR2 Workshop Videos
----------------------
 
*  `Starting PR2 Diagnostics And Debugging <https://www.youtube.com/watch?feature=player_embedded&v=6toTgF5B6mQ>`_  
*  `The PR2 Dashboard <https://www.youtube.com/watch?feature=player_embedded&v=nBuVuDaqspI>`_
*  `Runstops and diagnostic logs and PR2 dashboard <https://www.youtube.com/watch?feature=player_embedded&v=szZgRGvMB98>`_
*  `Starting and Stopping The PR2 controllers to test what is broken <https://www.youtube.com/watch?feature=player_embedded&v=5cL5wD7dc2c>`_
*  `Using RViz to debug the PR2 sensors <https://www.youtube.com/watch?feature=player_embedded&v=gMyC_zt79j8>`_
*  `Viewing the links and frames of a robot in RViz <https://www.youtube.com/watch?feature=player_embedded&v=JHTdISEbxY4>`_
*  `More Rviz videos <https://www.youtube.com/watch?feature=player_embedded&v=n2jeqq3j69g>`_
*  `Another Rviz video <https://www.youtube.com/watch?feature=player_embedded&v=DT1BlGL6wB8>`_
*  `Using rosbags to view how someone elses robot broke <https://www.youtube.com/watch?feature=player_embedded&v=ZbxLrLWC7Xk>`_
*  `Using the KVM To Debug The PR2 During Start Up <http://pr2s.clearpathrobotics.com/wiki/AdminTutorials/KVM>`_