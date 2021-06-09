# Setting Up d.ASH Server

As mentioned previously, the d.ASH server acts as a secured py-server responsible for sending control commands to the robot and for broadcasting data to any given remote systems. This section of the d.ASH SDK documentation provides details about setting up the d.ASH server. Information in this section includes python requirements, compiling, and testing.

### 3.1 ^^Python Requirements^^

The d.ASH SDK works with [Python 3.7](https://www.python.org/downloads/release/python-370/). To properly run the server, you will also need to install a python package installer and a python environment management system.

---

#### 3.1.1 Pip Installation
[Pip](https://pip.pypa.io/en/stable/installing/) is a package installer for Python. The d.ASH SDK and the third-party packages used by many of its programming examples use pip to install. To install pip, run the following command on Ubuntu:

``` python3
sudo apt install python3.7 python3-pip python-pip
python3.7 -m pip instal -- upgrade pip
```
It is recommended that you install an environment for Python. There are two ways to set up the Python 3.7 environment: via Conda or `apt-get`. 

---

#### 3.1.2 Conda Installation
Conda is an open source package management system and environment management system that runs on Windows, macOS and Linux. Conda quickly installs, runs and updates packages and their dependencies. First, install [Conda](https://conda.io/projects/conda/en/latest/user-guide/install/index.html#regular-installation). Then, to set up the new environment, execute the following command: 
```
$ conda create --name py37 python=3.7
```


#### 3.1.3 apt-get
If Conda is not installed, you can choose to use `apt-get` to an environment for Python. Installed in Ubuntu and any Ubuntu-based Linux distribution, `apt-get` is tool for installing, upgrading, and cleaning packages. To set up the new environment, execute the following command:
```
$ sudo apt-get install -y python3.7-dev
```
---

### 3.2 ^^Installing d.ASH Server Dependencies^^

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

### 3.3 ^^d.ASH Server Credentials^^

Now, you will need to register your robot by setting up the local credentials for the d.ASH server. To do so, you will need to by run the file:  `setServerPassNative` found in the `registration` folder of the SDK. Run the following command replacing `<username>` with your chosen username and  `<password>` with your chosen password.

```
$ ./setServerPassNative -u <username> -p <password>
```

For example, if your username is `user123` and your password is `ilovedASH`, your commands would look like this:
``` python
$ ./setServerPassNative -u user123 -p ilovedASH
```

!!! tip "Username in Robot Configuration"
    Please ensure that the username for the d.ASH server is the same as the one defined in the robot configuration file - [`robotConfig.json`](/sdk-config/robot-config). For example, you would set `"username" : "<username>"`.

--- 

### 3.4 ^^Testing Your Server^^

To test your server, you'll firstly need to run the d.ASH server by entering the following command: 
``` python3
$ python3.7 ./spotServer.py robotConfig.json
```

Now that your d.ASH server is running, you will need to connect the server with the `pilot_client`. This will allow any available cameras to show up as options on your screen. To connect to the pilot client, ...

Finally, try switching to the test camera streaming and verify the test camera is streaming properly.