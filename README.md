# task1AI-WEEK4-
^^ Launch TurtleBot navigation
<br> <br>
This guide provides step-by-step instructions for setting up and launching TurtleBot3 navigation using ROS Noetic. The process includes installing necessary packages, setting up the simulation environment in Gazebo, creating a map using SLAM (Simultaneous Localization and Mapping), and launching the navigation stack.
<br> <br>

## - Prerequisites
Ensure to install all the required dependences!!

## Step 1: Install TurtleBot Packages

1. Update the package list and install dependencies:
    ```bash
    sudo apt update
    sudo apt upgrade
    ```

2. Install TurtleBot3 packages:
    ```bash
    sudo apt install ros-noetic-turtlebot3 ros-noetic-turtlebot3-msgs ros-noetic-turtlebot3-slam ros-noetic-turtlebot3-navigation
    ```

3. Install TurtleBot3 simulation packages:
    ```bash
    sudo apt install ros-noetic-turtlebot3-simulations
    ```

## Step 2: Set Up the Environment

1. Set the TurtleBot3 model environment variable:
    ```bash
    echo "export TURTLEBOT3_MODEL=burger" >> ~/.bashrc
    source ~/.bashrc
    ```

2. Install the Gazebo simulator (if not already installed):
    ```bash
    sudo apt install ros-noetic-gazebo-ros-pkgs ros-noetic-gazebo-ros-control
    ```

## Step 3: Launch TurtleBot in Gazebo

1. Launch the TurtleBot3 world in Gazebo:
    ```bash
    roslaunch turtlebot3_gazebo turtlebot3_world.launch
    ```

## Step 4: Create a Map Using SLAM

1. Launch the SLAM node:
    ```bash
    roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
    ```

2. Launch the teleoperation node to control the robot:
    ```bash
    roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
    ```

3. Save the map once it’s created:
    ```bash
    rosrun map_server map_saver -f ~/map
    ```

## Step 5: Launch Navigation

1. Launch the navigation stack:
    ```bash
    roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=$HOME/map.yaml
    ```

## Additional Tips

- Ensure you have sourced your ROS setup files in every new terminal you open:
    ```bash
    source /opt/ros/noetic/setup.bash
    source ~/.bashrc
    ```

- If you encounter dependency issues, you can use `rosdep` to install them:
    ```bash
    rosdep update
    rosdep install --from-paths src --ignore-src -r -y
    ```
