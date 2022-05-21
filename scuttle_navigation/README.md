# scuttle_navigation

The `scuttle_navigation` [ROS](https://www.ros.org/) package provides configurations for the
[dwa_local_planner](http://wiki.ros.org/dwa_local_planner), the [global planner](http://wiki.ros.org/global_planner?distro=noetic)
and the different [costmaps](http://wiki.ros.org/costmap_2d?distro=noetic) adapted to the SCUTTLE
robot.

## Dependencies

The configurations in this repository assume you have the following prerequisites installed on the
device on which you want to run this code. That device might be an Ubuntu machine or a physical
SCUTTLE using Raspberry Pi OS.

1. [ROS Noetic](http://wiki.ros.org/noetic) with the `ros-noetic-navigation`, `ros-noetic-robot` and
   `ros-noetic-tf2` packages.
1. A working [ROS workspace](http://wiki.ros.org/catkin/Tutorials/create_a_workspace).
1. The [scuttle_description](https://github.com/scuttlerobot/scuttle_description) package installed
   in your workspace.
1. The [scuttle_bringup](https://github.com/scuttlerobot/scuttle_bringup) package installed in your
   workspace.

The ROS navigation assumes that a map is available either via [acml](http://wiki.ros.org/amcl?distro=noetic)
and a [map server](http://wiki.ros.org/map_server?distro=noetic) or via a
[SLAM node](https://github.com/scuttlerobot/scuttle_slam). If no map is available then the navigation
will fail.

## Usage

After installing the prerequisites you can pull this repository to the device on which you want to
run the code.

    cd <YOUR_ROS_WORKSPACE>/src
    git clone -b noetic https://github.com/scuttlerobot/scuttle_navigation.git

Once the code is on the device you can 'build' the workspace

    cd <YOUR_ROS_WORKSPACE>
    catkin_make

Finally you can run the navigation stack for SCUTTLE

    roslaunch scuttle_navigation scuttle_navigation.launch

## Configurations

There are several different configuration files for the different parts of the navigation stack.
All of these configurations are referenced in the [move_base.launch](launch/move_base.launch) file.

### Costmaps

The navigation stack uses two separate [costmaps](http://wiki.ros.org/costmap_2d?distro=noetic). One
for the [global planner](param/global_costmap_params.yaml) and one for the
[local planner](param/local_costmap_params.yaml). Additionally there is a shared, common,
[configuration](param/costmap_common_params.yaml) that has information that applies to both the
global planner and the local planner.

### DWA local planner

The [configuration](param/dwa_local_planner_params.yaml) file for the local planner contains
the configuration values for the [DWA local planner](http://wiki.ros.org/dwa_local_planner).

### Global planner

The [configuration](param/global_planner_params.yaml) file for the global planner contains the
configuration for the [global planner](param/global_costmap_params.yaml).
