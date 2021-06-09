# Rest Configuration

This section of the d.ASH SDK documentation provides details about the configuration file for the rest server - `restConfig.json`. Information in this section includes variable and definitions to configure the rest server.

### 1.1 ^^Config File^^

``` python
{
    "port" : 3000,
    "certFilename" : "./cert.pem",
    "keyFilename" : "./key.pem",
    "dhParamsFilename" : "",
    "robotRegisterNativeCert" : true,
    "activeIPIdx" : 1,
    "preferredIP" : "10.8.0.5",
    "runCmds" : {
        "py_server" : {
            "cmdStr" : "python ./spotServer.py ./configs/robotDeployConfig.json <!TOKEN!>",
            "cmdPath" : "C:/Users/kestr/Documents/Projects/dc/dash_code/py_server"
        }
    }
}
```

### 1.2 ^^Definitions^^

#### 1.2.1 Main

- **`port`**:
- **`certFilename`**:
- **`keyFilename`**:
- **`dhParamsFilename`**:
- **`robotRegisterNativeCert`**:
- **`activeIPIdx`**:
- **`preferredIP`**:

#### 1.2.2 d.ASH Server Commands

- **`cmdStr`** : 
- **`cmdPath`** : 
