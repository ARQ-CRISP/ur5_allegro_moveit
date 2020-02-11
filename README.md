# ur5_allegro_moveit
Moveit package for ur5 &amp; allegro combined.

You can launch the MoveIt! and RViz test using:

```
roslaunch ur5_allegro_moveit demo.launch optoforce:=true
```

This package is meant to be used with optoforce sensors, but you can disable them via the launch parameter _optoforce_. In that case MoveIt will give warnings that some links in the collision matrix (e.g. omd_1) does not exist. These warnings can be ignored.

## Install
*Tested on Ubuntu 16.04, ROS-Kinetic*

In order to use this package, the following should be installed:

* [MoveIt!](https://moveit.ros.org/)
* [*allegro-hand-ros (experimental branch)*](https://github.com/gokhansolak/allegro-hand-ros/tree/experimental)
* [universal-robot](https://github.com/ros-industrial/universal_robot)

**Optionally**, if you use Allegro with optoforce sensors:
* [optoforce-publisher](https://github.com/ARQ-CRISP/optoforce-publisher)

Most of these packages are installed for accessing the _xacro_ and _urdf_ files they contain.
