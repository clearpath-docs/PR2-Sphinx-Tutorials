Building PR2 Debians
========================


All of the PR2 Debians are now built on the internal Clearpath Robotics Jenkins server. They are set to poll every 5 minutes the source code
found at https://github.com/pr2-debs. The PR2 ROS packages are built and distributed by the ROS build farm.

In the near future, we will make this Jenkins server public and provide public information on build status and release status. If you want to make a PR to these repos, please, we will have an automated job check the git scm and it will test if your new package builds and report back.

Thank you,
Dash.
