Releasing a PR2 ROS Package
=============================

Clone the PR2's ROS repository located at https://github.com/pr2/

.. code:: bash

	cd ~ && git clone https://github.com/PR2/pr2_developer_kit

rosinstall all the packages

.. code:: bash

	cd pr2_developer_kit
 	git checkout hydro-devel
 	rosinstall .

Go to whatever package you choose, but in this example I will use the pr2_gripper_sensor package.

.. code:: bash

	cd pr2_gripper_sensor

Update your package and make whatever modifications required and then (don't forget to save them to github and test them with catkin_make compilation)

.. code:: bash

	catkin_generate_changelog
	catkin_prepare_release
	bloom-release --rosdistro hydro --track hydro pr2_gripper_sensor

For the release URL it will be located at https://github.com/pr2-gbp/${your_package_name}. For the source URL it is at https://github.com/pr2/${your_package_name}. That is all that is required. Following through on how to go through the bloom prompts; use this tutorial. http://wiki.ros.org/bloom/Tutorials/ReleaseCatkinPackage