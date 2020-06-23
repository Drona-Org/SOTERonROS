# SOTER on ROS

SOTER on ROS is a run-time assurance framework for building safe distributed mobile robotic (DMR) systems on top of the Robot Operating System (ROS). In SOTER, components of a DMR system are defined as runtime assurance (RTA) modules implementing a Simplex architecture. An RTA module based on Simplex consists of two controllers, an advanced controller (AC) and a safe controller, and a decision module that implements a switching logic between the AC and SC. 

The framework borrows from the Drona framework and is similarly comprised of three layers. The application layer, the robot software stack, and the robot SDK. The application layer implements an application related task planner that is responsible for computing application related tasks and distributing them amongst the robots for execution. The software stack of each robot consists of an interface to establish the communication with task planner, a motion planner, and a plan executor, in addition to a set of decision modules. The motion planner and the plan executor are implemented as RTA modules that are linked to one of the decision modules and to implementations of their safe and advanced controllers. 

The implementation of the software stack, examples of task planners, and interface of C++ modules can be found in the `PSrc` directory. The `PSrc` directory contains `Applications`, which contains all application specific files, `SoftwareStack`, which contains implementations of the Robot P machine, Motion Planner, Plan Executor, and Decision Modules, and `RobotSDK`, which contains the Cpp modules and foreign function implementations. 


## Table of Contents
1. [ Setup ](#Setup)
2. [ Case Studies ](#examples)

<a name="Setup"></a>
## Setup
- Install ROS and create a catkin workspace for your ROS packages: http://wiki.ros.org/catkin/Tutorials/create_a_workspace
    - `git clone git@github.com:Drona-Org/SOTERonROS.git`
- Install P: https://github.com/p-org/P
- To run a SOTER on ROS application run the following commands:
    - Launch roscore in a new terminal window: 
    ```
        roscore
    ```
    - Launch your simulator in a new terminal window:
    ``` 
        cd ~/catkin_ws
        catkin_make
        . devel/setup.sh
        roslaunch <simulation package> <simulator launch file>
    ```
    - Compile the P source code in a new terminal window:
    ``` 
        cd ~/catkin_ws/src/SOTERonROS/PSrc/SoftwareStack/
        pc ../Applications/<TaskPlanner.p> <Robot.p> <MotionPlanner.p> <PlanExecutor.p>  <DecisionModule.p> -outputDir:../application/path
    ```
    - Execute your application in a new terminal window:
    ``` 
        cd ~/catkin_ws
        catkin_make
        . devel/setup.sh
        rosrun SOTERonROS <application_executable>
    ```
- Example:
    - In the Drone Surveillance Case Study, we use the following packages:
        - OMPL: https://ompl.kavrakilab.org/installation.html
        - SJTU Drone: https://github.com/tahsinkose/sjtu-drone
        - `multi_robot` ROS/Gazebo simulation: https://github.com/sumukhshiv/multi_robot
    - Launching Simulator: `roslaunch multi_robot drone.launch`
    - Compiling P Code: `pc ../Applications/DroneExploration/MainDroneTaskPlanner.p RTAMotionPlanner.p RTAPlanExecutor.p RTADecisionModuleDrone.p Robot.p -outputDir:../Applications/DroneExploration`
    - Execuring application: `rosrun SOTERonROS soter_test`

<a name="examples"></a>
## Case Studies

In these videos, we implement SOTER on top of the Robot Operating System (ROS) and add monitor support. We have implemented a Drone Surveillance Protocol case study and a Robot Delivery case study. In the Drone Surveillance experiement, we have a single monitor that ensures the drone does not crash into the walls of the workspace. In the Robot Delivery experiement, we implement 3 runtime assurance modules: Battery safety, Geo-fencing, and Collision Avoidance. In each case, we have implemented an Advanced Controller, Safe Controller, and Decision Module to ensure that the robots guarantee safety. The robots are survelling a 5x5 workspace with static obstacles. 

### Drone Case Study
[![Drone Case Study](https://img.youtube.com/vi/fXJ1Iwt2Ryw/0.jpg)](https://youtu.be/fXJ1Iwt2Ryw?list=PLaL5L3Z-dA6KVlPkXRb-4-TfNMPWumeUA)

### Robot Delivery Case Study - Battery
[![Robot Delivery Case Study - Battery](https://img.youtube.com/vi/ytpT68LATnc/0.jpg)](https://youtu.be/ytpT68LATnc?list=PLaL5L3Z-dA6KVlPkXRb-4-TfNMPWumeUA)

### Robot Delivery Case Study - Geo-Fence
[![Robot Delivery Case Study - Geo-Fence](https://img.youtube.com/vi/T9GiCFxVE9Q/0.jpg)](https://youtu.be/T9GiCFxVE9Q?list=PLaL5L3Z-dA6KVlPkXRb-4-TfNMPWumeUA)

[![Robot Delivery Case Study - Geo-Fence 2](https://img.youtube.com/vi/cogQpzTV6xE/0.jpg)](https://youtu.be/cogQpzTV6xE?list=PLaL5L3Z-dA6KVlPkXRb-4-TfNMPWumeUA)

### Robot Delivery Case Study - Collision Avoidance
[![Robot Delivery Case Study - Collision Avoidance](https://img.youtube.com/vi/fccxB6r-YGs/0.jpg)](https://youtu.be/fccxB6r-YGs?list=PLaL5L3Z-dA6KVlPkXRb-4-TfNMPWumeUA)

[![Robot Delivery Case Study - Collision Avoidance](https://img.youtube.com/vi/5hQ4E14JK30/0.jpg)](https://youtu.be/5hQ4E14JK30?list=PLaL5L3Z-dA6KVlPkXRb-4-TfNMPWumeUA)

### Robot Delivery Case Study - Composing Monitors
[![Robot Delivery Case Study - Composing Monitors](https://img.youtube.com/vi/j_0WC9fo6W4/0.jpg)](https://youtu.be/j_0WC9fo6W4?list=PLaL5L3Z-dA6KVlPkXRb-4-TfNMPWumeUA)
