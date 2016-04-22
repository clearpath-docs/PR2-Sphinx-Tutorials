Willow Garage to Clearpath Robotics PR2 Transition FAQ
=======================================================  

1. The pr2-users mailman mailing list server is no longer online. That medium of communication was replaced by the pr2-users Google group located here: https://groups.google.com/forum/#!forum/pr2_users. Access is by request and is usually accepted within 2-5 minutes during EST daylight hours.

 
2. The pr2-admins mailing list no longer exists. Due to lack of demand, and communication to the pr2-admins via internal messaging, this is no longer required. 

 
3. Aptproxy.willowgarage.com should be removed from PR2 and basestations sources.list and sources.list.d/* files. This includes anything inside sources.list.d that includes it. It was only meant to be a mirror to download Ubuntu packages quickly from inside Willow Garage. This server is no longer online, and it may have caused confusion when running an apt-get update on a robot or basestation.

 
4.  pr2support.willowgarage.com is  available at http://pr2s.pr2.clearpathrobotics.com/wiki/ and will no longer be available at the prior address. 

 
5. Official ROS distro releases info can be found on the ros-users mailing list http://lists.ros.org/mailman/listinfo/ros-users.  For the pr2 releases, those announcements will be communicated here at the pr2-users list. Official communication of the PR2 (regarding hardware modifications, products, and maintenance) can be found on this Google Groups list, as well as with an additional direct communication to owners of the PR2. 

 
6. Hydro development is the main target of our development team at Clearpath. MoveIt! is supported for the PR2 Hydro release, but ros_control integration is undecided for the moment. ROS Indigo will have the PR2 running Ubuntu 14.04 with ros_control and the current architecture will still exist for Indigo (E.g pr2_controller_manager and pr2_kinematics)
 

7. A current experimental/unstable beta version of Hydro for the PR2 can be downloaded and installed. There are known bugs that are actively being fixed and help is appreciated in the form of pull requests to https://github.com/PR2/. It is not recommended to install these packages and set up these repos on the PR2 unless you are prepared and able to work through bugs and fix any errors that may occur. If the apt-get program attempts to uninstall core packages on the pr2 like pr2-environment or pr2-core, always say no or else the PR2 will not start the next time you reboot it.
 
 
Instructions on how to install the beta/unstable version of Hydro can be found here: wiki.ros.org/Robots/PR2/Hydro