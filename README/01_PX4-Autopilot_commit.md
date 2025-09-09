## Repo and Commit
## PX4-Autopilot

### 1. Gazebo Harmonic
#### 1.1 px4 သည် Gazebo classic or gz Harmonic in ubuntu 22.04 နဲ့ တွဲသုံးလို့ရတယ်။ ROS2 Humble မှာက gz Fortress ဖြစ်လို့ Harmonic ကို install လုပ်ပေးရမယ်။
```
sudo apt-get update
sudo apt-get install curl lsb-release gnupg
sudo curl https://packages.osrfoundation.org/gazebo.gpg --output /usr/share/keyrings/pkgs-osrf-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/pkgs-osrf-archive-keyring.gpg] https://packages.osrfoundation.org/gazebo/ubuntu-stable $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/gazebo-stable.list > /dev/null
sudo apt-get update
sudo apt-get install gz-harmonic

# if you want to remove Harmonic
# sudo apt remove gz-harmonic && sudo apt autoremove
```
#### 1.2 ပြီးရင် Gazebo Fortress အတွက် ros2_control တွေထည့်ပေးသင့်တယ်။
```
# လောလောဆယ် မလိုသေး။
```

### 2. PX4-AutoPilot
#### 2.1 PX4 ကို install လုပ်ရန်
```
# branch: release/1.15
git clone -b release/1.15 git@github.com:ROM-robotics/PX4-Autopilot.git
cd PX4-Autopilot
git submodule update --init --recursive
make px4_sitl gz_x500 # this should ok
```

#### 2.2 add gz_x500_mono_cam_down with our new position
```
# open Terminal from vscode
cp ./gz_models/4014_gz_x500_mono_cam_down /home/mr_robot/Desktop/Git/Drone/PX4-Autopilot/ROMFS/px4fmu_common/init.d-posix/airframes/
cp -r ./gz_models/x500_mono_cam_down /home/mr_robot/Desktop/Git/Drone/PX4-Autopilot/Tools/simulation/gz/models/
rm -rf /home/mr_robot/Desktop/Git/Drone/PX4-Autopilot/build

make px4_sitl gz_x500_mono_cam_down # First Time Error

cp ./gz_models/4014_gz_x500_mono_cam_down /home/mr_robot/Desktop/Git/Drone/PX4-Autopilot/build/px4_sitl_default/rootfs/etc/init.d-posix/airframes/

make px4_sitl gz_x500_mono_cam_down # Finally ok :P
```

#### 2.3 baylands
```
make px4_sitl gz_x500_mono_cam_down_baylands # Done
```

#### 2.4 check submodule's commits ( OPTIONAL )
```
#### BEFORE SUBMODULE UPDATE
mr_robot@desktop:~/Desktop/Git/Drone/PX4-Autopilot$ git submodule status
-f47ce7b5fbbb3aa43d33d2be1f6cd3746b13d5bf Tools/simulation/flightgear/flightgear_bridge
-da7206e057703cc645770f02437013358b71e1c0 Tools/simulation/gazebo-classic/sitl_gazebo-classic
-d754381a1cecdd7f17050acd72bf5bf1327bced6 Tools/simulation/gz
-66b764ada522893c05224950aa6268c809f8e48a Tools/simulation/jmavsim/jMAVSim
-68de2cc63ded9a0d6641d45e9eb3ed2b43454cba Tools/simulation/jsbsim/jsbsim_bridge
-ca16e99074641a10d153961291243ede7720c2e2 boards/modalai/voxl2/libfc-sensor-api
-e37940d8535f603a16b8f6f21c21edaf584218aa platforms/nuttx/NuttX/apps
-5d74bc138955e6f010a38e0f87f34e9a9019aecc platforms/nuttx/NuttX/nuttx
-36a01e428b110ff84c8babe5b65667b5e3037d5e src/drivers/cyphal/legacy_data_types
-5c69d451ab0787a81dcb615692d707f2a286f5e5 src/drivers/cyphal/libcanard
-d0bd6516dac8ff61287fe49a9f2c75e7d4dc1b8e src/drivers/cyphal/public_regulated_data_types
-ad769ff53d683d06937c92bae58377d65893967b src/drivers/gps/devices
-9a0fd624c448cad5633720676233f74846387a9f src/drivers/uavcan/libuavcan
-314887ca403c2fb0a0316add22672102936ed36c src/lib/cdrstream/cyclonedds
-7790c70717e09c003711f6f65015666c223fc283 src/lib/cdrstream/rosidl
-673f5ce29015a9bba3c96792920a10601b5b0718 src/lib/crypto/libtomcrypt
-fd73d7630b9d3ed5a79d613ff680a549e9780de7 src/lib/crypto/libtommath
-baca5d31259c598540e4d1284bc8d8f793abf83a src/lib/crypto/monocypher
-59f7f5c0ec2e76fadbc1dc40cc0705d614472edc src/lib/events/libevents
-052e6de72f67f1777198bce98f3de62f7f3c16a0 src/lib/heatshrink/heatshrink
-a3558d6b335d930fc01816fd168d16b3f38ed434 src/modules/mavlink/mavlink
-711aef423edd1820347b866d1e4164832df35d04 src/modules/uxrce_dds_client/Micro-XRCE-DDS-Client
-22bbfc215092a051341c234fdcf68f5baa267dec src/modules/zenoh/zenoh-pico

```

```
make distclean
git submodule update --init --recursive
```
```
mr_robot@desktop:~/Desktop/Git/Drone/PX4-Autopilot$ git submodule status
 f47ce7b5fbbb3aa43d33d2be1f6cd3746b13d5bf Tools/simulation/flightgear/flightgear_bridge (heads/master)
 da7206e057703cc645770f02437013358b71e1c0 Tools/simulation/gazebo-classic/sitl_gazebo-classic (da7206e)
 d754381a1cecdd7f17050acd72bf5bf1327bced6 Tools/simulation/gz (d754381)
 66b764ada522893c05224950aa6268c809f8e48a Tools/simulation/jmavsim/jMAVSim (heads/main)
 68de2cc63ded9a0d6641d45e9eb3ed2b43454cba Tools/simulation/jsbsim/jsbsim_bridge (68de2cc)
 ca16e99074641a10d153961291243ede7720c2e2 boards/modalai/voxl2/libfc-sensor-api (ca16e99)
 e37940d8535f603a16b8f6f21c21edaf584218aa platforms/nuttx/NuttX/apps (nuttx-11.0.0-5-ge37940d85)
 5d74bc138955e6f010a38e0f87f34e9a9019aecc platforms/nuttx/NuttX/nuttx (nuttx-8.2-10661-g5d74bc1389)
 36a01e428b110ff84c8babe5b65667b5e3037d5e src/drivers/cyphal/legacy_data_types (remotes/origin/legacy)
 5c69d451ab0787a81dcb615692d707f2a286f5e5 src/drivers/cyphal/libcanard (3.0.1-1-g5c69d45)
 d0bd6516dac8ff61287fe49a9f2c75e7d4dc1b8e src/drivers/cyphal/public_regulated_data_types (d0bd651)
 ad769ff53d683d06937c92bae58377d65893967b src/drivers/gps/devices (remotes/origin/release/1.15)
 9a0fd624c448cad5633720676233f74846387a9f src/drivers/uavcan/libuavcan (remotes/origin/python3.10-fix)
 314887ca403c2fb0a0316add22672102936ed36c src/lib/cdrstream/cyclonedds (314887ca)
 7790c70717e09c003711f6f65015666c223fc283 src/lib/cdrstream/rosidl (7790c70)
 673f5ce29015a9bba3c96792920a10601b5b0718 src/lib/crypto/libtomcrypt (1.17-2055-g673f5ce2)
 fd73d7630b9d3ed5a79d613ff680a549e9780de7 src/lib/crypto/libtommath (v1.2.0-247-gfd73d76)
 baca5d31259c598540e4d1284bc8d8f793abf83a src/lib/crypto/monocypher (3.1.2)
 59f7f5c0ec2e76fadbc1dc40cc0705d614472edc src/lib/events/libevents (59f7f5c)
 052e6de72f67f1777198bce98f3de62f7f3c16a0 src/lib/heatshrink/heatshrink (heads/main)
 a3558d6b335d930fc01816fd168d16b3f38ed434 src/modules/mavlink/mavlink (1.0.12-657-ga3558d6b)
 711aef423edd1820347b866d1e4164832df35d04 src/modules/uxrce_dds_client/Micro-XRCE-DDS-Client (heads/px4)
 22bbfc215092a051341c234fdcf68f5baa267dec src/modules/zenoh/zenoh-pico (0.5.0-beta.9-612-g22bbfc21)

```