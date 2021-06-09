# d.ASH Autonomy Controller

As mentioned previously, the d.ASH autonomy controller is the GUI (graphical user interface) for the d.ASH SDK. It encompasses the interactive visual components for d.ASH's software and displays different elements for users to interact with to control your robot. This section of the d.ASH SDK documentation provides details about setting up the d.ASH autonomy controller, including information on ...

---
### 3.1 ^^Main Components^^

![Screenshot](img/main.png){: style="width:500px" }

1. ^^Main toolbar^^: Used to open other menus.
2. ^^Slider^^: Used to move floor grid up and down.
3. ^^Access mode^^: Used switch to mouse/keyboard mode.
      - ^^Navigation^^: The default mode uses the keys `WASD` to move camera and right click the mouse to zoom/tilt the camera. 
       - ^^Waypoint creation^^: Used for adding waypoints to routes.
4. ^^Floor grid^^

### 3.2 ^^Login^^

![Screenshot](img/login.png#center){: style="width:500px" }

Ensure login credentials match ...

### 3.3 ^^Robot Connection^^

![Screenshot](img/connect-robot.png#center){: style="width:500px" }

1.	Robots that are online and ready to be used, you can select which robot to connect to
2.	Robots that you have connected to in the client, you can select which robot to manipulate from this list
3.	Press to connect to the robot selected in the online list, the robot will then move to the connected list
4.	Press to disconnect from the robot in the connected list

Init Pose: Tells the robot where its rough initial position is, draw the arrow by: 
1.	Click init pose
2.	left clicking and dragging the mouse on the grid

![Screenshot](img/init.png#center){: style="width:500px" }

Follow: Toggle on to have the camera follow the selected dog

---

### 3.4 ^^Routes^^

![Screenshot](img/routes.png#center){: style="width:500px" }

1.	Text box to enter route name to add
2.	Click to add route of given name
3.	Click to select a route
4.	 Click to remove selected route
5.	Click to add waypoints to selected route
6.	Load/save all routes
7.	Segment number, use keypad +/- to increment/decrement segment

Robot Follow Route: Make the selected robot follow the selected route

![Screenshot](img/waypoint-1.png#center){: style="width:500px" }

-	Add waypoints by clicking on the grid, you can use WASD + Right click mouse to manipulate the view.
-	Exit waypoint mode by middle clicking the mouse

![Screenshot](img/waypoint-2.png#center){: style="width:500px" }

-	Delete waypoints by clicking the waypoint
-	Selected waypoint change to orange color
-	Press del to remove

![Screenshot](img/waypoint-3.png#center){: style="width:500px" }

-	Change elevation by moving the floor grid
-	You can move floor grid in waypoint mode by pressing ctrl+mouse scroll

![Screenshot](img/waypoint-4.png#center){: style="width:500px" }

-	You can adjust the the elevation of the waypoint by moving the grid
-	Waypoint is created when you click on grid, to create elevated waypoints, move grid up/down then click.

### 3.5 ^^Map Settings^^

![Screenshot](img/map.png#center){: style="width:500px" }

1.	Low pass, voxels below this value is visible. Voxels in maps have elevation, by lowering low pass, voxels above the low pass will be cropped

![Screenshot](img/map-2.png#center){: style="width:500px" }

Notice that the ceiling voxels have now been cropped by reducing the low pass

### 3.6 ^^Layer Visibility^^

![Screenshot](img/layer.png#center){: style="width:500px" }

Toggles visibility of various items

### 3.7 ^^Load Scans^^

![Screenshot](img/load-scan.png#center){: style="width:500px" }

Scans from dash pack can be previewed here
1.	Select your down sample size in metres, large value means lower quality, but faster loading
2.	You can pick loaded point clouds to toggle translucency

![Screenshot](img/load-scan-2.png#center){: style="width:500px" }

Translucent mode
