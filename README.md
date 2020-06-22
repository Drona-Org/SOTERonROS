# SOTER on ROS

SOTER on ROS is a run-time assurance framework for building safe distributed mobile robotic (DMR) systems on top of the Robot Operating System (ROS). In SOTER, components of a DMR system are defined as runtime assurance (RTA) modules implementing a Simplex architecture. An RTA module based on Simplex consists of two controllers, an advanced controller (AC) and a safe controller, and a decision module that implements a switching logic between the AC and SC. 

The framework borrows from the Drona framework and is similarly comprised of three layers. The application layer, the robot software stack, and the robot SDK. The application layer implements an application related task planner that is responsible for computing application related tasks and distributing them amongst the robots for execution. The software stack of each robot consists of an interface to establish the communication with task planner, a motion planner, and a plan executor, in addition to a set of decision modules. The motion planner and the plan executor are implemented as RTA modules that are linked to one of the decision modules and to implementations of their safe and advanced controllers. 


## Table of Contents
1. [ Setup ](#Setup)
2. [ Case Studies ](#examples)

<a name="Setup"></a>
## Setup
- Install ROS and create a catkin workspace for your ROS packages: http://wiki.ros.org/catkin/Tutorials/create_a_workspace
- Clone the `multi_robot` ROS package into the `src` directory of your `catkin_ws`. 
    - `cd ~/catkin_ws/src`
    - `git clone git@github.com:sumukhshiv/multi_robot.git`
- Clone this repo `src` directory
    - `git clone git@github.com:Drona-Org/SOTERonROS.git`
- To run the Drone Surveillance Sample run the following commands:
    - New terminal window: 
    ```
        roscore
    ```
    - New terminal window
    ``` 
        cd ~/catkin_ws
        catkin_make
        . devel/setup.sh
        roslaunch multi_robot drone.launch
    ```
    - New terminal window
    ``` 
        cd ~/catkin_ws/src/SOTERonROS/PSrc/SoftwareStack/
        pc ../Applications/DroneExploration/MainDroneTaskPlanner.p RTAMotionPlanner.p RTAPlanExecutor.p RTADecisionModuleDrone.p Robot.p -outputDir:../Applications/DroneExploration
    ```
    - New Terminal Window
    ``` 
        cd ~/catkin_ws
        catkin_make
        . devel/setup.sh
        rosrun SOTERonROS soter_test
    ```

<a name="examples"></a>
## Case Studies

Videos of case studies can be found at [https://drona-org.github.io/Drona/.](https://drona-org.github.io/Drona/)
