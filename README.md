# task1AI-WEEK4-
^^ Launch TurtleBot navigation
<br> <br>
This guide provides step-by-step instructions for setting up and launching TurtleBot3 navigation using ROS Noetic. The process includes installing necessary packages, setting up the simulation environment in Gazebo, creating a map using SLAM (Simultaneous Localization and Mapping), and launching the navigation stack.
<br> <br>

## - Prerequisites
Ensure to install all the required dependences!!

    $ sudo apt-get install ros-noetic-joy ros-noetic-teleop-twist-joy \
      ros-noetic-teleop-twist-keyboard ros-noetic-laser-proc \
      ros-noetic-rgbd-launch ros-noetic-rosserial-arduino \
      ros-noetic-rosserial-python ros-noetic-rosserial-client \
      ros-noetic-rosserial-msgs ros-noetic-amcl ros-noetic-map-server \
      ros-noetic-move-base ros-noetic-urdf ros-noetic-xacro \
      ros-noetic-compressed-image-transport ros-noetic-rqt* ros-noetic-rviz \
      ros-noetic-gmapping ros-noetic-navigation ros-noetic-interactive-markers
      
 

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

    <img src=https://github.com/user-attachments/assets/a6a029b4-0621-463f-b552-4363267a5e37 width=80%>


3. Install TurtleBot3 simulation packages:
    ```bash
    sudo apt install ros-noetic-turtlebot3-simulations
    ```
    <img src=https://github.com/user-attachments/assets/d2c2df00-c31d-4473-8403-d71bac51df6e width=80%>


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

    <img src=https://github.com/user-attachments/assets/3da22931-3cf2-4d16-a82a-8f1b86dc3bd0 width=80%>

    

## Step 4: Create a Map Using SLAM

1. Launch the SLAM node:
    ```bash
    roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
    ```
   <img src=https://github.com/user-attachments/assets/4afca4c2-09fc-4135-bf83-931057db4f8a width=80%>
    
   <img src=https://github.com/user-attachments/assets/761d9b47-2170-4e27-88e6-906c44230448 width=80%>


2. Save the map once it’s created:
    ```bash
    rosrun map_server map_saver -f ~/map
    ```

3. Launch the teleoperation node to control the robot:
    ```bash
    roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
    ```

## Step 5: Launch Navigation

1. Launch the navigation stack:
   
    ```bash
    roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=$HOME/map.yaml
    ```
    <img src=https://github.com/user-attachments/assets/f340e91d-2238-4012-8c48-678ef7fde34c width=80%>
