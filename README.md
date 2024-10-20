## Installation
- this repo was tested on Ubuntu 20.04 with ROS noetic
- there are quite a few dependencies that are not included in this repo. If you face any error while doing **catkin_make**, run **sudo apt-get install ros-noetic-(dependencies)**
```
sudo apt install ros-noetic-twist-mux
sudo apt install libgeographic-dev
sudo apt install ros-noetic-teleop-twist-joy
sudo apt install ros-noetic-interactive-marker-twist-server
sudo apt install ros-noetic-map-server
sudo apt install ros-noetic-jackal-desktop
sudo apt install ros-noetic-hector-gazebo-plugins
suod apt install map_server
git clone https://github.com/Evintjh/MA4822-sensors-application-proj.git
catkin_make
```
## Localisation/Sensor fusion
- Default sensor fusion: odom + IMU, rostopic: /odometry/filtered
- To test out sensor fusion of odom + IMU + gps, rostopic: /odometry/gps
```
roslaunch robot_localization navsat_transform_template.launch
```

## Mapping
To do 2D mapping:
- ensure that you do not drive/turn the Jackal bot too quickly, otherwise accuracy might be affected
```
roslaunch jackal_navigation gmapping_demo.launch
roslaunch jackal_viz view_robot.launch config:=gmapping
# To save map in your current directory:
rosrun map_server map_saver -f mymap 
```

## Testing Navigation Stack
```
roscore 
```

For visualisation:
- use the rviz UI to open the config file, ma4822_jackal.rviz, in the repo
```
rviz 
```


To run simulator with robot_localization package (for sensor fusion):
```
roslaunch jackal_gazebo jackal_world.launch 
```


To run navigation stack with your new map:
```
roslaunch jackal_navigation amcl_demo.launch [map_file:=/path/to/mymap.yaml]
```


## Current problems:
- IMU causes drift after staying stationary for awhile. Still looking up on solutions for that.
