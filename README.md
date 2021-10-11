# waypoint-based-3D-navigation-in-ros
This repository contains code for 3D waypoint based navigation in ROS.

<img src="img/header.jpg" alt="Header" width="100%"/>

The repository is meant for leveraging system development and robot deployment for ground-based autonomous navigation and exploration. Containing a variety of simulation environments, autonomous navigation modules such as collision avoidance, terrain traversability analysis, waypoint following, etc, and a set of visualization tools, users can develop autonomous navigation systems and later on port those systems onto real robots for deployment.

## Quick Start
The repository has been tested in Ubuntu 18.04 with ROS Melodic and Ubuntu 20.04 with ROS Noetic. Install dependencies with command lines below.
```
sudo apt update
sudo apt install libusb-dev
```
Clone the open-source repository.
```
git clone https://github.com/HongbiaoZ/autonomous_exploration_development_environment.git
```
In a terminal, go to the folder and checkout the branch that matches the computer setup. Replace 'distribution' with 'melodic' or 'noetic'. Then, compile.
```
cd autonomous_exploration_development_environment
git checkout distribution
catkin_make
```
Run a script to download simulation environments (~500MB). This may take several minutes. If the script does not start the download, users can download the simulation environments and unzip the files to 'src/vehicle_simulator/meshes'.
```
./src/vehicle_simulator/mesh/download_environments.sh
```
Source the ROS workspace and launch the system.
```
source devel/setup.sh
roslaunch vehicle_simulator system_garage.launch
```
Now, users can send a waypoint by clicking the 'Waypoint' button in RVIZ and then clicking a point to set the waypoint. The vehicle will navigate to the waypoint avoiding obstacles along the way. Note that the waypoint should be reachable and in the vicinity of the vehicle.

Alternatively, users can run a ROS node to send a series of waypoints. In another terminal, go to the folder and source the ROS workspace, then run the ROS node with the command line below. The ROS node sends navigation boundary and speed as well. The vehicle will navigate inside the boundary while following the waypoints.
```
roslaunch waypoint_example waypoint_example_garage.launch
```
