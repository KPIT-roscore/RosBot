# KBot 
<img src="images/index.jpeg">
Learning and Fun with ROS Towards Autonomous Driving @ KPIT

## Build Status

[![Build Status](https://travis-ci.org/KPIT-roscore/RosBot.svg?branch=master)](https://travis-ci.org/KPIT-roscore/RosBot) 

## System Requirements

# Implementation of SLAM Algorithms in Simulation 

## Quick Start
This is a quick start guide for beginners intrested in running this project in your system
This Repo contains launch files for Gmapping, Hector Map and Rtab Map SLAM Algorithms.
It also includes launch files for Gazebo simulations.

If you are new to ROS please refer ROS wiki page - http://wiki.ros.org/ROS/Tutorials

### Setting up ROS in a Linux (Ubuntu) PC

In this project the stable version of ROS is used which is Kinetic.
To run this project on Melodic version just replace 'kinetic' with 'melodic' in the below commands.

ROS installation link - http://wiki.ros.org/kinetic/Installation/Ubuntu  (Install Desktop-Full)

### Installing essential dependencies

Install the following dependencies after ROS is installed

```
$ sudo apt-get update

$ sudo apt-get install ros-kinetic-slam-gmapping 

$ sudo apt-get install ros-kinetic-hector-slam   

$ sudo apt-get install ros-kinetic-rtabmap-ros

$ sudo apt-get install ros-kinetic-teleop-twist-keyboard

$ sudo apt-get install ros-kinetic-amcl

$ sudo apt-get install ros-kinetic-move-base

$ sudo apt-get install ros-kinetic-map-server

```

**_(At the time of writing, the package hector-slam is not available for melodic version of ROS)_**

### Setting up ROS Environment

Now, navigate to home directory and open .bashrc file by running the below command

```
$ cd

$ nano .bashrc
```

**_Add these at the end of .bashrc file and source the file_**

```
export ROS_MASTER_URI=http://localhost:11311/

export ROS_HOSTNAME=localhost
```

```
$ source /opt/ros/kinetic/setup.bash
```

Now, We have installed ROS and it's supporting dependencies to run this project.

### Cloning the Repo of Simulation Workspace

Download the RodBot Repo by running the following commands.

```
$ git clone https://github.com/hamsadatta/RosBot.git
```

Now change directory to 'Simulation_ws' and build the workspace using the following commands.

```
$ cd ~/RosBot/Simulation/Simulation_ws

$ catkin_make
```

The above command 'catkin_make' will build you workspace. Now you are all set to run the simulation.

### Initializing the Project workspace

```
$ source /opt/ros/kinetic/setup.bash

$ cd ~/RosBot/Simulation/Simulation_ws

$ source ~/RosBot/Simulation/Simulation_ws/devel/setup.bash
```
**_Sourcing ROS and Project directory is essential to run the project._**

```diff
- RUNNING ROSCORE IN THE BACKGROUND IS EXTREMELY IMPORTANT
```

### THE SIMULATION

#### *GMAP SLAM*

**Creating the Map**
Run the following commands below. And use teleop to move the robot around to create an accurate and thorough map.

In Terminal 1, launch the Gazebo world
```
roslaunch kbot_gazebo kbot_world.launch
```
In Terminal 2, start map building
```
roslaunch kbot_navigation gmapping_demo.launch
```
In Terminal 3, launch rviz and set the parameters:
```
roslaunch kbot_description kbot_rviz_gmapping.launch
```
In Terminal 4, start teleop
```
rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```


**Saving the Map**
In Terminal 5, save the map to some file path
```
rosrun map_server map_saver -f ~/Simulation_ws/src/kbot_navigation/maps/test_map
```


**Loading the Map followed by localization**
Close all previous terminals and run the following commands below. Once loaded, use rviz to set navigation waypoints and the robot should move autonomously.

In Terminal 1, launch the Gazebo world
```
roslaunch kbot_gazebo kbot_world.launch
```
In Terminal 2, start map building

**_Note:- To use the map that was saved earlier, please change the path for map in the below launch file._**
```
roslaunch kbot_navigation amcl_demo.launch
```
In Terminal 3, launch rviz
```
roslaunch kbot_description kbot_rviz_amcl.launch
```



#### *HECTOR MAPPING*
**Creating the Map**
Run the following commands below. Use the teleop to move the robot around to create an accurate and thorough map.

In Terminal 1, launch the Gazebo world
```
roslaunch kbot_gazebo kbot_world.launch
```
In Terminal 2, start map building
```
roslaunch kbot_navigation tutorial.launch
```
In Terminal 3, launch rviz and set the parameters:
```
roslaunch kbot_description kbot_rviz_gmapping.launch
```
In Terminal 4, start teleop
```
rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```


**Saving the Map**
In Terminal 5, save the map to some file path
```
rosrun map_server map_saver -f ~/Simulation_ws/src/kbot_navigation/maps/hector_map
```


**Loading the Map followed by localization**
Close all previous terminals and run the following commands below. Once loaded, use rviz to set navigation waypoints and the robot should move autonomously.

In Terminal 1, launch the Gazebo world
```
roslaunch kbot_gazebo kbot_world.launch
```
In Terminal 2, start map building

**_Note:- To use the map that was saved earlier, please change the path for map in the below launch file._**
```
roslaunch kbot_navigation amcl_demo.launch
```
In Terminal 3, launch rviz
```
roslaunch kbot_description kbot_rviz_amcl.launch
```




### *RTAB MAPPING*

**Creating the Map**
Run the following commands below. Use the teleop to move the robot around to create an accurate and thorough map.

In Terminal 1, launch the Gazebo world
```
roslaunch kbot_gazebo kbot_world.launch
```
In Terminal 2, start map building
```
roslaunch kbot_navigation rtab.launch
```
In Terminal 3, launch rviz and set the parameters:
```
roslaunch kbot_description kbot_rviz_gmapping.launch
```
In Terminal 4, start teleop
```
rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```


**Saving the Map**
Map server is not required in RTAB-MAP


**Loading the Map followed by localization**
Close all previous terminals and run the following commands below. Once loaded, use rviz to set navigation waypoints and the robot should move autonomously.

In Terminal 1, launch the Gazebo world
```
roslaunch kbot_gazebo kbot_world.launch
```
In Terminal 2, start map building
```
roslaunch kbot_navigation rtab.launch localization:=true
```
In Terminal 3, launch rviz
```
roslaunch kbot_description kbot_rviz_amcl.launch
```

## Issues 

## License

## Acknowledgements
