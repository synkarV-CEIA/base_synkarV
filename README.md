# base_synkarV

This is a base project for SynkarV, designed for use with one of the mobile robotic bases.

## Installation

First clone the repository and build the docker image.

```bash
git clone https://github.com/synkarV-CEIA/base_synkarV.git 
cd base_synkarV
docker build -t synkar5-ros-noetic -f docker/Dockerfile .
```

## Usage

First we need to configure the network to connect to the robot through the ethernet port. To do so, we need to set a static IP address to the ethernet port. 

1. Set the IP address and netmask of the ethernet port. 
```bash
sudo ip addr add 10.10.10.1/24 dev <ethernet_interface>
```
2. Set the robot's default gateway.
```bash
sudo ip route add default via 10.10.10.199
```

Then we can run the docker container.

```bash
./run.sh
```

### Control the robot using the keyboard

To control the robot using the keyboard, we need to run the following command inside the docker container.

```bash
roscore
```

Now we should start the serial connection of the robot:

```
rosrun rosserial_python serial_node.py _port:=tcp
```

Then we can run the following command to control the robot using the keyboard.

```bash
rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```

We can also run it using the launch file provided.

```bash
roslaunch base_teleop teleop.launch
```

### Visualize the realsense d435 and t265 cameras

To visualize the realsense d435 and t265 cameras, we need to run the following command inside the docker container.

```bash
roslaunch realsense2_camera rs_d400_and_t265.launch
```

Then we can visualize the cameras using rviz.

```bash
rviz
```
