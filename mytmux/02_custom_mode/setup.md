git clone https://github.com/ARK-Electronics/px4_ros2_example_ws
cd px4_ros2_examples_ws
git submodule update --init --recursive
colcon build
colcon build --packages-select custom_node
source install/setup.bash
cd your/PX4-Autopilot/
make px4_sitl_default gz_x500
MicroXRCEAgent udp4 -p 8888
./QGroundControl.AppImage
cd px4_ros2_examples_ws
source install/setup.bash
ros2 run custom_mode custom_mode
OR
ros2 launch custom_mode custom_mode.launch.py
OR
ros2 launch custom_mode custom_mode.launch.py trajectory_type:=spiral
ros2 launch custom_mode custom_mode.launch.py trajectory_type:=figure8
You Can start from QGC
OR
ros2 run custom_mode custom_mode --ros-args -p trajectory_type:=figure8
