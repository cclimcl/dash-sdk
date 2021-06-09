# Payload Registration

Before running the d.ASH SDK, please make sure your all your credentials have been set up correctly. This means using the right username and the right password. This section of the d.ASH SDK documentation provides details about setting up credentials for the d.ASH SDK. Information in this section includes the d.ASH server and the ROS driver credentials setup. Files will be found in the folder `registration` under the SDK.

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

### 2.2 ^^Robot Registration^^

To register the payload computer with d.ASH's backend system, you will need to by run the file:  `register_bot_native`. However, you will first need to configure the `registerBot.json` found in the `config` folder of the SDK. Set `<robot_name>` to any name you like, and set `<robot _username>` to your dConstruct cloud admin username. 

For example, if your robot name is `robot1` and your cloud admin user name is `user123`, your `registerBot.json` would look like this:

```
{
    RobotName: robot1,
    RobotUserName: user123
}
```

Now, run the following command to register your robot: 

```
register_bot_native -i ../config/registerBot.json
```

---

### 2.3 ^^ROS Driver Credentials^^

To set up the local credentials for the ROS driver, you will need to by run the file:  `setAutonomyCred`. Run the following command replacing `<username>` with your cloud admin username and  `<password>` with your cloud admin password. 

``` python
cd ./setAutoCred/build
./setAutonomyCred -u <username> 
```
For example, if your username is `user123`, your command would look like this:
``` python
cd ./setAutoCred/build
./setAutonomyCred -u user123 -p ilovedASH 
```
You will then be prompted to enter a <password>. This <password> will match your cloud admin password.