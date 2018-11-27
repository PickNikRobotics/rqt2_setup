# RQT1

## Setup

In order to reproduce our setup first create a ROS2 workspace at `~/ros2_ws/` by following the instructions on the ros2 wiki at: [installing ROS2 from source on Ubuntu 18.04](https://index.ros.org/doc/ros2/Linux-Development-Setup/)

## Build ROS2 and RQT2 From Source

### Download ROS2 and RQT2 Repositories

    cd ~/ros2_ws
    wget https://raw.githubusercontent.com/PickNikRobotics/rqt2_setup/master/rqt2.repos
    vcs import src --force < rqt2.repos

### Install Dependencies

    rosdep install --from-paths src --ignore-src --rosdistro bouncy -y --skip-keys "console_bridge fastcdr fastrtps libopensplice67 rti-connext-dds-5.3.1 urdfdom_headers rqt_gui_cpp"

**Note:** Some dependencies are skipped including *rqt_gui_cpp* which aren't yet fully ported or are othewise not yet available from rosdep.

### Build ROS2 and RQT2

    cd ~/ros2_ws/
    colcon build

Advanced colcon usages:

 - Show verbose output:

      colcon build --event-handlers console_direct+

 - Only build one package and its dependencies:

      colcon build --packages-up-to rqt_shell

### Source your environment

    . install/local_setup.bash

## Install from Debian

TODO: Release when Crystal is released

## Run Examples

Launching RQT gui will bring up a window where you can load and unload RQT plugins.

    ros2 run rqt_gui rqt_gui

Alternatively, you can run individual plugins.

 - RQT Shell:

    ros2 run rqt_shell rqt_shell

 - RQT Python Console

    ros2 run rqt_py_console rqt_py_console
