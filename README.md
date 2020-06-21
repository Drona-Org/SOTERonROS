# SOTER on ROS

## Table of Contents
1. [ Setup. ](#Setup)
2. [ Case Studies. ](#examples)

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

Videos of case studies can be found at [label](https://drona-org.github.io/Drona/)