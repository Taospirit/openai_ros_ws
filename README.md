# openai_ros_ws
## dependences & install
1. some dpkgs to install:
```shell
sudo apt install -y ros-kinetic-pid ros-kinetic-joy ros-kinetic-ecl ros-kinetic-yocs-msgs ros-kinetic-ar-track-alvar
```
2. you must have gazebo models files already for the visualization, or to download the models from one of the following source, then move unzip files to `~/.gazebo/models`.
- [ExBot ROS](https://bitbucket.org/osrf/gazebo_models/downloads/)
- [baiduyun](https://pan.baidu.com/s/1pKaeg0F) passward: cmxc

reference: [csdn-下载gazebo模型](https://blog.csdn.net/qq_40213457/article/details/81021562)
3. install tf2_py support for Python3: 
```shell
mkdir -p src/tf2 && cd src/tf2
git clone https://github.com/ros/geometry
git clone https://github.com/ros/geometry2

cd ../..
catkin_make --cmake-args \
            -DCMAKE_BUILD_TYPE=Release \
            -DPYTHON_EXECUTABLE=/usr/bin/python3 \
            -DPYTHON_INCLUDE_DIR=/usr/include/python3.5m \
            -DPYTHON_LIBRARY=/usr/lib/x86_64-linux-gnu/libpython3.5m.so
```
4. if use bash

you must change the line 75 of `.../openai_ros_ws/src/openai_ros/openai_ros/src/openai_ros/openai_ros_common.py` to 

      source_env_command = "source "+ros_ws_abspath+"/devel/setup.bash;"

and the line 80 to:

      p = subprocess.Popen(command, shell=True)


## problems
### 1. Python Error: `no model named 're'`.
you must change the line 6 of `.../src/turtlebot/turtlebot_gazebo/launch/includes/kobuki.launch.xml` to

      <arg name="urdf_file" default="$(find xacro)/xacro --inorder '$(find turtlebot_description)/robots/$(arg base)_$(arg stacks)_$(arg 3d_sensor).urdf.xacro'" />

### 2. 
