# Robot Configuration

This section of the d.ASH SDK documentation provides details about the configuration file for the robot `robotConfig.json`. Information in this section includes variable and definitions used to configure the [d.ASH server](../index.md#dash-server).

### 1.1 ^^Config File^^
``` json
{
    "serverAddress" : "localhost:50051",
    "robotHostname" : "192.168.80.3",
    "username" : "user5",
    "camList" : ["RealsenseCam"],
    "payloads" : [],
    "dataStateLogFolder" : "G:/Temp/logs",
    "ssl" : true,
    "fastServer" : false,
    "fastServerHostname" : "localhost:7777",
    "secureDefaultToken" : false,
    "testMode" : true,
    "withAudio" : true,
    "realSenseConfig" : {
        "test" : true,
        "testFilenames" : ["../../test_videos/nus_left.mp4", "../../test_videos/nus_center.mp4","../../test_videos/nus_right.mp4"],
        "flipOptions" : {
            "0" : [false, false],
            "1" : [true, true],
        "2" : [false, false]
        },
        "baseWidth" : 640,
        "baseHeight" : 480,
        "codec" : "video",
        "width" : 320,
        "height" : 240,
        "bitrate" : 3600000
    }
}
```
<p>&nbsp;</p>

### 1.2 ^^Definitions^^

- **`serverAddress`** : Sets address of the spotServer in `<HOSTNAME>:<PORT>` format.
- **`robotHostname`** : Sets hostname of the Spot to connect to robot's IP.
- **`username`** : Sets username to log into the Spot.
- **`camList`** : Sets a list of cameras active for the current session i.e. *RealsenseCam*.
---
- **`payloads`** : Optional payloads list.
- **`dataStateLogFolder`** : Sets folder to write out the recorded msgpack data of the robot i.e. *cameras, odom etc.*
- **`ssl`** : Enables secure SSL messaging and encryption.
---
!!! note "The following parameter should always be set to **`False`**. Use the **`<!TOKEN!>`** method in the Robot Rest Service to pass the authentication token in."

- **`secureDefaultToken`** : ???

---
- **`testMode`** : Enables the Spot server to enter into test mode.
- **`withAudio`** : Enables audio streaming playback.

---
#### 1.2.1 Intel RealSense Configuration

- **`test`**: This streams any attached hardware RealSense devices. Default is set to `false`. If you set `test` to `true`, then you can simulate camera streaming via provided custom mp4 video files specified as a list in `testFilenames`.
- **`flipOptions`**: This allows you to specific how you want to flip each camera (based on index) along the X and Y axes. The format is that of a map/table: `{ "index" : [ flipX, flipY] }`
- **`codec`**: This has jpg or video options, with jpg being regular jpeg encoding (larger size but more stable) and video using VP9 encoding. 
- **`baseWidth`**: Adjusts the processing width of the camera stream. 
- **`baseHeight`**: Adjusts the processing height of the camera stream. 
!!! note "Processed Resolution"
    The video will be actually processed at this resolution before being resized via `width` and `height`. This means you can potentially have a higher/lower resolution for the actual processed camera stream vs the returned/final size. You need this because sometimes you might want to change the actual processed resolution due to power/efficiency considerations of the RealSense devices. 
- **`width`**: Adjusts the final returned/resized width dimensions of the input camera stream
- **`height`**: Adjusts the final returned/resized height dimensions of the input camera stream
!!! note "Video Streaming"
    For video streaming, you need this to be at least a `baseWidth` of *640* and a `baseHeight` of *360* starting out. 
- **`bitrate`**:  This is the quality of the video encoding [only applies to video streaming]
!!! note "HD Streaming"
    For HD Streaming, RealSense requires a high bitrate of 3600000. This value has been tested to work well with control.
- **`odomCam`**: [**OPTIONAL**] This is a parameter that you must set if you want to use odom streaming for RealSense. If you have `odomStreamCam` setup in the main **`robotConfig.json`**, then you must also setup `odomCam` in `realSenseConfig.json`. This tells the setup to use a particular type of RealSense camera.
