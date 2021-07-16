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

In case of TurtleBot3 Burger
```
echo "export TURTLEBOT3_MODEL=burger" >> ~/.bashrc
```
In case of TurtleBot3 Waffle Pi
```
echo "export TURTLEBOT3_MODEL=waffle_pi" >> ~/.bashrc
```


## Simulation

### Gazebo Simulation
#### 1. Install Simulation Package
Open a new terminal.
```
$ cd ~/catkin_ws/src/
$ git clone -b melodic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
$ cd ~/catkin_ws && catkin_make
```
OR
```
$ cd ~/catkin_ws/src/
$ git clone https://github.com/ROBOTIS-GIT/turtlebot3_msgs.git
$ git clone https://github.com/ROBOTIS-GIT/turtlebot3.git
$ cd ~/catkin_ws && catkin_make
```

#### 2. Launch Simulation World
Three simulation environments are prepared for TurtleBot3. Please select one of these environments to launch Gazebo.
##### 1 ) Empty World
```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch
```
![TurtleBots Burger](https://user-images.githubusercontent.com/85652061/125993421-908071fe-04cf-4d41-a2a9-ef64015ec710.png)


##### 2 ) TurtleBot3 World
```
$ export TURTLEBOT3_MODEL=waffle
$ roslaunch turtlebot3_gazebo turtlebot3_world.launch
```
![TurtleBot3 World](https://user-images.githubusercontent.com/85652061/125994195-23acd6d7-3099-4421-bc68-700ad2ba820d.png)
![TurtleBots Waffle](https://user-images.githubusercontent.com/85652061/125994027-e63f85c4-ce99-4fb1-a695-a1dc97882d7e.png)


##### 3 ) TurtleBot3 House
```
$ export TURTLEBOT3_MODEL=waffle_pi
$ roslaunch turtlebot3_gazebo turtlebot3_house.launch
```
![TurtleBot3 House](https://user-images.githubusercontent.com/85652061/125994257-455970d4-670b-46ba-a2f3-a024101edc19.png)


### SLAM Simulation
#### 1. Launch Simulation World
```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_gazebo turtlebot3_world.launch
```
![SLAM Node](https://user-images.githubusercontent.com/85652061/125994378-b65d3860-68ae-49e4-9b48-3bc3fb8242a5.png)

#### 2. Run SLAM Node
Open a new terminal.
```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
```
![Map1](https://user-images.githubusercontent.com/85652061/125994542-67033768-f3ee-469a-affd-389b657eac6f.png)


#### 3. Run Teleoperation Node
Open a new terminal.
```
$ export TURTLEBOT3_MODEL=burger
$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```

#### 4. Save Map
Open a new terminal.
```
$ rosrun map_server map_saver -f ~/map
```
![Map2](https://user-images.githubusercontent.com/85652061/125994735-0e9e9cf9-8995-4de4-848c-eb36e22134aa.png)

