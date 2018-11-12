# RQT2

## Install ROS2

In order to reproduce our setup follow the instructions on the ros2 wiki for [installing ROS2 from source on Ubuntu 18.04](https://index.ros.org/doc/ros2/Linux-Development-Setup/).

TODO: After Crystal release, support building RQT2 on top of debian ROS2 packages

## Build From Source

### Install Dependencies

    sudo apt-get install python3-vcstool python3-rosdep2

If you haven't already, initialize rosdep:

    sudo rosdep init
    rosdep update

### Download RQT2 repositories and dependencies

    mkdir -p ~/ros2_ws/src
    cd ~/ros2_ws
    wget https://raw.githubusercontent.com/PickNikRobotics/rqt2_setup/master/rqt2.repos
    vcs import src < rqt2.repos
    rosdep install --from-paths src --ignore-src --rosdistro bouncy -y --skip-keys "console_bridge fastcdr fastrtps libopensplice67 rti-connext-dds-5.3.1 urdfdom_headers rqt_console rqt_gui_cpp"

### Build the RQT2 repositories

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

RQT Shell:

    ros2 run rqt_shell rqt_shell

RQT Python Console

    ros2 run rqt_py_console rqt_py_console
