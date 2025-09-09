### Repo and Commit

#### Drone Road Following
```
# branch: rom_release/1.15
git clone -b rom_release/1.15 git@github.com:ROM-robotics/Drone_Road_Following.git

# or checkout 
# git checkout 4daefca613e07a8e97172df9a5184a947f3f1af3
```

#### Micro XRCE DDS Agent
```
# tag: v3.0.1, branch: master
git clone https://github.com/eProsima/Micro-XRCE-DDS-Agent.git

# or checkout 
# git checkout 155cfaaf8b7abac2e85d4a62d3649b09ace0be55
```

#### px4_ros2_examples_ws
```
# branch: rom_custom_mode
git clone git@github.com:ROM-robotics/px4_ros2_examples_ws.git -b rom_custom_mode 

# or checkout 
# git checkout fb3740019b2e138297feadbf72fb0ad9d63dfcb8
```

```
# check submodules in px4_ros2_examples_ws

git submodule status

# 303d0981edb217bbb2d77e1d17d31266f60aa602 rom_flight_control (rom_custom_mode-11-g303d098)
# b2c044041041795f1620b46491adede658a7ce67 src/px4-ros2-interface-lib (heads/main-2-gb2c0440)
# f31cef224bb09220b43daf031b96e7b0914c0d81 src/px4_msgs (f31cef2)
```