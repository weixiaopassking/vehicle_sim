# Overview
Autonomous driving car simulator based on gazebo.
The following sensors are simulated.
- velodyne (VLP-16, HDL-32E)
- camera
- imu
![screenshot from 2019-01-11 00-42-10-min](https://user-images.githubusercontent.com/8327598/50984661-bed3f780-1545-11e9-9af6-071ddd1cec76.png)

# Requirements
- ROS (higher kinetic)
- gazebo (higher version 7)

# Download
```shell
$ cd <catkin workspace/src/>
$ git clone https://github.com/yukkysaito/vehicle_sim.git --recurse-submodules
```
or if you already have a copy of the repo, run `$ git submodule update --init --recursive`.

# How to use

1. build

```shell
$ rosdep install --from-paths <vehicle_sim/vehicle_model path> -y
$ cakin_make
$ source "your catkin workspace"/devel/setup.bash
```

2. upgrade gazebo version and download gazebo models(**only once**)
   -  reason : https://bitbucket.org/DataspeedInc/velodyne_simulator/src/56d11e899ce0a198e7206298b3aaaf8004f3a2c6/gazebo_upgrade.md?fileviewer=file-view-default
```
$ rosrun vehicle_model setup.sh
```

3. launch gazebo

```shell
$ roslaunch vehicle_model world_test.launch
```

If GPU is available

```shell
$ roslaunch vehicle_model world_test.launch gpu:=true
```
[![](https://img.youtube.com/vi/JViNKB_igI4/0.jpg)](https://www.youtube.com/watch?v=JViNKB_igI4)

# Some example
- **Citysim** : http://gazebosim.org/blog/car_sim
```
$ roslaunch vehicle_model gazebo7_citysim.launch gpu:=true
```
![screenshot from 2019-01-11 00-40-35-min](https://user-images.githubusercontent.com/8327598/50985197-19ba1e80-1547-11e9-98d1-284b3172c064.png)
- **mcity(car_demo)** : https://github.com/osrf/car_demo
```
$ roslaunch vehicle_model gazebo_mcity.launch gpu:=true
```
![screenshot from 2019-01-11 00-38-49-min](https://user-images.githubusercontent.com/8327598/50985258-3e15fb00-1547-11e9-91d4-3b826b82136e.png)

- **Connect to Autoware** : https://github.com/CPFL/Autoware
If you need pointcloud map and path files, you can download following url
https://drive.google.com/drive/folders/1yu8s885HDkJp3IbMV06KWim2ZdUxIoIF?usp=sharing
```
$ roslaunch vehicle_model gazebo_autoware.launch gpu:=true
```
[![](https://img.youtube.com/vi/wIzZ25XJI2M/0.jpg)](https://www.youtube.com/watch?v=wIzZ25XJI2M)


# How to change vehicle info
You can customize sensor position and vehicle info.
- sensor position: config/caibration.yaml
- vehicle info: config/vehicle_info.yaml
