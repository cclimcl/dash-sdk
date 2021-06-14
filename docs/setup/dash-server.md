# Setting Up d.ASH Server

As mentioned previously, the d.ASH server acts as a secured py-server responsible for sending control commands to the robot and for broadcasting data to any given remote systems. This section of the d.ASH SDK documentation provides details about setting up the d.ASH server. Information in this section includes compiling, and testing.


### 3.1 ^^Installing d.ASH Server Dependencies^^

To install the d.ASH server dependencies using pip, the following [desktop dependencies](/setup/desktop-dep) must be set up prior:

1. [Intel RealSense SDK 2.0](https://github.com/IntelRealSense/librealsense/releases/tag/v2.45.0)
2. [ROS Melodic on Ubuntu 18.04](/setup/desktop-dep/#12-ros-installation)
3. [FFmpeg](https://www.ffmpeg.org/download.html)

If the above dependencies have been installed, proceed by running the following command to install the rest of the python packages:
```
python3.7 configLibs.py
```
--- 
<!-- ### 3.1 ^^Import Compiled Server^^
In the file `robotHAL.py`, we need to make sure you are importing the compiled py_server C++ library:

``` python
# sys.path.append('G:/Builds/testPyServer_Build/RelWithDebInfo')
$ sys.path.append('C:/Users/kestr/Documents/Projects/Builds/dc/py_server_build/RelWithDebInfo') 
# Change this to your built path
```

Now, in `realSenseCameras.py`, we need to make sure you have also compiled the py_realsense_node C++ library:

``` python
$ sys.path.append('C:/Users/kestr/Documents/Projects/Builds/dc/py_realsense_node_build/RelWithDebInfo') # Change this to your built path
```

--- -->

<!-- ### 3.3 ^^Intel RealSense^^

[Intel RealSense](https://www.intelrealsense.com/) is an RGB camera with channels designed for depth perception capabilities. You can configure custom settings for any Intel RealSense cameras attached to the system to stream images to remote clients. You can do so by providing a config file in the same folder as where you launched d.ASH server. The config file needs to be named as [`realSenseConfig.json`](/sdk-config/realsense). 

--- -->

### 3.2 ^^Setting up Rest Configuration^^

Before you test the d.ASH server, you will need to config the rest server file, [`restConfig.json`](\sdk-config\rest-config) located in the folder `config`. 

```
dash-sdk/
└─ configs/
    └─ restConfiy.json
```

Firstly, run `runrest` to see available IP address for your rest server:
```python
runrest
```
Pick the index of the IP address you like and append it to the `activeIPIdx` variable:
```
"activeIPIdx" : 1, # where '1' is the chosen IP address indec
```
Then, you will need to set your `preferredIP` address, that is, the IP address for the computer onboard your robot. This IP address will have precedence over `activeIPIdx`. Similarly, replace the default IP address with your preferred IP address:
```
"preferredIP" : "10.8.0.5",
```
Ensure that the IP address of the onboard computer is within the same subnet by the remote client. Lastly, you will need to change the `<PATH>` of `cmdPath`. To do this, `pwd` to print your current working directory path.
```
$ pwd
C:/Users/dc/Desktop/dash_sdk/py_server
```
---

### 3.3 ^^Testing Your Server^^

To test your server, you'll firstly need to run the d.ASH server by entering the following command: 

``` python3
./robot_rest ~/.data/restConfig.json
```


``` python3
$ python3.7 ./spotServer.py robotConfig.json
```

Now that your d.ASH server is running, you will need to connect the server with the `pilot_client`. This will allow any available cameras to show up as options on your screen. To connect to the pilot client, ...

Finally, try switching to the test camera streaming and verify the test camera is streaming properly.