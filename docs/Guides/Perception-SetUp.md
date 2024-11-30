---
title: Perception SetUp
parent: Guides
nav_order: 3
---

# Perception SetUp
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

# **Perception Module Configuration**

The Perception module processes data from sensors to extract meaningful information about the driving environment. This guide explains how to configure perception pipelines using the **`SensorToModelPipeline`** class.

---

### **Step 1: Understand the Sensor-to-Model Pipeline**

The `SensorToModelPipeline` class acts as the core component to link sensor input with perception models. Each pipeline defines how a sensor's data is processed by the module to produce outputs for decision-making.

**Core Parameters**:
- **`input_sensor`**: The unique identifier for the sensor sending data.
- **`sensor_type`**: The type of the sensor. Supported values: `['Camera', 'Lidar', 'Custom']`.
- **`sensor_position`**: Specifies the physical position of the sensor: `['Frontal', 'Rear', 'Side', 'Custom']`.
- **`output_decision`**: The topic where the pipeline sends its outputs.
- **`perceptions` (optional)**: A list of specific perception tasks.

---

### **Step 2: Define Perception Pipelines**

Perception pipelines allow you to specify how data flows from sensors into perception models and how results are utilized. Here is an example of how to define pipelines:

```py
from module.perception import SensorToModelPipeline

pipelines = [
    SensorToModelPipeline(
        input_sensor="sensor_camera_0", 
        sensor_type="Camera",
        sensor_position="Frontal",
        output_decision="output_topic_objects1"
    ),
    SensorToModelPipeline(
        input_sensor="sensor_camera_1", 
        sensor_type="Camera",
        sensor_position="Side",
        output_decision="output_topic_objects1"
    )
]
```

* `input_sensor`: Assigns the data source. For example, sensor_camera_0 corresponds to the first configured camera.
* `sensor_type`: Specifies the type of the sensor used in the pipeline. In this case, cameras are used.
* `sensor_position`: Indicates the position of the sensor. For example, Frontal or Side.
* `output_decision`: The topic to which perception results are published.

### **Step 3: Start Perception Processing**

Once you have defined your pipelines, you can initiate the perception processing by invoking the function `control_perception_streaming` with your pipeline configuration.

```py
from module.perception import control_perception_streaming

control_perception_streaming(pipelines)
```
* This function handles streaming data through the defined pipelines, ensuring that the perception tasks are executed in real time.

### **Step 4: Customize Perception Tasks**

The Perception module supports multiple tasks, such as object detection, lane detection, and free space evaluation. By default, the system assigns these tasks based on the sensor type and position. You can customize this behavior by explicitly defining tasks in the *perceptions* parameter:

```py
custom_pipeline = SensorToModelPipeline(
    input_sensor="sensor_camera_0",
    sensor_type="Camera",
    sensor_position="Frontal",
    output_decision="output_topic_objects2",
    perceptions=["LaneDetection", "TrafficSignDetection"]
)
```
* The *perceptions* parameter allows you to specify the exact perception tasks you want to execute for the sensor. In this case, tasks include *LaneDetection* and *TrafficSignDetection*.

## Complete Example

Here is a complete example that demonstrates configuring and running perception pipelines:

```py
def main():
    # Define pipelines for the sensors
    pipelines = [
        SensorToModelPipeline(
            input_sensor="sensor_camera_0", 
            sensor_type="Camera",
            sensor_position="Frontal",
            output_decision="output_topic_objects1"
        ),
        SensorToModelPipeline(
            input_sensor="sensor_camera_1", 
            sensor_type="Camera",
            sensor_position="Side",
            output_decision="output_topic_objects1"
        )
    ]

    # Start processing data through perception pipelines
    control_perception_streaming(pipelines)
```
