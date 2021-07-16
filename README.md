# Create-and-save-a-map-by-using-Turtlebot3-with-SLAM-approach_Mobile-Robot-Base
## PC Setup
First you need to sign up in (https://app.theconstructsim.com/#/Home) and start a new project using ROS melodic, open web shell and follow these steps to install turtlebot3 packages.

### 1. Install TurtleBot3 Packages
```
$ sudo apt-get install ros-melodic-dynamixel-sdk
$ sudo apt-get install ros-melodic-turtlebot3-msgs
$ sudo apt-get install ros-melodic-turtlebot3
```
### 2. Set TurtleBot3 Model Name
choose the Trurtlebot you want to work with: 

In case of TurtleBot3 Burger
```
echo "export TURTLEBOT3_MODEL=burger" >> ~/.bashrc
```
In case of TurtleBot3 Waffle Pi
```
echo "export TURTLEBOT3_MODEL=waffle_pi" >> ~/.bashrc
```


## Simulation
After choosing the Trurtlebot you need to run it in an environment using a simulation, and you can use:

### Gazebo Simulation
#### 1. Install Simulation Package
```
$ cd ~/catkin_ws/src/
$ git clone -b melodic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
$ cd ~/catkin_ws && catkin_make
```
------

#### 2. Launch Simulation World
There are 3 simulation environments prepared for TurtleBot3, you can select any one of these environments to launch Gazebo:
##### 1 ) Empty World
```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch
```
-------

##### 2 ) TurtleBot3 World
```
$ export TURTLEBOT3_MODEL=waffle
$ roslaunch turtlebot3_gazebo turtlebot3_world.launch
```
-------

##### 3 ) TurtleBot3 House
```
$ export TURTLEBOT3_MODEL=waffle_pi
$ roslaunch turtlebot3_gazebo turtlebot3_house.launch
```
--------


### SLAM Simulation
#### 1. Launch Simulation World
```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_gazebo turtlebot3_world.launch
```
---------

#### 2. Run SLAM Node
```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
```
---------
---------

#### 3. Run Teleoperation Node
```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```
--------

#### 4. Save Map
```
$ rosrun map_server map_saver -f ~/map
```
---------
---------
