# RQT2

## Setup

In order to reproduce our setup first create a ROS2 workspace at `~/ros2_ws/` by following the instructions on the ros2 wiki at: [installing ROS2 from source on Ubuntu 18.04](https://index.ros.org/doc/ros2/Linux-Development-Setup/)

**Note:** RQT2 depends on the latest version of ROS2 repos. You *must* use ``https://raw.githubusercontent.com/ros2/ros2/master/ros2.repos`` instead of ``https://raw.githubusercontent.com/ros2/ros2/release-latest/ros2.repos``

## Build ROS2 and RQT2 From Source

Instlal PySide2 for Shiboken:

    pip3 install -U --user pyside2
    pip3 install -U --user pydot

### Download ROS2 and RQT2 Repositories

    cd ~/ros2_ws
    wget https://raw.githubusercontent.com/PickNikRobotics/rqt2_setup/master/rqt2.repos
    vcs import src --force < rqt2.repos

### Install Dependencies

    rosdep install --from-paths src --ignore-src --rosdistro bouncy -y --skip-keys "console_bridge fastcdr fastrtps libopensplice67 rti-connext-dds-5.3.1 urdfdom_headers"

If you are setting up your workspace as an [overlay](https://index.ros.org/doc/ros2/Colcon-Tutorial/#create-an-overlay), then you will need to add your underlaid workspace to your paths like so:

    rosdep install --from-paths src ~/ros2_ws/src/ --ignore-src --rosdistro bouncy -y --skip-keys "console_bridge fastcdr fastrtps libopensplice67 rti-connext-dds-5.3.1 urdfdom_headers"


### Build ROS2 and RQT2

    cd ~/ros2_ws/
    colcon build

Advanced Colcon commands:

 - Show verbose output:

        colcon build --event-handlers console_direct+

 - Only build one package and its dependencies:

        colcon build --packages-up-to rqt_shell

### Source your environment

    . install/local_setup.bash

## Install from Debian

TODO: Release when Crystal is released

## Run Examples

Launching RQT Gui will bring up a window where you can load and unload RQT2 plugins.

    ros2 run rqt_gui rqt_gui

Alternatively, you can run individual plugins.

 - RQT Shell:

        ros2 run rqt_shell rqt_shell

 - RQT Python Console

        ros2 run rqt_py_console rqt_py_console

To see the C++ plugin interface in action run ``rqt_image_view`` with the following commands:

 - In one terminal:

        ros2 run rqt_image_view rqt_image_view

 - In another terminal:

        ros2 run rqt_image_view image_publisher
