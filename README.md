# barrett_hand_sim::Bug Repaired


# ------------------------
Some users downloaded the previous version and catkin_make the files. After they input the roslaunch barrett_hand_gazebo barrett_hand.launch, the fatal error will be reported on the terminal: 

[FATAL] [1555737632.690393621]: No matching hardware interface found for 'hardware_interface/EffortJointInterface

[FATAL] [1555737632.690484449]: Could not initialize robot simulation interface



In order to deal with the problem, we find the instructions from ROS official website http://wiki.ros.org/urdf/XML/Transmission and find the defination of transmission.

The only thing we need to do is to remove the "hardware_interface" in both bh280.urdf.xacro and bh282.urdf.xacro files. Then the barrett model can show on Gazabo successfully!!

New version files have been updated based on the previous version. The bh280.urdf.xacro and bh282.urdf.xacro files have been corrected.

# ------------------------------

Barrett hand simulation package for ROS

Launch the Gazebo simulation:

roslaunch barrett_hand_gazebo barrett_hand.launch

How to switch to available hand models:

Edit file barrett_hand_description/robots/bh_alone.urdf.xacro and change the name of the included file (bh282.urdf.xacro or bh280.urdf.xacro)

Publish topics to control the hand:

rostopic pub /bh_j11_position_controller/command std_msgs/Float64 'desired_angle'

Controller list:

bh_j11_position_controller -> spread DoF

bh_j12_position_controller -> finger 1 grasp

bh_j22_position_controller -> finger 2 grasp

bh_j32_position_controller -> finger 3 grasp
