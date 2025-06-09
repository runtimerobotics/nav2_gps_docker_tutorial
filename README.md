# Nav 2 GPS Tutorial in ROS 2 Humble

This repository include docker compose files and nav2 gps tutorial package work on ROS 2 Humble. The official tutorial mentioned in this [link](https://docs.nav2.org/tutorials/docs/navigation2_with_gps.html).


## Prerequesties

- Docker installed on your system


## Installation of Docker

Clone the repository
```
git clone https://github.com/runtimerobotics/nav2_gps_docker_tutorial.git
```

```
cd ~/nav2_gps_docker_tutorial/docker_setup_scripts/
```

```
chmod +x setup_docker_ubuntu.sh
```

```
sudo ./setup_docker_ubuntu.sh
```

## Create a ROS 2 workspace in the main OS

```
mkdir -p ~/master_ros2_humble_ws/src

cp -r ~/nav2_gps_docker_tutorial/navigation2_tutorials ~/master_ros2_humble_ws/src


```


## Starting Nav2 using Docker Compose

```
cd ~/nav2_gps_docker_tutorial/docker_compose_nav2_humble
```


Start Docker compose

```
docker compose -f docker-compose-nvidia.yml build
```

```
docker compose -f docker-compose-nvidia.yml up
```

Take a new terminal to attach new docker terminal

```
cd ~/nav2_gps_docker_tutorial/docker_compose_nav2_humble

./start_container.sh ros2_nav_humble

source /ros_entrypoint.sh

colcon build

source install/setup.bash

```

## Start Nav2 and Gazebo with GPS

```
ros2 launch nav2_gps_waypoint_follower_demo gps_waypoint_follower.launch.py use_rviz:=True


ros2 run nav2_gps_waypoint_follower_demo interactive_waypoint_follower


ros2 launch nav2_gps_waypoint_follower_demo mapviz.launch.py
```

In mapviz set custom path of image as

```
file:///home/robot/master_ros2_humble_ws/src/test_no_alpha//{level}/{x}/{y}.png

```

or open mapviz_config.mvc from ~/master_ros2_humble_ws/src


# Reference

- Github [issues](https://github.com/ros-navigation/navigation2_tutorials/issues/77)