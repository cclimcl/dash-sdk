# Payload Registration

Before running the d.ASH SDK, please make sure your all your credentials have been set up correctly. This means using the right username and the right password. This section of the d.ASH SDK documentation provides details about setting up credentials for the d.ASH SDK. Information in this section includes the d.ASH server and the ROS driver credentials setup.

### 2.1 ^^d.ASH Server Credentials^^

To set up the local credentials for the d.ASH server, you will need to by run the file:  `setServerPassNative`. Run the following command replacing `<username>` with your chosen username and  `<password>` with your chosen password.

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

### 2.2 ^^ROS Driver Credentials^^

To set up the local credentials for the ROS driver, you will need to by run the file:  `setAutonomyCred`. Run the following command replacing `<username>` with your chosen username and  `<password>` with your chosen password. 

``` python
$ cd ./setAutoCred/build
$ ./setAutonomyCred -u <username> -p <password> 
```
For example, if your username is `user123` and your password is `ilovedASH`, your commands would look like this:
``` python
$ cd ./setAutoCred/build
$ ./setAutonomyCred -u user123 -p ilovedASH 
```