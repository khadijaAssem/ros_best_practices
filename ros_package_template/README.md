# Mission Planning Package

## Description

This module takes the data from visual and sensory perceptions then sends it to controller with the feedback from task failure handler which has the threshold for all missions to be able to identify the mission and sends its ID to scheduler to schedule it depends on its priority, finally it passes its ID to global planning to execute.

### License

The source code is released under a [GNU GENERAL PUBLIC LICENSE](https://github.com/fatma-mohamed-98/VAUV/blob/master/LICENSE).

**Author: vortex-co<br />
Affiliation: [VorteX-Co](https://vortex-co.com/home)<br />
Maintainer: vortex-co, info@vortex-co.com**

The mission planning module package has been tested under [ROS2] Eloquent Elusor on Ubuntu 18.04.

## Table of contents
* [Installation](#Installation)
* [Usage](#Usage)
* [Config files](#Config-files)
* [Launch files](#Launch-files)
* [Hardware](#hardware)


## Installation
### Installation from Packages

Open a terminal, clone the repository, update the dependencies and build the packages:
~~~
	cd ~/ros2_ws/src/ #use your current ros2 workspace folder
	git clone https://github.com/khadijaAssem/VAUV.git
	cd ../
	rosdep install --from-paths src --ignore-src -r -y
	colcon build --symlink-install
	source ~/.bashrc
~~~   

### Building from Source

#### Dependencies

- [Robot Operating System (ROS)](http://wiki.ros.org) (middleware for robotics).

#### Building

To build from source, clone the latest version from this repository into your  workspace and compile the package using
~~~
	cd workspace/src
	git clone https://github.com/khadijaAssem/VAUV.git
	cd ../
	rosdep install --from-paths . --ignore-src
	colcon build --symlink-install
~~~
### Running in Docker

Docker is a great way to run an application with all dependencies and libraries bundles together. 
Make sure to [install Docker](https://docs.docker.com/get-docker/) first. 


## Usage

Use examples liberally, and show the expected output if you can. It's helpful to have inline the smallest example of usage that you can demonstrate, while providing links to more sophisticated examples if they are too long to reasonably include in the README.

Run the main node with
~~~
	ros2 launch ros_package_template ros_package_template.launch.py
~~~
## Config files

## Launch files

## Nodes

### task_manager_node

Reads labeled camera feed ,detects the mission the AUV is currently seeing and determines the next mission to be executed.

#### Subscribed Topics

...

#### Published Topics

...

#### Services

...

#### Parameters

...

### task_controller_node

Maps each mission id to a corresponding finite state machine, Loops on each current state in the FSM until this state changes based on the feedback from the task failure handler until the FSM is finished and another one takes its place.

#### Subscribed Topics

...

#### Published Topics

...

#### Services

...

#### Parameters

...

### Scheduler_Node

Takes task ID, manages the available time for a series of tasks and generates the current task ID.


#### Subscribed Topics

...

#### Published Topics

...

#### Services

...

#### Parameters

...

### Task_Failure_Handler_Node

Takes the current executing task ID and Subscribes on sensor’s topics to get its readings, then publishes feedback on each task.

#### Subscribed Topics	

...

#### Published Topics
	
...

#### Services

...

#### Parameters

...

## Hardware

This package is only for planning, So it doesn't use any sort of hardware.
