# limo_ros
This repository contains ROS packages for limo. 

<img src="limo_description/img/limo.jpg" width="640" height="208" /> 

## Packages


* limo_base: ROS wrapper for limo
* limo_bringup: launch and configuration files to start ROS nodes
* limo_description: URDF model for limo 

## Build from source code
Clone the repository and catkin_make:
```
    $ cd ~/catkin_ws/src
    $ git clone https://github.com/agilexrobotics/limo_ros.git
    $ cd ..
    $ catkin_make
```


## Usage

* Start the base node for limo

    ```
    $ roslaunch limo_bringup limo_start.launch
    ```


* Start the keyboard teleop node

    ```
    $ roslaunch limo_bringup limo_teleop_keyboard.launch
    ```

## ------------------------------------------------------------------
## kante upload


### <1.>YDLidar-SDK문제 해결방법 

#### 1) 적당한 위치에서(예: /root/deps) 설치
mkdir -p /root/deps && cd /root/deps
git clone https://github.com/YDLIDAR/YDLidar-SDK.git
cd YDLidar-SDK && mkdir build && cd build
cmake -DCMAKE_BUILD_TYPE=Release -DBUILD_SHARED_LIBS=ON ..
make -j"$(nproc)"
make install
ldconfig

### 2) 설치 확인
find /usr/local/lib/cmake/ydlidar_sdk -maxdepth 1 -name '*cmake' -print

### 3) 워크스페이스 빌드
cd /root/ws
catkin_make
