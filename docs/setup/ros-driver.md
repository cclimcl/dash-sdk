# ROS Driver
As mentioned, the ROS driver is a ROS node handles computational calls and sends control commands to the d.ASH server. It acts as an intermediate layer for ROS messages to be communicated with d.ASH server and unreal-clients through [gRPC](https://grpc.io/docs/what-is-grpc/introduction/).



### 4.1 ^^Update External Libraries^^ 

First, let's update the external libs, more specifically the `grpc_layer`, by executing the following commands:

```
$ git submodule update --init --recursive
$ git submodule update --remote --merge
```


### 4.2 ^^Prerequisite^^
Now, we need to use vcpkg to install following packages to set up the ROS Driver:

```
$ cd ~/vcpkg
$ ./vcpkg install grpc:x64-linux
$ ./vcpkg install nlohmann-json:x64-linux
$ ./vcpkg install libsodium:x64-linux
$ ./vcpkg install msgpack:x64-linux
$ ./vcpkg install eigen3:x64-linux
$ ./vcpkg install opencv[world]:x64-linux
$ ./vcpkg install spdlog:x64-linux
$ ./vcpkg install pcl:x64-linux
```
Then, using apt-get to install  following packages to set up the ROS Driver:

```
$ sudo apt install ros-melodic-hector-trajectory-server ros-melodic-realsense2-camera ros-melodic-velodyne ros-melodic-joy ros-melodic-octomap ros-melodic-dynamic-edt-3d ros-melodic-tf2 ros-melodic-serial* libgoogle-glog-dev git libssl-dev libusb-1.0-0-dev pkg-config libgtk-3-dev libglfw3-dev libgl1-mesa-dev libglu1-mesa-dev
$ sudo add-apt-repository ppa:joseluisblancoc/gtsam-develop
$ sudo apt update
$ sudo apt install libgtsam-dev
$ sudo apt-key adv --keyserver keys.gnupg.net --recv-key 6F3EFCDE
$ sudo apt update
$ sudo apt install librealsense2*
$ sudo apt install libudev-dev
$ sudo apt-get install libsecret-1-dev
```


### 4.3 ^^Configuration^^
Now, we need to place the `pyConfig.json`  into the folder `~/.data`. Similarly, make sure security files are stored in the folder `~/.data/security/`.

To build the ROS Driver, execute the following commands:
``` 
$ mkdir build
$ cd build
$ cmake -DBUILD_SHARED_LIBS=On .. -DCMAKE_TOOLCHAIN_FILE=/home/spot/vcpkg/scripts/buildsystems/vcpkg.cmake -DCMAKE_BUILD_TYPE=Release   (change path accordingly)
$ make -j12
```
  
### 4.4 ^^Running the Driver^^
By default, token authentication is enabled. To disable it, add `auth: false` to the `pyConfig.json`.

To run without token authentication:
```
$ ./ros_msg_interface <!path_to_pyConfig.json>
```

Otherwise, if token authentication is enabled, run
```
$ ./ros_msg_interface <!path_to_pyConfig.json> <!TOKEN_HERE>
```

### 4.5 ^^Building the d.ASH Server on Linux^^

Now, you will need to compile the py_realsense_node C++ library by executing the following:
```
$ cmake -DBUILD_SHARED_LIBS=On .. -DCMAKE_TOOLCHAIN_FILE=/home/spot/vcpkg/scripts/buildsystems/vcpkg.cmake -DCMAKE_BUILD_TYPE=RELEASE
$ make sure add set(CMAKE_CXX_STANDARD 14) in CMakelists
$ make
```
Then, you will need to compile the py_server C++ library by executing the following:
```
$ cmake -DBUILD_SHARED_LIBS=On .. -DCMAKE_TOOLCHAIN_FILE=/home/spot/vcpkg/scripts/buildsystems/vcpkg.cmake -DCMAKE_BUILD_TYPE=RelWithDebInfo
$ make sure add set(CMAKE_CXX_STANDARD 14) in CMakelists
$ make
```

Finally, add the python path correctly by ensuring:

- In robotHAL.py, ensure you are importing the compiled py_server C++ library.
- In realSenseCameras.py, ensure you have compiled the py_realsense_node C++ library. 