Release Notes
=============== 

Patch notes for release 3.18.7-rt1 (March 10th, 2016)
-----------------------------------------------------------

* Bare bones system
* C1 boots with the capability to teleop the robot via keyboard
* No C2 netbooting, no sensors on C2 (no lidar, tilt laser)
* No wireless or VPN capabilities. 

Patch notes for PR2 Head NUC release 3.19.0-33 (March 15th, 2016)
--------------------------------------------------------------------

* Works for getting the Kinect setup
* Packages for setup on C1 can be found at https://github.com/pr2-debs
* Calibration procedures to be found at https://github.com/code-iai/iai-kinect2
* Usability notes found on this guide:


Patch notes for release 3.19.0-49 (March 22nd, 2016)
------------------------------------------------------

* Fairly stable system, C2 boots, C1 boots.
* Wireless capabilities are disabled
* Teleop works, teleop general works.
* Motors, action servers, controllers are up
* Dashboard and RViz for reviewing the robots state


Patch notes for release 3.19.0-49 (March 24th, 2016) (Suggested)
--------------------------------------------------------------------

* All of the advancements above, including the ability to use the sensors on C2 with a hub (shipped via clearpath) into the top USB port on C2
* A big bug fix which included regressing to a 3.19.0-42 kernel point release because the other version was missing the cdc-acm and ftdi-sio modules which prevented USB usage.
* Wireless capabilities disabled still. Fix pending.


Patch notes for release 3.19.0-49 (April 6th, 2016) 
-------------------------------------------------------
* Regression causing c2 not to boot
* Wireless still not working

Patch notes for release 3.19.0-49 (April 15th, 2016) 
==================================================================
-> Regression fixed c2 not booting. Now boots correctly without 50% chance of it working due to race conditions in the network interface names on boot
-> Left arm starts on calibration
-> Sensors enabled with units that are using an external USB from top hub of C2
-> Sensor data, battery data, all working/running through C2
-> Changed C2 to use 3.19.0-42-lowlatency kernel because it both includes the necessary sensor modules, and it fixes some realtime errors


Patch notes for release 3.19.0-49 (April 22nd, 2016) (Suggested)
=================================================================
-> Wireless access point available for PR2 at SSID "PR2-wireless"
-> Password and SSID can be changed by modifying /etc/hostapd/hostapd.conf
-> Default password is "clearpath"
-> PR2 navigation and mapping
