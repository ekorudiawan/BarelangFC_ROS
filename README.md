# BarelangFC ROS Motion Interface

**How to setup and run**
1. Install ROS Kinetic, follow this link http://wiki.ros.org/kinetic/Installation/Ubuntu
2. Clone the workspace
    ```bash
    cd ~
    git clone https://github.com/ekorudiawan/BarelangFC_ROS.git
    cd BarelangFC_ROS
    catkin_make 
    source devel/setup.bash
    ```
3. Run ROS motion interface
    ```bash
    roslaunch barelang_motion_bridge barelang_motion_bridge.launch
    ```
    Robot should activate, but not standing up
4. Controlling the robot through ROS interface
    
    Make the robot stand up
    ```bash
    rostopic pub /motion/state std_msgs/String "data: 'stand'"
    ```
    Make the robot sit down
    ```bash
    rostopic pub /motion/state std_msgs/String "data: 'sit'" 
    ```

    Start Walking
    ```bash
    rostopic pub /motion/state std_msgs/String "data: 'start'"
    ```

    Stop Walking
    ```bash
    rostopic pub /motion/state std_msgs/String "data: 'stop'"
    ```

    Control motion velocity (only executed after calling start walking).

    vx = linear x, vy = linear y, va = linear z
    ```bash
    rostopic pub /motion/cmd_vel geometry_msgs/Twist "linear:
    x: 0.0
    y: 0.0
    z: 0.0
    angular:
    x: 0.0
    y: 0.0
    z: 0.0"
    ```