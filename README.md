# ROS - Visual Servoing IBVS with Blobs Detection

**Table-of-contents**

* [Dependencies](#dependencies)
* [Process](#process)
* [Execution](#execution)

More description is given in the subsections.

## Dependencies

The following project has been tested with **Ubuntu 14.04 LTS**.

Since this project concerns ROS Indigo, following libraries are needed:

* ROS Indigo - `sudo apt-get install ros-indigo-desktop-full`
* Gazebo Simulation - `sudo apt-get install ros-indigo-gazebo-ros-pkgs ros-indigo-gazebo-ros-control`
* Turtlebot for Gazebo - `sudo apt-get install ros-indigo-turtlebot_gazebo`

The development part has been performed using CPP and ViSP:

* ROS Indigo ViSP - `sudo apt-get install ros-indigo-visp-*`
* ViSP - `sudo apt-get install libvisp-dev libvisp-doc visp-images-data`

## Getting your marker in the Gazebo world:
Paste the 'marker0' folder in 'gazeboResources' into your gazebo resources directory.

Usually, this is a hidden folder in your 'home' directory, named '.gazebo'. Paste the 'marker0' folder inside '.gazebo/models/'. In your Gazebo, you'll now be able to 'insert' marker0, check the insert pane!

The 'qr.world' file available in 'world' folder contains a Gazebo world with a pattern containing 5 dots. 


## Process

The following code performs multiple operations to compute **visual servoing task** using **ROS Indigo** and a **Turlebot**.

* Extraction of image from the Kinect ( and dependant topic) .
* Detection of the target using a predefined template.
* Estimate the position of the target in the world coordinate frame -  **PBVS** .
* Compute velocities according to the error differentiating the actual coordinates of **Turtlebot** and desired coordinates.
* Stop the velocity publishing and computation when reaching a distance contained in a threshold scale.

##Pseudocode

![Base QR](ressources/pseudocodepython.png)

## Execution

### Standard commands

Running the minimal launch and the 3Dsensor launch from ros.

* minimal - `roslaunch turtlebot-bringup minimal.launch`
* 3dsensor - `roslaunch turtlebot-bringup 3dsensor.launch`

### PBVS Task

* PBVS - `roslaunch #NameOfPackage# qr_pbvs.launch`

* PBVS Simulation - `roslaunch #NameOfPackage# turtlebot_world.launch world_file:='/world/NameofWorld.world' `

## Provided in the repository

### launch

This folder contains all the launch files to run the code in real world or Gazebo.

### scripts

This folder contains all the cpp files to run the code in real world or Gazebo.

### model

This folder contains all the files concerning the template to track.

### world

This folder contains the Gazebo world to launch the code under simulation.

## Materials

![Base QR](ressources/pseudocodepython.png)
