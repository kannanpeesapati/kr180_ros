# Motion Planning KUKA KR180 R2900 with MoveIt

## 1. Details
1.  Install the ROS-I Repo : **apt-get install ros-melodic-industrial-core**
2.  Install kuka_experimental repo and rewrite some folders with the zip data : **git clone https://github.com/ros-industrial/kuka_experimental.git**
3.  Download the git and rewrite the zip data to kuka-experimental folder
3. Check the ros dependency by **rosdep install --from-paths src --ignore-src**
4. Compile the src by **catkin_make** and **source devel/setup.bash**
5. Install joint-trajectory controller:  sudo apt-get install ros-melodic-joint-trajectory-controller


## 2. Running
Please always run roscore
### 1. Simulation
**roslaunch kr180_moveit_test_test real.launch sim:=false robot_ip:=127.0.0.1** 

**roslaunch kuka_rsi_simulator kuka_rsi_simulator.launch rsi_hw_iface_ip:=127.0.0.1 rsi_hw_iface_port:=49152**

### 2. Real Environment
**roslaunch kr180_moveit_test_test real.launch sim:=false robot_ip:=192.168.1.5**

## 3. RQT

run rqt in terminal and set some plugins
1. choose Plugins > Topics > Topic Monitor

this is used to see all available topics to be observed.
Important topic ist /joint_trajectory_action/feedback

2. choose Plugins > Visualization > Plot

Put this command to plot the position and PID tuning in config>controller.yaml

/joint_trajectory_action/feedback/feedback/actual/positions[n]
/joint_trajectory_action/feedback/feedback/desired/positions[n]
/joint_trajectory_action/feedback/feedback/error/positions[n]

n is the number of joint and starts from 0.