# RSE-Go-Chase-It
Localazing a robot in a maze
## Structure
```
# RSE-Where-Am-I
Contains Where-Am-I project, where it is able to identify the robot position related to it's environment, using AMCL algorithm
RSE-Where-Am-I                     # Where Am I Project
├── my_robot                       # my_robot package
│   ├── launch                     # launch folder for launch files
│   │   ├── robot_description.launch
│   │   ├── world.launch
│       ├── amcl.launch
│   ├── meshes                     # meshes folder for sensors
│   │   ├── hokuyo.dae
│   ├── urdf                       # urdf folder for xarco files
│   │   ├── my_robot.gazebo
│   │   ├── my_robot.xacro
│   ├── world                      # world folder for world files
│   │   ├── world1.world
│   ├── CMakeLists.txt             # compiler instructions
│   ├── package.xml                # package info
│   ├── config
│   │   ├── local_costmap_params.yaml
│   │   ├── global_costmap_params.yaml
│   │   ├── costmap_common_params.yaml
│   │   ├── base_local_planner_params.yaml
│   ├── maps
│   │   ├── map.yaml
│   │   ├── map.pgm
├── pgm_map_creator                # pgm map creator package
│   ├── launch                     # launch folder for launch files
│   │   ├── request_publisher.launch
│   ├── src                        # source folder for C++ scripts
│   │   ├── collision_map_creator.cc
│   │   ├── request_publisher.cc
│   ├── maps                        # folder for generated maps
│   │   ├── map.pgm
│   ├── world                       # folder containing world files
│   │   ├── world1.world
│   ├── package.xml                 # package info
│   ├── msgs
│   │   ├── collision_map_request.proto
│   │   ├── CMakeLists.txt             # compiler instructions
│   ├── package.xml                # package info
├── teleop_twist_keyboard
│   ├── teleop_twist_keyboard.py
│   ├── package.xml
│   ├── CMakeLists.txt
│   ├── CHANGELOG.rst
│   ├── README.md
└──
```
**pgm_map_creator**: Create pgm map from Gazebo world file for ROS localization.

**teleop_twist_keyboard**: Generic Keyboard Teleop for ROS.

## Prerequisites
 
1. Install Gazebo and [ROS](http://wiki.ros.org/ROS/Installation) on Linux.
2. Install `sudo apt-get install ros-${ROS_DISTRO}-gazebo-ros-pkgs`
(If you are using gazebo11 it should be `sudo apt-get install ros-${ROS_DISTRO}-gazebo11-ros-pkgs`)
3. Cmake and gcc/g++

## Build and Launch

1. Move to `catkin_ws\` and build
```
$ cd /home/workspace/catkin_ws/

```

2.  Launch my_robot package
```
$ roslaunch my_robot world.launch
```

3. Launch the amcl launch file
```
$ roslaunch my_robot amcl.launch
```

4. Move the robot around to see the accuracy of localization results
```
rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```
