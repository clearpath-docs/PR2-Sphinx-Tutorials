Reinstalling the PR2 (Fix)
=========================== 

When packages.willowgarage.com went down, the original installer was broken that was looking towards the packages.willowgarage.comrepository. A hack below will allow you to modify the system yourself to make sure the install to Groovy/Precise12.04 works and your robot is at the most recent version. Fixes will be made to the relevant debian files and pushed out on the repo soon, in the case that they have not been, then this is the place to look. (As of Nov 20, 2014 they have not been pushed to the reprepro repo located at http://54.68.185.13/pr2-dev/ubuntuand you are using the only working install method). Any errors or problems that arise can be articulated to Clearpath Robotics via the Willow Garage Zendesk located at http://wgsupport.willowgarage.com/tickets/new

 
1. Make back-ups of the below file on your basestation

.. code:: bash

	cp /var/www/robot_precise64.preseed ~/your/chosen/location
	cp /var/www/pr2-packages/lists/ ~/your/chosen/location
	cp /var/www/packages/conf/updates ~/your/chosen/location
 
2. Replace the above files on the basestation with these downloaded ones found here: http://www.clearpathrobotics.com/pr2/downloads/

.. code:: bash
 
	cp -rf ~/Downloads/robot_precise64.preseed /var/www/robot_precise64.preseed
	cp -rf ~/Downloads/lists /var/www/pr2-packages/
	cp -rf ~/Downloads/updates /var/www/pr2-packages/conf/
 
Running sudo robot-install should now work properly and begin downloading files. If you receive errors about the aptproxy.willowgarage.com, please see "WG to CPR PR2 Transition FAQ" at `our PR2 support page <https://support.clearpathrobotics.com/hc/en-us/categories/200217239-PR2>`_. The netboot sequence should be followed then as per the `manual <http://www.clearpathrobotics.com/wp-content/uploads/2014/08/pr2_manual_r321.pdf>`_ at Chapter 16. In short, press F12 when the server boots. I found it helpful to use the KVM during this procses (instructions `here <http://www.scribd.com/doc/40902096/pr2-service-port>`_).
 
This solution uses the temporary repo hosted by Austin Hendrix, and the official repo located at 54.68.185.13 will be maintained by Clearpath, and is scheduled to be released sometime near the end of Beta for PR2 Hydro (Dec 1st)