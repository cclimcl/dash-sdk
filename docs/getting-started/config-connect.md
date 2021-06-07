# Configuring Sensors
## 2.1 Velodyne Driver

The [Velodyne Driver](http://wiki.ros.org/velodyne_driver) is a driver in the ROS package that provides basic device handling for Velodyne 3D LIDAR sensors.

- For more info, refer to this (insert link on how to set up)

### 2.1.1 ^^Setting Up on Sensor^^
By default, the Velodyne LIDAR sensor IP address is factory set on default value `192.168.1.201`. The d.ASH SDK will assume the default Velodyne IP address.

### 2.1.2 ^^Setting Up on Personal Computer^^
You'll need to configure a static IP address for your computer to use an address within the range `192.168.1.XXX` where `XXX` may be any integer from 2 to 254, except 201 (which is the LIDAR’s IP). For example, an appropriate static IP address for your compute could be `192.168.1.100`. 

## 2.2 Ouster Driver

### 2.2.1 ^^Setting Up on Sensor^^
By default, the Ouster LIDAR sensor IP address is factory set on your IPv6/IPv4 link-local address. The addresses lie within the block `169.254.0.0` to `169.254.255.255`. To change the static IP address for Ouster, refer to the [Ouster Documentation](https://data.ouster.io/downloads/software-user-manual/software-user-manual-v2p0.pdf). It is recommended to set up your own static IP address. 

### 2.2.2 ^^Setting Up on Personal Computer^^

You'll need to configure a static IP address for your computer to use an address within the range `192.0.2.XXX` where `XXX` may be any integer from 2 to 254. For example, an appropriate static IP address for your compute could be `192.0.2.123`. 