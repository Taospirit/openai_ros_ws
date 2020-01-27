# openai_ros_ws
## dependences & problems
1. you must have gazebo models files already for the visualization, or to download the models from one of the following:
- [ExBot ROS](https://bitbucket.org/osrf/gazebo_models/downloads/)
- [baiduyun](https://pan.baidu.com/s/1pKaeg0F) passward: cmxc

reference: [csdn-下载gazebo模型](https://blog.csdn.net/qq_40213457/article/details/81021562)

2. Python Error: no model named 're':

you must change the line 6 of `.../src/turtlebot/turtlebot_gazebo/launch/includes/kobuki.launch.xml` to:

      <arg name="urdf_file" default="$(find xacro)/xacro --inorder '$(find turtlebot_description)/robots/$(arg base)_$(arg stacks)_$(arg 3d_sensor).urdf.xacro'" />

3. todo