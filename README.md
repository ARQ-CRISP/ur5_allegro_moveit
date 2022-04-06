# ur5_allegro_moveit
Moveit package for ur5 &amp; allegro combined.

You can launch the MoveIt! and RViz test using:

```
roslaunch ur5_allegro_moveit demo.launch optoforce:=true
```

This package is meant to be used with optoforce sensors, but you can disable them via the launch parameter _optoforce_. In that case MoveIt will give warnings that some links in the collision matrix (e.g. omd_1) does not exist. These warnings can be ignored.

## Install
*Tested on Ubuntu 18.04, ROS-Melodic*

In order to use this package, the following should be installed:

* [MoveIt!](https://moveit.ros.org/)
* [*allegro-hand-ros*](https://github.com/gokhansolak/allegro-hand-ros)
* [ Universal_Robots_ROS_Driver
](https://github.com/UniversalRobots/Universal_Robots_ROS_Driver) (details below)
* [optoforce-publisher](https://github.com/ARQ-CRISP/optoforce-publisher)

Most of these packages are installed for accessing the _xacro_ and _urdf_ files they contain.

### Setting up with the ur_robot_driver

Recently, [ur_modern_driver]() has become obsolete, in favor of ur_robot_driver. There are a number of things to configure to be able to control the real robot with the new drivers. The following should be done once for setup:

* Install the ur_robot_driver as described [here](https://github.com/UniversalRobots/Universal_Robots_ROS_Driver#requirements).
  - Replace universal-robot package with fmauch's fork of universal-robot.
  - Update UR5 robot software as described here, if not done earlier.
  - Install URCal external-control and create the program as described here.
* Modify the controller namespace of controller.yaml

The following must be done each time after starting the robot:

* In control pendant, click _run program_ go to file and choose _external-control.urp_.
* Start ROS drivers:
  ```
  roslaunch ur5_allegro_moveit ur5_allegro_bringup.launch robot_ip:=<your-ip> optoforce:=true
  ```
* Press play button (▶) in the control pendant.
* See "Robot ready to receive control commands" log.
* Start controlling with Moveit or other.
