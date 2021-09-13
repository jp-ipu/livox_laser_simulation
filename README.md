# Livox Laser Simulation
A package to provide plug-in for [Livox Series LiDAR](https://www.livoxtech.com).

## Requirements
- ROS(=Kinectic)
- Gazebo (= 9.x, http://gazebosim.org/)
- Ubuntu(=18.04)
- Install `libode-dev`

## Results
- avia

![](resources/avia.gif)
- mid40

![](resources/mid40.gif)
- mid70

![](resources/mid70.gif)
- tele

![](resources/tele.gif)
- horizon

![](resources/horizon.gif)

## Usage

> Note that the published point cloud message is sensor_msg/PointCloud in main branch. If you want to obtain snesor_msg/PointCloud2 message, you can checkout to "PointCloud2-ver" branch.

Before you write your urdf file by using this plugin, catkin_make/catkin build is needed.

A simple demo is shown in livox_simulation.launch

Run 
```
    roslauch livox_laser_simulation livox_simulation.launch
```
to see.

We can choose the lidar model by selecting different CSV file in scan_mode dir from changing the launch file:
- avia.csv
- horizon.csv
- mid40.csv
- mid70.csv
- tele.csv

## Parameters(example by avia)

- laser_min_range: 0.1  // min detection range
- laser_max_range: 200.0  // max detection range
- horizontal_fov: 70.4   //°
- vertical_fov: 77.2    //°
- ros_topic: scan // topic in ros
- samples: 24000  // number of points in each scan loop
- downsample: 1 // we can increment this para to decrease the consumption

### This repository is now maintained by CaoMing(https://github.com/EpsAvlc) and LvFengchi. Its appreciate with the help of Caoming!

## Manual Offset seetings
The branch origin/config_calibration is a temporary solution for correcting the offset error of two lidar simulation.

The File [/config/offset.yaml](/config/offset.yaml) can be used to control the offset by defining the topic name of the lidar data to be corrected with respect to another topic. The offset in transaltion (x,y,z) and rotation angles (roll ,pitch,yaw) in radian can be defined.