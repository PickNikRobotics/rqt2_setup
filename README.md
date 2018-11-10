# Install RQT2

## Download RQT2 repositories and dependencies

    cd ~/ros2_ws
    wget https://raw.githubusercontent.com/PickNikRobotics/rqt2_setup/master/rqt2.repos
    vcs import src < rqt2.repos
    rosdep install --from-paths src --ignore-src --rosdistro bouncy -y --skip-keys "console_bridge fastcdr fastrtps libopensplice67 rti-connext-dds-5.3.1 urdfdom_headers rqt_console rqt_gui_cpp"

## Build the RQT2 repositories

    colcon build

## Source your environment

    . install/local_setup.bash

## Run some simple examples

RQT Shell:

    ros2 run rqt_shell rqt_shell

RQT Python Console

    ros2 run rqt_py_console rqt_py_console
