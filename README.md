## Installation
- this repo was tested on Ubuntu 20.04 with ROS noetic
- there are quite a few dependencies that are not included in this repo. If you face any error while doing **catkin_make**, run **sudo apt-get install ros-noetic-(dependencies)**
```
git clone https://github.com/Evintjh/MA4822-sensors-application-proj.git
catkin_make
```

## Testing 
```
roscore 
```

- To run simulator with robot_localization package (for sensor fusion)
```
roslaunch jackal_gazebo jackal_world.launch 
```

- To run navigation stack:
```
roslaunch jackal_navigation amcl_demo.launch
```
