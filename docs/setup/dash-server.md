# Setting Up d.ASH Server

As mentioned previously, the d.ASH server acts as a secured py-server responsible for sending control commands to the robot and for broadcasting data to any given remote systems. This section of the d.ASH SDK documentation provides details about setting up the d.ASH server. Information in this section includes python requirements, compiling, and testing.

Run https://bitbucket.org/dconstruct/dash_code/src/master/py_server/cython/configLibs.py to install d.ASH server dependencies

### 3.1 ^^Import Compiled Server^^
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

---

### 3.2 ^^Python Requirements^^

The d.ASH SDK works with [Python 3.7](https://www.python.org/downloads/release/python-370/). To properly run the server, you will also need to install the following dependencies - a python package installer and a python environment management system.

---

#### 3.2.1 Pip Installation
[Pip](https://pip.pypa.io/en/stable/installing/) is a package installer for Python. The d.ASH SDK and the third-party packages used by many of its programming examples use pip to install. 
Check if pip is installed by requesting its version:
``` python3
$ python3 -m pip --version
pip 19.2.1 from <PATH_ON_YOUR_COMPUTER>
```


If pip is not found, you’ll need to install [pip](https://pip.pypa.io/en/stable/installing/). Otherwise, install the following packages using pip:

``` python3
$ python3.7 -m pip install pillow
$ python3.7 -m pip install opencv-python
$ python3.7 -m pip install bosdyn-client bosdyn-mission bosdyn-choreography-client
$ python3.7 -m pip install keyring
$ python3.7 -m pip install secretstorage
$ python3.7 -m pip install keyrings.alt
```

It is recommended that you install an environment for Python. There are two ways to set up the Python 3.7 environment: via Conda or `apt-get`. 

---

#### 3.2.2 Conda Installation
Conda is an open source package management system and environment management system that runs on Windows, macOS and Linux. Conda quickly installs, runs and updates packages and their dependencies. First, install [Conda](https://conda.io/projects/conda/en/latest/user-guide/install/index.html#regular-installation). Then, to set up the new environment, execute the following command: 
```
$ conda create --name py37 python=3.7
```


#### 3.2.3 apt-get
If Conda is not installed, you can choose to use `apt-get` to an environment for Python. Installed in Ubuntu and any Ubuntu-based Linux distribution, `apt-get` is tool for installing, upgrading, and cleaning packages. To set up the new environment, execute the following command:
```
$ sudo apt-get install -y python3.7-dev
```
---

### 3.3 ^^Intel RealSense^^

[Intel RealSense](https://www.intelrealsense.com/) is an RGB camera with channels designed for depth perception capabilities. You can configure custom settings for any Intel RealSense cameras attached to the system to stream images to remote clients. You can do so by providing a config file in the same folder as where you launched d.ASH server. The config file needs to be named as [`realSenseConfig.json`](/sdk-config/realsense). 

---

### 3.4 ^^Testing Your Server^^

To test your server, you'll firstly need to run the d.ASH server by entering the following command: 
``` python3
$ python3.7 ./spotServer.py robotConfig.json
```

Now that your d.ASH server is running, you will need to connect the server with the `pilot_client`. This will allow any available cameras to show up as options on your screen. To connect to the pilot client, ...

Finally, try switching to the test camera streaming and verify the test camera is streaming properly.