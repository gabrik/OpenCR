# OpenCR: Open Source Control Module for ROS [![Build Status](https://travis-ci.org/ROBOTIS-GIT/OpenCR.svg?branch=master)](https://travis-ci.org/ROBOTIS-GIT/OpenCR/)
![](http://emanual.robotis.com/assets/images/parts/controller/opencr10/opencr_product.png)

## ROBOTIS e-Manual for OpenCR
- [ROBOTIS e-Manual for OpenCR](http://emanual.robotis.com/docs/en/parts/controller/opencr10/)

## Open Source related to OpenCR
- [Micro ROS Arduino](https://github.com/micro-ROS/micro_ros_arduino)
- [OpenCR](https://github.com/ROBOTIS-GIT/OpenCR)
- [OpenCR-Hardware](https://github.com/ROBOTIS-GIT/OpenCR-Hardware)
- [OpenCM 9.04](https://github.com/ROBOTIS-GIT/OpenCM9.04)
- [dynamixel_sdk](https://github.com/ROBOTIS-GIT/DynamixelSDK)
- [turtlebot3](https://github.com/ROBOTIS-GIT/turtlebot3)
- [open_manipulator](https://github.com/ROBOTIS-GIT/open_manipulator)
- [robotis_op3](https://github.com/ROBOTIS-GIT/ROBOTIS-OP3)

## Documents and Videos related to OpenCR
- [ROBOTIS e-Manual for OpenCR](http://emanual.robotis.com/docs/en/parts/controller/opencr10/)
- [ROBOTIS e-Manual for OpenCM 9.04](http://emanual.robotis.com/docs/en/parts/controller/opencm904/)
- [ROBOTIS e-Manual for OpenCM 485 Expansion Board](http://emanual.robotis.com/docs/en/parts/controller/opencm485exp/)
- [ROBOTIS e-Manual for Dynamixel SDK](http://emanual.robotis.com/docs/en/software/dynamixel/dynamixel_sdk/overview/)
- [ROBOTIS e-Manual for TurtleBot3](http://turtlebot3.robotis.com/)
- [ROBOTIS e-Manual for OpenManipulator](http://emanual.robotis.com/docs/en/platform/openmanipulator/)
- [ROBOTIS e-Manual for ROBOTIS OP3](http://emanual.robotis.com/docs/en/platform/op3/introduction/)
- [Videos for OpenCR](https://www.youtube.com/playlist?list=PLRG6WP3c31_VTd-u90LVXaT1B8NMjCSoj)

## Repository folder structure description
- arduino
  - opencr_arduino
    - libraries : A collection of some libraries that can be used with OpenCR.
    - opencr : OpenCR package core to be installed in Arduino.
    - tools : Tools for OpenCR firmware writing.
  - opencr_develop
    - opencr_bootloader : OpenCR bootloader source
    - opencr_ld : OpenCR loader source (related bootloader)
    - opencr_ld_shell : OpenCR loader script source for TB3
  - opencr_release
    - Folders(version name) : Compressed files for updating TB3 core binary with ld_shell for each TB3 core version.
    - shell_update : Latest Compressed files for updating TB3 core binary with ld_shell.
    - package_opencr_index.json : json file for Arduino OpenCR package.


## How to build for OpenCR

Install arduino-cli: https://arduino.github.io/arduino-cli/0.19/installation/

Add the OpenCR board manager

```
echo '''board_manager:
  additional_urls:
    - https://raw.githubusercontent.com/ROBOTIS-GIT/OpenCR/master/arduino/opencr_release/package_opencr_index.json''' > arduino-cli.yaml

```

Install the board:

```
arduino-cli core install OpenCR:OpenCR
arduino-cli core update-index
arduino-cli lib update-index

```

Build the sketch

```
arduino-cli compile --fqbn OpenCR:OpenCR:OpenCR path_to_ino_file --output-dir ./
```


## How to flash

Use the `opencr_ld`

Eg.

```
./opencr_ld /dev/cu.usbmodemFFFFFFFEFFFF1 115200 /path/to/file.bin 1
```


## Topics used

Found in: `arduino/opencr_arduino/opencr/libraries/turtlebot3/examples/turtlebot3_burger/turtlebot3_core/turtlebot3_core_config.h`

### Subscribers

| Topic Name   |      Type      |
|--------------|:--------------:|
| cmd_vel      | Twist          |
| sound        | Sound          |
| motor_power  | Bool           |
| reset        | Empty          |


### Publishers

| Topic Name       |      Type      |
|------------------|:--------------:|
| sensor_state     | SensorState    |
| firmware_version | VersionInfo    |
| imu              | Imu            |
| cmd_vel_rc100    | Twist          |
| odom             | Odometry       |
| joint_states     | JoinState      |
| battery_state    | BatteryState   |
| magnetic_field   | MagneticField  |