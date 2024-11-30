---
title: Sensors SetUp
parent: Guides
---

# Sensors SetUp
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

# **Camera Sensor Configuration**

To configure a **Camera** sensor in the framework, follow these steps:

### **Step 1: Detect Available Cameras**

The first step is to detect the cameras connected to your system. You can use the `get_cameras_info()` function to scan for available camera ports and retrieve details about each detected camera.

```py
def get_cameras_info(max_index=10):
    """
    Detect connected cameras and retrieve details for each, such as resolution.
    
    Args:
        max_index (int): Maximum number of camera indices to check.
    
    Returns:
        list: Details of available cameras.
    """
```
The function will check available camera indices (up to the number specified in the `max_index` parameter) and return information about the detected cameras, including their resolution.

### **Step 2: Instantiate the Camera Sensor**

Once you've detected the available cameras, select one to instantiate a `camera` sensor. Use the Camera class to configure and enable the sensor.

```py
cam1 = Camera(0, .3)  # Camera on port 0 with a sensing speed of 0.3 seconds
cam1.enable_sensor()   # Enable the camera sensor
```
* `port`: Specifies the index of the camera you want to use (e.g., 0 for the first camera).
* `sensing_speed`: The camera's sensing speed (in seconds). The default value is 0.1, but you can adjust it according to your needs.

### **Step 3: Enable the Sensor**

After instantiating the camera, you must enable it to start capturing data. This is done by calling the `enable_sensor()` method of the camera.

```py
cam1.enable_sensor()  # Enable the camera sensor
```

* This method opens the camera port and configures the necessary properties for image capturing.

### **Step 4: Start Data Streaming**

Once the sensor is enabled, you can begin streaming the captured data. This is done using the `start_data_streaming()` method.

```py
await start_sensors_streaming([cam1])  # Start streaming data from the camera
```
* `start_sensors_streaming()`: This method starts streaming data from the selected sensors. In this case, we are passing the list containing the cam1 camera.

### **Step 4: Stop Data Streaming**

When you no longer wish to stream data from the camera, you can stop the data stream using the `stop_data_streaming()` method.

```py
cam1.stop_data_streaming()  # Stop the data streaming
```
* This method stops the data streaming from the sensor.

## Complete Example

Here is a complete example of how to detect available cameras, instantiate a camera sensor, enable it, and start data streaming:

```py
async def main():
    # Detect available cameras
    available_cameras = get_cameras_info()

    if available_cameras:
        # Display information about the available cameras
        print("Available Cameras:")
        for camera in available_cameras:
            print(f"Index: {camera['index']}, Resolution: {camera['resolution']}")

        # Instantiate a selected camera, e.g., the camera on index 0
        cam1 = Camera(0, .3)  # Camera on port 0 with a sensing speed of 0.3
        cam1.enable_sensor()   # Enable the sensor

        # Start streaming data from the cameras
        await start_sensors_streaming([cam1])

    else:
        print("No cameras found.")
```
{: .note }
> By following these steps, you will be able to easily configure and use camera sensors in the framework. In the future, you will be able to integrate other sensor types, such as LIDAR or radars, using a similar approach.
