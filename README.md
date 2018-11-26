# RQT2

## Setup

In order to reproduce our setup follow the instructions on the ros2 wiki for [installing ROS2 from source on Ubuntu 18.04](https://index.ros.org/doc/ros2/Linux-Development-Setup/) stopping before the section: *Get ROS 2.0 code*.

TODO: After Crystal release, support building RQT2 on top of debian ROS2 packages

## Build From Source

### Download ROS2 and RQT2 Repositories

    mkdir -p ~/ros2_ws/src
    cd ~/ros2_ws
    wget https://raw.githubusercontent.com/ros2/ros2/release-latest/ros2.repos
    wget https://raw.githubusercontent.com/PickNikRobotics/rqt2_setup/master/rqt2.repos
    vcs import src --force < ros2.repos
    vcs import src --force < rqt2.repos

### Install Dependencies

    sudo rosdep init
    rosdep update
    rosdep install --from-paths src --ignore-src --rosdistro bouncy -y --skip-keys "console_bridge fastcdr fastrtps libopensplice67 rti-connext-dds-5.3.1 urdfdom_headers rqt_gui_cpp"

**Note:** If you see the error message about mulitply packages named *uncrustify_vendor* then run `rm -rf ~/ros2_ws/src` and start this section again.

### Build ROS2 and RQT2

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

RQT Gui:

    ros2 run rqt_gui rqt_gui

RQT Shell:

    ros2 run rqt_shell rqt_shell

RQT Python Console

    ros2 run rqt_py_console rqt_py_console
