# laser_assembler
Install the necessary package:

sudo apt-get install ros-indigo-laser-assembler ros-indigo-laser-geometry

Check out the RRbot code:

git clone https://github.com/ros-simulation/gazebo_ros_demos
Then change the branch into indigo-devel

git checkout indigo-devel
Add the path to ROS_PACKAGE_PATH

source /opt/ros/indigo/setup.bash
export ROS_PACKAGE_PATH=/home/behnam/gazebo_ros_demos/:$ROS_PACKAGE_PATH

roslaunch rrbot_gazebo rrbot_world.launch

roslaunch rrbot_control rrbot_control.launch

rosrun rqt_gui rqt_gui


set the second joint value

(/rrbot/joint2_position_controller/command)  into (pi/4)+(1*pi/4)*sin(i/40)*sin(i/40)

and the frequency into 50 Hz

Finally, run:

rosrun laser_assembler_service_caller


Alternatively, you can also use the following launch file to call the laser assembler via rqt_gui:

<launch>
    <node type="laser_scan_assembler" pkg="laser_assembler" name="my_assembler">
        <remap from="scan" to="/rrbot/laser/scan"/>
        <param name="max_clouds" type="int" value="400" />
        <param name="fixed_frame" type="string" value="world" />
    </node>
</launch>

