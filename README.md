TURUTLEBOT4 PRAKTIK UTS

# TurtleBot4 Setup & Run Guide

This guide explains how to set up your workspace, configure IP
connection, build the project, and run TurtleBot4 with navigation,
localization, RViz visualization, and custom packages.

------------------------------------------------------------------------

## 0. Configure Manual IP Connection (PC → TurtleBot4)

Set your PC's network adapter manually:

-   **IP Address:** 192.168.185.5\
-   **Subnet Mask:** 255.255.255.0\
-   **Gateway:** 192.168.185.3

This puts your PC on the same network as TurtleBot4.

------------------------------------------------------------------------

## 1. Create Workspace & Build

### Create a workspace:

``` bash
mkdir -p ~/klp1/src
cd ~/klp1/src
```

### Clone the GitHub repository:

``` bash
git clone https://github.com/antonius1224/UTS-RE702-Antonius-Heri-Natanael-4222201059.git
```

### Build using colcon:

``` bash
cd ~/klp1
colcon build
```

### Source the workspace:

``` bash
source install/setup.bash
```

------------------------------------------------------------------------

## 2. Visualization (RViz)

### **Option A: Run RViz remotely via SSH (only if needed)**

Connect with X forwarding:

``` bash
ssh -X ubuntu@192.168.185.3
```

Launch navigation RViz view:

``` bash
ros2 launch turtlebot4_viz view_navigation.launch.py
```

### **Option B: Run RViz locally (recommended)**

If RViz is installed on your laptop:

``` bash
ros2 launch turtlebot4_viz view_robot.launch.py
```

------------------------------------------------------------------------

## 3. Localization

(Open a new terminal) Connect to the robot:

``` bash
ssh ubuntu@192.168.185.3
```

Source workspace:

``` bash
cd ~/klp1
source install/setup.bash
```

Run localization:

``` bash
ros2 launch klppoint localization.launch.py map:=src/klp1/maps/mapklp1.yaml
```

In RViz:\
➡️ Use **2D Pose Estimate** to set the initial pose.

------------------------------------------------------------------------

## 4. Run Your Navigation Package

(Open a new terminal):

``` bash
ssh ubuntu@192.168.185.3
```

Enter workspace:

``` bash
cd ~/klp1
source install/setup.bash
```

Launch your navigation node:

``` bash
ros2 launch klppoint run_nav.launch.py
```

Then test navigation using **Nav2 Goal** in RViz.

------------------------------------------------------------------------

## 5. Run Additional Nodes

(Open a new terminal):

``` bash
ssh ubuntu@192.168.185.3
```

Source workspace:

``` bash
cd ~/klp1
source install/setup.bash
```

Run your custom node:

``` bash
ros2 run klppoint uts_nav launch.py
```

------------------------------------------------------------------------

## You're Ready!


