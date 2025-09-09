### 1 Deploy on Host

#### 1.1 linking 
```
ln -s ~/Desktop/Git/Drone/Drone_Road_Following ~
ln -s ~/Desktop/Git/Drone/PX4-Autopilot ~
ln -s ~/Desktop/Git/Drone/px4_ros2_examples_ws ~
```

#### 1.2 building
```
cd ~/px4_ros2_examples_ws/
bb
source ~/px4_ros2_examples_ws/install/setup.bash
```

### 2 Container

#### 2.1 How to run
```
docker pull romrobotics/humble_production:road_follow_drone
./run.sh
```