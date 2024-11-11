
# Turtlebot3 Automation

This project is designed for automatic navigation using the Turtlebot3 robot in a Gazebo world. The robot will navigate through a predefined map, avoiding obstacles, and reach four specific locations.

## Prerequisites

Before running the project, ensure you have the following installed:

1. **Ubuntu 22.04**  
2. **Gazebo 11**  
3. **ROS 2 Humble**

### Installation

#### 1. Install Gazebo 11
Gazebo 11 can be installed on Ubuntu using the following commands:

```bash
sudo apt update
sudo apt install gazebo11 libgazebo11-dev
```

#### 2. Install ROS 2 Humble
Follow the [ROS 2 Humble installation guide](https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debians.html) to install ROS 2 on your system. Make sure to source your ROS 2 setup file after installation:

```bash
source /opt/ros/humble/setup.bash
```

#### 3. Install TurtleBot3 Dependencies
Once ROS 2 is installed, install Turtlebot3 packages:

```bash
sudo apt update
sudo apt install ros-humble-turtlebot3-*
```

### Workspace Setup


1. Clone the TurtleBot3 repository:

```bash
git clone <your-repository-url> .
```

2. Import the required repositories:

```bash
vcs import . < turtlebot3.repos
```

3. Build the workspace:

```bash
colcon build --symlink-install
```

4. Source the workspace:

```bash
source ./install/setup.bash

. /usr/share/gazebo/setup.sh
```

5. Export TurtleBot3 model:

```bash
export GAZEBO_MODEL_PATH=$GAZEBO_MODEL_PATH:~/turtlebot3_ws/src/turtlebot3/turtlebot3_simulations/turtlebot3_gazebo/models

export TURTLEBOT3_MODEL=waffle_pi
```

6. Launch turtlebot3 simulation infrastructure

```bash
ros2 launch tb3_sim turtlebot3_world.launch.py
```

7. Open new terminal, Launch nav2 infrastructure (nav2 + amcl initial pose)

```bash
source ./install/setup.bash
. /usr/share/gazebo/setup.sh
ros2 launch tb3_sim nav2.launch.py
```

8. Open new terminal, Launch autonomy behavior for demo

```bash
source ./install/setup.bash
. /usr/share/gazebo/setup.sh
ros2 launch tb3_autonomy autonomy.launch.py
```
This starts our demonstration where TurtleBot moves between 4 different locations in the world simulation (set in tb3_sim/config/sim_house_locations.yaml)
##Move the Turtlebot3 to Locations:##
   - The robot will automatically navigate through the four predefined locations in the map. Ensure that the map and navigation goals are configured in the navigation launch files.






