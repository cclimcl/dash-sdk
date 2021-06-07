# Installing Dependencies on the Desktop

While most of the d.ASH SDK build is hermetic, some system dependencies on the Desktop are required -  **Linux Ubuntu 18.04 LTS** and **ROS Melodic**. This section of the d.ASH SDK documentation provides details for both Ubuntu and ROS Melodic installations.

### 1.1 ^^Ubuntu Installation^^
Ubuntu is a complete Linux operating system, which will serve as the primary platform for [ROS](https://ubuntu.com/robotics/what-is-ros). Currently, the d.ASH SDK only supports [Linux Ubuntu 18.04 LTS](http://releases.ubuntu.com/18.04/) for development and simulation from your workstation. 

!!! info "Ubuntu Installation via Bootable USB"
    If you would like to install Ubuntu via a bootable USB, you can do so for both [Windows](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview) and [MacOS](https://ubuntu.com/tutorials/create-a-usb-stick-on-macos#1-overview).

!!! info "Ubuntu Installation via Virtual Machine"
    If you would like to install Ubuntu via a virtual machine, you can do so using [VirtualBox](https://codingwithmanny.medium.com/installing-ubuntu-18-04-on-mac-os-with-virtualbox-ac3b39678602) to kickstart your installation process.

Once Ubuntu is installed, check that your version of Ubuntu has the release code `18.04`.  Open the terminal and type the command:
``` python
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.5 LTS
Release:        18.04
Codename:       bionic
```
---

### 1.2 ^^ROS Installation^^
[ROS](https://ubuntu.com/robotics/what-is-ros) (Robot Operating System) is a open-source framework that helps researchers and developers build and reuse code between robotics applications. Currently, the d.ASH SDK only supports ROS Melodic for development and simulation from your workstation. 

Use [Ubuntu to install ROS](http://wiki.ros.org/melodic/Installation/Ubuntu) onto your computer system. Once ROS has been installed on your Linux system, check that your version of ROS is `melodic`.  Open the terminal and type the command:

``` 
$ rosversion -d
melodic
```